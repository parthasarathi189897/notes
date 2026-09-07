---
type: sysdesign-diagram
chapter: 8
system: "URL Shortener"
first_drawn: ""
can_redraw: false
confidence: ""
created: 2026-05-31
tags: [study, system-design, diagram]
---

# Diagram: URL Shortener

> Draw this after completing [[../weeks/week-14]].

---

## What to draw

**Write path:** long URL → hash → check collision → store in DB → return short URL.
**Read path:** short URL → cache lookup → DB fallback → 301 redirect.
Show the cache layer (read-heavy = cache-friendly).

---

## Components checklist

- [ ] Write flow: client → API → hash function (base62) → collision check → DB write → return short URL
- [ ] Read flow: client → short URL → cache (Redis) → DB fallback → 301/302 redirect
- [ ] Cache layer between app and DB
- [ ] Database (URL mapping table)
- [ ] 301 (permanent) vs 302 (temporary) redirect decision

---

## Excalidraw drawing

> Create `06-url-shortener.excalidraw.md` in this folder, then it renders here automatically.

![[06-url-shortener.excalidraw]]

---

## Draw log

| Date | From memory? | Time | Gaps |
|------|:------------:|------|------|
| | | | |
| | | | |

---

*Back to [[../progress-tracker]] · Related: [[../weeks/week-14]]*
