---
type: sysdesign-milestone
milestone: capstone
parent: "[[README]]"
weeks: "W25-26 (Apr 19 - May 2, 2027)"
original_target: "W25-26 (Jan 18-31, 2027)"
track: ship
status: not-started
created: 2026-08-11
tags: [study, system-design, project, milestone]
---

# Capstone Wrap — Whole-Site Architecture + Walkthrough

> **Review & Mock weeks** · Weeks **W25-26 (Apr 19 - May 2, 2027)** · 🔨 Ship
> Tie every milestone together. This is the artifact you show and the story you tell.

---

## 🎯 What I'm shipping

A finished `ARCHITECTURE.md` for the whole family site + a recorded 15-min walkthrough where
you explain the design as if in an interview. This is your Vol-1 capstone.

---

## ✅ Acceptance criteria

- [ ] `ARCHITECTURE.md` shows the full end-state diagram with every milestone's box
- [ ] Each component has a 1-2 sentence "why it's here + tradeoff" note
- [ ] A "how I'd scale this to 1000× / 1M users" section pulling in the design notes (Ch 5, 7, 9, 11, 13)
- [ ] Record yourself explaining the whole design in ~15 min (voice memo or screen record)
- [ ] Listen back → note the 2 weakest spots → re-read those chapters
- [ ] Repo `family-site` public, README tells the story: problem → architecture → tradeoffs → numbers

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W25 | Consolidate all `docs/*.md` into `ARCHITECTURE.md`. Re-draw 3 weakest diagrams. | ⬜ |
| W26 | Record the 15-min walkthrough. Review. Note gaps. Polish repo README. | ⬜ |

---

## 🎤 The walkthrough script (outline)

```
1. Problem + requirements (family site, one box, low cost, secure exposure)
2. High-level architecture (Cloudflare → tunnel → Caddy → app → cache → DB)
3. Deep dive: CDN caching (Ch1) + edge rate limiting (Ch4) + short links (Ch8)
4. Scaling story: what breaks first, and the design notes for sharding/IDs/feed/etc.
5. What I'd do differently
```

---

## 📝 Final post-mortem

**What I actually built vs planned:**
**Best interview story from this project:**
**What I'd build next (Vol 2 territory):**

---

*Back to [[README]] · Prev: [[m8-family-wall]]*
