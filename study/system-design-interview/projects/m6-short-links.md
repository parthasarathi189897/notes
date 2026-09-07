---
type: sysdesign-milestone
milestone: 6
chapter: 8
parent: "[[README]]"
weeks: "W13-14 (Nov 9-22)"
track: build
status: not-started
created: 2026-08-11
tags: [study, system-design, project, milestone]
---

# M6 — Real Short-Link Service (`go/xxx`)

> **Ch 8: Design a URL Shortener** · Weeks **W13-14 (Nov 9-22)** · 🔨 Build
> The best 1:1 match in the whole book. A URL shortener is small, read-heavy, and
> cache-friendly — you can build the *actual* system the chapter describes.

---

## 🎯 What I'm shipping

A working short-link service on your site: `yourdomain.com/s/abc123` → 301 redirect to a
long URL. base62 encoding, cache on the read path, DB for storage. This is Ch 8, for real.

---

## ✅ Acceptance criteria

- [ ] Create a short link (POST long URL → returns short code)
- [ ] Visit short link → **301** redirect to the long URL
- [ ] Short code generated via base62 (or hash + base62), collisions handled
- [ ] Read path hits cache (reuse M5 cache) before DB
- [ ] Simple analytics: click count per link
- [ ] `docs/short-links.md`: write path, read path, why 301 vs 302, cache strategy

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W13 | Read Ch 8 (API, hash, base62). Build create + redirect endpoints. | ⬜ |
| W14 | Read Ch 8 rest (collisions, cache, analytics). Add cache + click count. Draw diagram. | ⬜ |

---

## 🧱 Design (fill in as you build)

```
WRITE:  long URL → generate code (base62) → check collision → store {code→url} → return short URL
READ:   short code → cache lookup → (miss) DB lookup → 301 redirect → increment click count (async)
```

**301 vs 302:** 301 = permanent, browser caches it (fewer origin hits, but you lose per-click
analytics unless you count at the edge). 302 = temporary, every click hits you. Document your choice.

---

## 🧠 Concept ↔ reality

| Book concept | In this project |
|--------------|-----------------|
| base62 encoding | Your code generator |
| Read-heavy → cache-friendly | Reuse the M5 cache on the redirect path |
| 301 vs 302 tradeoff | A real decision with a real analytics consequence |
| Collision resolution | Handle it when two inputs hash to the same code |

---

## 📊 Numbers

- Redirect latency (cache HIT):
- Codes generated before first collision:
- Total links created:

---

## 📝 Post-milestone note

**What worked:**
**One thing I can defend in an interview:**

---

*Back to [[README]] · Prev: [[m5-cache-layer]] · Next: [[m7-notifications]]*
