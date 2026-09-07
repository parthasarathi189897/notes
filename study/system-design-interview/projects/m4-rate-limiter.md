---
type: sysdesign-milestone
milestone: 4
chapter: 4
parent: "[[README]]"
weeks: "W5-6 (Sep 14-27)"
track: build
status: not-started
created: 2026-08-11
tags: [study, system-design, project, milestone]
---

# M4 — Edge Rate Limiting (Cloudflare WAF)

> **Ch 4: Design a Rate Limiter** · Weeks **W5-6 (Sep 14-27)** · 🔨 Build
> One of the three strongest hands-on wins. You'll configure a real rate limit at the edge
> and watch it return 429s.

---

## 🎯 What I'm shipping

A Cloudflare rate-limiting rule protecting your site (e.g. the contact form or the whole
origin), plus a small load test that trips it so you *see* the 429s and the algorithm behavior.

---

## ✅ Acceptance criteria

- [ ] A Cloudflare rate-limit rule active on a path (e.g. `/contact` or `/*`)
- [ ] Deliberately exceed the limit → observe HTTP **429** responses
- [ ] Note which algorithm Cloudflare uses (sliding window) vs the book's 5 algorithms
- [ ] Screenshot the 429 + the rule config
- [ ] `docs/rate-limiting.md`: which algorithm, where the limiter sits, tradeoffs

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W5 | Read Ch 4 (token bucket, sliding window). Add a CF rate-limit rule. | ⬜ |
| W6 | Read Ch 4 rest (distributed, race conditions). Load-test to trip 429s. Draw diagram. | ⬜ |

---

## 🔬 Trip the limit

```bash
# fire N requests quickly and count status codes
for i in $(seq 1 100); do
  curl -s -o /dev/null -w "%{http_code}\n" https://YOUR-DOMAIN/contact
done | sort | uniq -c
# expect a burst of 200s then 429s once the limit trips
```

---

## 🧠 Concept ↔ reality

| Book concept | In this project |
|--------------|-----------------|
| Where to put the limiter (client/server/middleware) | At the edge (Cloudflare), before origin |
| Sliding window counter | What Cloudflare uses under the hood |
| 429 + Retry-After | The actual response you'll observe |
| Distributed rate limiting | Cloudflare does this across its edge for you — note *why* it's hard |

---

## 📊 Numbers

- Limit set (req / window):
- Requests before first 429:
- Response headers on a 429 (Retry-After?):

---

## 📝 Post-milestone note

**What worked:**
**One thing I can defend in an interview:**

---

*Back to [[README]] · Prev: [[m3-design-doc]] · Next: [[m5-cache-layer]]*
