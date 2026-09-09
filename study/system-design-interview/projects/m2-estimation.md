---
type: sysdesign-milestone
milestone: 2
chapter: 2
parent: "[[README]]"
weeks: "W3 (Oct 5-11, 2026)"
original_target: "W3 (Aug 31 - Sep 6)"
track: build
status: not-started
created: 2026-08-11
tags: [study, system-design, project, milestone]
---

# M2 — Estimate Your Real Family Traffic

> **Ch 2: Back-of-Envelope Estimation** · Week **W3 (Oct 5-11, 2026)** · 🔨 Build (write-up)
> Tiny numbers, real method. You'll do the exact estimation drill from the book, but on
> traffic you actually control.

---

## 🎯 What I'm shipping

A one-page estimation of your family site's load — using the book's QPS/storage/bandwidth
method — plus the "what changes at 1000×" version so you practice scaling the numbers.

---

## ✅ Acceptance criteria

- [ ] QPS estimate for the family site (peak + average) with assumptions written down
- [ ] Storage estimate (pages, images, DB rows) for 1 year
- [ ] Bandwidth estimate (with vs without Cloudflare cache — show the cache savings)
- [ ] A "×1000 users" column showing which number breaks first
- [ ] Added to `docs/estimation.md` in the repo

---

## 📐 The drill (fill in)

```
Users:            ~5 family + occasional visitors
Requests/user/day:
Peak QPS:         (daily requests × peak factor) / 86400
Avg object size:
Bandwidth/day:    QPS × avg size
Cache offload:    % served by Cloudflare edge → origin bandwidth saved
Storage/year:     pages + images + DB growth
```

**Key book numbers to reuse:** 1M req/day ≈ 12 QPS · 1M users × 1KB = 1GB · cache the hot 20%.

---

## 🧠 Concept ↔ reality

Your real QPS is ~0. The *point* is the method: when someone asks "design Twitter", you'll
estimate from first principles instead of guessing. Practicing on your own tiny site makes
the technique muscle memory.

---

## 📝 Post-milestone note

**Which number would break first at scale:**
**One thing I can defend in an interview:**

---

*Back to [[README]] · Prev: [[m1-origin-and-cdn]] · Next: [[m3-design-doc]]*
