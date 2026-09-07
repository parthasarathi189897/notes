---
type: sysdesign-week
week: 5
chapter: 4
dates: "Sep 14-20, 2026"
book_section: "Ch 4: rate limiter algorithms"
video: "https://www.youtube.com/watch?v=YXkOdWBwqaA"
status: completed
created: 2026-05-31
tags: [study, system-design, weekly]
---

# Week 5 — Ch 4: Rate Limiter (Part 1)

> Dates: **Sep 14-20, 2026**
> Read: Ch 4 first half — token bucket, leaking bucket, sliding window
> Watch: [Rate Limiting — System Design](https://www.youtube.com/watch?v=YXkOdWBwqaA) — ByteByteGo

---

## 🎯 This week's focus

- [x] Watch rate limiting video during commute/walk
- [x] Read Ch 4 first half: algorithms — token bucket, leaking bucket, fixed window, sliding window

---

## 📝 Reading notes

### Token bucket
- Each user/IP gets a "bucket" that holds up to **b** tokens
- Tokens refill at a fixed rate **r** tokens/sec
- Each request costs 1 token; if bucket empty → reject (HTTP 429)
- Two params to tune: **bucket size** (burst capacity) and **refill rate** (sustained throughput)
- Example: bucket=10, refill=2/sec → allows burst of 10 then sustains 2 req/s
- Used by **Amazon** and **Stripe** — simple, memory efficient, allows bursts
- Tradeoff: tuning b and r correctly is challenging in practice

### Leaking bucket
- Requests enter a **FIFO queue** of fixed size
- Queue processes at a constant rate (like water leaking from a bucket)
- If queue full → new requests dropped
- Guarantees a **smooth, constant output rate** — good for APIs needing stable throughput
- Downside: a burst of traffic fills the queue with old requests; newer requests get dropped even if they're higher priority
- Used by **Shopify** — shapes traffic into uniform rate

### Fixed window counter
- Time divided into fixed windows (e.g., every minute: 0:00-0:59, 1:00-1:59)
- Counter increments per request; resets at window boundary
- Simple to implement: one counter + one timestamp per user
- **Critical flaw**: boundary burst — if limit is 5/min, a user can send 5 at 0:59 and 5 at 1:00 = 10 requests in 2 seconds
- Memory efficient but imprecise at window edges

### Sliding window log
- Stores **timestamp of every request** in a sorted set (e.g., Redis ZSET)
- On new request: remove all timestamps older than `now - window_size`, count remaining
- No boundary burst problem — perfectly accurate
- **Downside: memory expensive** — stores every timestamp, even for rejected requests
- O(n) cleanup on each request; not great for high-traffic APIs

### Sliding window counter
- **Hybrid** of fixed window + sliding window log
- Formula: `count = prev_window_count * overlap_% + current_window_count`
- Example: window=1min, we're 30s into current minute → `prev * 0.5 + current`
- Only stores 2 counters (prev + current) — very memory efficient
- Not 100% accurate but CloudFlare measured only 0.003% error rate in practice
- **Best balance** of accuracy vs. memory for most use cases

---

## 🧠 Algorithm comparison

| Algorithm | Pros | Cons | Use when |
|-----------|------|------|----------|
| Token bucket | Memory efficient, allows bursts | Hard to tune 2 params | Need burst tolerance (API gateways) |
| Leaking bucket | Smooth constant output rate | Burst fills queue, starves new requests | Need stable processing rate (payment APIs) |
| Fixed window | Simplest, minimal memory | Boundary burst problem (2x spike) | Low-stakes limiting, prototyping |
| Sliding window log | Perfectly accurate | High memory (stores all timestamps) | Strict accuracy required, low volume |
| Sliding window counter | Low memory, nearly accurate | ~0.003% edge-case error | Production APIs (best overall tradeoff) |

---

## 💡 Key takeaways / things I want to remember

- "Where do you put the rate limiter?" → Usually in an **API gateway** (middleware), not in each service
- Rate limiting headers: `X-Ratelimit-Remaining`, `X-Ratelimit-Limit`, `X-Ratelimit-Retry-After`
- In a distributed system, the counter lives in **Redis** (fast, atomic INCR, shared across instances)
- Two big distributed problems: **race conditions** (solved with Lua script or Redis sorted sets) and **synchronization** (solved with centralized Redis vs. sticky sessions)
- Interview tip: always clarify — rate limit by user ID? IP? API key? Different rules per endpoint?

---

## 📓 Session log

### Session 1 — Jun 29
- **Duration:** 35 min
- **Did:** Read Ch 4 up through sliding window counter. Took notes on all 5 algorithms.
- **Learned:** Sliding window counter is the sweet spot — I'd been overthinking the tradeoff between log and fixed window. The weighted average formula is elegant.

### Session 2 — Jul 1 (commute)
- **Duration:** 18 min
- **Did:** Watched ByteByteGo rate limiting video
- **Learned:** The video emphasized the API gateway placement more than the book. Good mental model: rate limiter = bouncer at the door, not inside the club.

### Session 3 — Jul 3
- **Duration:** 15 min
- **Did:** Re-read algorithm comparison, filled in the table from memory, then checked
- **Learned:** I kept mixing up leaking bucket vs token bucket direction. Mnemonic: **Token** = you spend tokens (allowance), **Leaking** = requests drip out (queue drains).

---

*Prev: [[week-04]] · Back to [[../progress-tracker]] · Next: [[week-06]]*
