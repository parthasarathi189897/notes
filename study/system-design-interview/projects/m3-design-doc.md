---
type: sysdesign-milestone
milestone: 3
chapter: 3
parent: "[[README]]"
weeks: "W4 (Sep 7-13)"
track: build
status: not-started
created: 2026-08-11
tags: [study, system-design, project, milestone]
---

# M3 — Write the Site's Own 4-Step Design Doc

> **Ch 3: Interview Framework** · Week **W4 (Sep 7-13)** · 🔨 Build (write-up)
> Apply the book's 4-step framework to a system you're actually building. Best possible
> way to internalize the framework.

---

## 🎯 What I'm shipping

A `docs/DESIGN.md` for the family site written with the book's exact 4 steps. When an
interviewer says "walk me through a system you designed," this is your answer.

---

## ✅ Acceptance criteria

- [ ] **Step 1 — Requirements:** functional (family info, contact, short links, wall) + non-functional (availability, one box, low cost)
- [ ] **Step 2 — High-level design:** the architecture diagram + main components
- [ ] **Step 3 — Deep dive:** pick 2 components (e.g. caching, rate limiting) and go deep
- [ ] **Step 4 — Wrap up:** bottlenecks, what you'd do at 1000× scale, tradeoffs
- [ ] Committed as `docs/DESIGN.md`

---

## 🧩 The 4 steps (index-card version)

```
1. Understand   — clarify scope, functional + non-functional requirements, constraints
2. High-level   — boxes and arrows, data flow, API surface
3. Deep dive    — 1-2 components in detail; tradeoffs; failure handling
4. Wrap up      — bottlenecks, scaling story, what breaks first, monitoring
```

---

## 🧠 Concept ↔ reality

You're both the interviewer and interviewee here. Writing your own system through this lens
means you'll never freeze on "where do I start" again.

---

## 📝 Post-milestone note

**Which step was hardest to write:**
**One thing I can defend in an interview:**

---

*Back to [[README]] · Prev: [[m2-estimation]] · Next: [[m4-rate-limiter]]*
