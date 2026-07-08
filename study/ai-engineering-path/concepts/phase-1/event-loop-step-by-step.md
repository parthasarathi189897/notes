---
type: concept
domain: python-async
difficulty: intermediate
confidence: low
revisit_date: 2026-07-11
created: 2026-07-04
updated: 2026-07-04
tags:
  - concept
  - python
  - async
  - event-loop
aliases: [event loop trace, asyncio step by step, how the event loop runs]
phase: 0
related_courses:
  - "Python async fundamentals"
---

# Event loop, step by step (E2E trace)

> Deep dive companion to [[async + httpx in python]]. One example, traced tick by tick, to see **exactly** how the loop runs, suspends, idles, and resumes.

## First, clear up "the main thread"
> There is **only one thread**. The event loop *is* running on your main thread. So "handing control back" does **not** mean switching to another thread — it means the coroutine's `await` returns control to the **loop's driver code** (which is on the same thread). The loop then decides what to run next. No parallelism, no second thread — just one thread that refuses to sit idle.

---

## The example

One synchronous entry point that launches **three** async events with different durations. The timestamps in the output are the proof of what the loop did.

```python
import asyncio
import time

start = time.perf_counter()
def ts() -> str:                     # seconds since program start
    return f"{time.perf_counter() - start:4.1f}s"

async def worker(name: str, delay: int) -> str:
    print(f"[{ts()}] {name}: START")
    await asyncio.sleep(delay)       # suspend: register a timer, yield to loop
    print(f"[{ts()}] {name}: RESUMED (waited {delay}s)")
    return f"{name}-result"

async def main() -> None:
    print(f"[{ts()}] main: START")
    results = await asyncio.gather(  # schedule A, B, C; wait for all
        worker("A", 3),
        worker("B", 1),
        worker("C", 2),
    )
    print(f"[{ts()}] main: DONE -> {results}")

print(f"[{ts()}] sync: before asyncio.run()")
asyncio.run(main())                  # build loop, run main() to completion, close loop
print(f"[{ts()}] sync: after asyncio.run()")
```

### What it prints

```
[ 0.0s] sync: before asyncio.run()
[ 0.0s] main: START
[ 0.0s] A: START
[ 0.0s] B: START
[ 0.0s] C: START
[ 1.0s] B: RESUMED (waited 1s)
[ 2.0s] C: RESUMED (waited 2s)
[ 3.0s] A: RESUMED (waited 3s)
[ 3.0s] main: DONE -> ['A-result', 'B-result', 'C-result']
[ 3.0s] sync: after asyncio.run()
```

Two things to notice immediately:
1. All three `START`s happen at `0.0s` — they were launched back-to-back before any of them blocked.
2. They **resume in finish order** (B, C, A = 1s, 2s, 3s), but `gather` returns results in **call order** (A, B, C). Total time ≈ 3s (the longest), not 6s (the sum).

---

## The tick-by-tick trace

This is the whole point — what the loop is doing at each moment. "Ready queue" = things to run *now*; "Timers" = wake-ups scheduled for later.

| # | Clock | What happens | Ready queue → | Pending timers |
|---|-------|--------------|---------------|----------------|
| 1 | 0.0 | sync prints "before"; `asyncio.run` creates the loop + a Task for `main` | `[main]` | — |
| 2 | 0.0 | Loop runs **main**: prints "main START"; `gather` wraps A, B, C as Tasks and queues them; `main` awaits the gather-future → **main suspends** | `[A, B, C]` | — |
| 3 | 0.0 | Loop runs **A**: prints "A START"; `await sleep(3)` registers a timer at t=3 → **A suspends** | `[B, C]` | `A@3` |
| 4 | 0.0 | Loop runs **B**: prints "B START"; `await sleep(1)` → timer at t=1 → **B suspends** | `[C]` | `A@3, B@1` |
| 5 | 0.0 | Loop runs **C**: prints "C START"; `await sleep(2)` → timer at t=2 → **C suspends** | `[]` | `A@3, B@1, C@2` |
| 6 | 0.0 | Ready queue empty. Nearest timer is B@1. Loop calls `selector.select(timeout=1)` → **the thread idles at the OS level** (not spinning) | `[]` | `A@3, B@1, C@2` |
| 7 | 1.0 | B's timer is due → loop pushes B's resume callback | `[B]` | `A@3, C@2` |
| 8 | 1.0 | Loop **resumes B** right after its `await`: prints "B RESUMED"; `return "B-result"` → B's Task result is **set** → gather notes 1 of 3 done | `[]` | `A@3, C@2` |
| 9 | 1.0 | Ready empty again → idle until next timer C@2 | `[]` | `A@3, C@2` |
| 10 | 2.0 | C's timer due → push C | `[C]` | `A@3` |
| 11 | 2.0 | Loop **resumes C**: prints "C RESUMED"; returns → result set → 2 of 3 done | `[]` | `A@3` |
| 12 | 2.0 | Idle until A@3 | `[]` | `A@3` |
| 13 | 3.0 | A's timer due → push A | `[A]` | — |
| 14 | 3.0 | Loop **resumes A**: prints "A RESUMED"; returns → 3 of 3 → **gather-future's result is set** → the thing `main` was awaiting is ready → **main is re-scheduled** | `[main]` | — |
| 15 | 3.0 | Loop **resumes main**: prints "main DONE [...]"; `main` returns → its Task is done → `run_until_complete` stops the loop | `[]` | — |
| 16 | 3.0 | `asyncio.run` closes the loop; control returns to sync code → prints "after" | — | — |

![[async-loop-iteration]]

---

## Answering the exact questions

**"How does it hand control back?"**
> Steps 3–5 and 8/11/14: a coroutine calls `await` on something not-yet-done. Under the hood that `await` **returns out of the coroutine** back into the loop's driver. The coroutine is frozen exactly where it stopped (Python keeps its local state alive), with a callback registered to resume it later. The loop then picks the next ready item. Same thread throughout.

**"What happens when the async event has a result?"**
> Steps 8, 11, 14: when the awaited thing completes (a timer fires, a socket has data), the loop **sets the result on that future**. Setting a result triggers the future's done-callbacks, which **schedule the suspended coroutine's continuation onto the ready queue**. On a later tick the loop pops it and the coroutine resumes on the line right after its `await`, with the value available.

**"Where does the sync/idle time go?"**
> Steps 6, 9, 12: when nothing is ready to run, the loop doesn't busy-wait. It calls `selector.select(timeout=<next timer>)`, which puts the single thread to sleep at the OS level until either an I/O source is ready or the timer is due. This is *why* async is efficient — the idle waiting costs no CPU.

---

## The three things to internalize
> 1. **One thread.** `await` yields to the loop, never to another thread. Concurrency ≠ parallelism.
> 2. **A coroutine runs only up to its next `await`,** then suspends. The loop interleaves many coroutines by running each in these short bursts.
> 3. **A result is delivered by re-queuing the coroutine.** "Getting a result" = future result set → continuation scheduled → resumed next tick.

⚠️ Corollary: a *synchronous* blocking call (`time.sleep`, `requests.get`) inside a coroutine never yields — so the loop is frozen and **all** other coroutines stall. Always use the async version (`asyncio.sleep`, `httpx.AsyncClient`).

---

## Related Concepts
- [[async + httpx in python]]

## Sources
> Python `asyncio` docs (Event Loop, Tasks and Coroutines); CPython `selectors` module

---
%%Confidence guide: low = just learned, revisit in 7 days. medium = understand it, revisit in 30 days. high = could teach it.%%
