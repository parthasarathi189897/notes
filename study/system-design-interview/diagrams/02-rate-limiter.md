---
type: sysdesign-diagram
chapter: 4
system: "Rate Limiter"
first_drawn: ""
can_redraw: false
confidence: ""
created: 2026-05-31
tags: [study, system-design, diagram]
---

# Diagram: Rate Limiter

> Draw this after completing [[../weeks/week-06]].

---

## What to draw

Client → API gateway (rate limiter middleware) → Redis counter → rules engine → response (429 or pass-through). Show the token bucket algorithm flow.

---

## Components checklist

- [ ] Client request
- [ ] API gateway / middleware layer
- [ ] Rate limiter logic (token bucket or sliding window)
- [ ] Redis (counter store)
- [ ] Rules engine (rate limit rules per API/user)
- [ ] Response: 429 Too Many Requests or pass-through
- [ ] Rate limit headers (X-RateLimit-Remaining, X-RateLimit-Retry-After)

---

## Excalidraw drawing

> Create `02-rate-limiter.excalidraw.md` in this folder, then it renders here automatically.

![[02-rate-limiter.excalidraw]]

---

## Draw log

| Date | From memory? | Time | Gaps |
|------|:------------:|------|------|
| | | | |
| | | | |

---

*Back to [[../progress-tracker]] · Related: [[../weeks/week-06]]*
