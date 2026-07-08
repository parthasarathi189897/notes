---
type: concept
domain: python-async
difficulty: beginner
confidence: low
revisit_date: 2026-07-11
created: 2026-07-04
updated: 2026-07-04
tags:
  - concept
  - python
  - async
aliases: [asyncio, async await python, event loop, httpx async]
phase: 0
related_courses:
  - "Python async fundamentals"
---

# Async / await & httpx in Python

## In One Sentence
> `async`/`await` let a **single thread** stay busy by switching to other work whenever it hits a slow I/O wait (like a network call), and the **event loop** is the scheduler that orchestrates that switching.

## Why Does It Matter?
> LLM and RAG work is full of I/O waits — API calls to models, vector DBs, and web pages. Async lets you fire many of those at once on one thread, turning "3 requests × 2s = 6s" into "≈2s". `httpx.AsyncClient` is the standard way to do this for HTTP.

---

## 1. The core idea — blocking vs. concurrent

The problem async solves: most of the time in an API call is spent **waiting** on the network, not computing. Synchronous code sits idle during that wait. Async code uses it.

![[async-sync-vs-async]]

Key point: this is **concurrency, not parallelism**. It's still one thread — there's no extra CPU doing work. It just refuses to sit idle.

---

## 2. Vocabulary (get these straight first)

| Term | What it is |
|------|-----------|
| **coroutine function** | a function defined with `async def` |
| **coroutine object** | what you get when you *call* it — it doesn't run yet, it's a "paused plan" |
| **`await`** | pause here, hand control back to the loop, resume when the awaited thing is ready |
| **Task** | a coroutine scheduled onto the loop to run (`create_task`, `gather`) |
| **event loop** | the single-threaded scheduler that runs tasks up to their next `await` |
| **`asyncio.run()`** | creates the loop, runs your top coroutine until done, closes the loop |

---

## 3. How `await` and the event loop actually work

When a coroutine hits `await` on something slow, it **suspends** and returns control to the loop. The loop starts (or resumes) other work. When the OS signals that the I/O is done, the loop wakes the original coroutine back up.

![[async-eventloop-sequence]]

This is why **one slow blocking call poisons everything**: if you call a *synchronous* blocking function (e.g. `time.sleep()` or `requests.get()`) inside a coroutine, it never yields, so the loop is frozen and nothing else runs. Use the async equivalents (`asyncio.sleep()`, `httpx.AsyncClient`).

---

## 4. Mental model — how the pieces connect

![[async-mental-model]]

You author coroutines; `asyncio` schedules them as tasks; the loop juggles them. You rarely touch the loop directly — `asyncio.run()` and `gather()` cover most needs.

---

## 5. Concrete example — concurrent HTTP with httpx

```python
import asyncio
import httpx

async def fetch(client: httpx.AsyncClient, url: str) -> int:
    resp = await client.get(url)      # suspends here; loop runs other fetches
    return resp.status_code

async def main() -> None:
    async with httpx.AsyncClient(timeout=10) as client:   # reuse one client
        urls = ["https://example.com"] * 5
        tasks = [fetch(client, u) for u in urls]           # coroutine objects
        results = await asyncio.gather(*tasks)             # run all concurrently
        print(results)

asyncio.run(main())   # entry point: builds the loop, runs main() to completion
```

What each layer does:
- `async with httpx.AsyncClient()` — one client, pooled connections, reused across requests.
- `[fetch(client, u) for u in urls]` — builds coroutine objects; **nothing runs yet**.
- `asyncio.gather(*tasks)` — schedules them all and awaits all results; this is where concurrency happens.
- `asyncio.run(main())` — the only synchronous call; everything async lives under it.

---

## 6. Common gotchas

| Gotcha | Fix |
|--------|-----|
| Calling a coroutine without `await` | You get a coroutine object, not a result — always `await` it (or schedule it). |
| Using `requests` / `time.sleep()` inside async | Blocks the whole loop. Use `httpx` / `asyncio.sleep()`. |
| Creating a new `AsyncClient` per request | Kills connection reuse. Create one, share it. |
| Awaiting in a plain loop instead of `gather` | `for u in urls: await fetch(...)` runs them **sequentially** — no speedup. Use `gather`. |
| Forgetting `asyncio.run` | Coroutines never execute without a loop driving them. |

---

## Related Concepts
- [[event-loop-step-by-step]] — E2E tick-by-tick trace of the loop
- [[LLM Application]]
- [[pydantic]]

## Sources
> Python `asyncio` docs + `httpx` async guide (python-httpx.org)

---
%%Confidence guide: low = just learned, revisit in 7 days. medium = understand it, revisit in 30 days. high = could teach it.%%
