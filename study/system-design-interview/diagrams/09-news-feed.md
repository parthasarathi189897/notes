---
type: sysdesign-diagram
chapter: 11
system: "News Feed (Fan-out)"
first_drawn: ""
can_redraw: false
confidence: ""
created: 2026-05-31
tags: [study, system-design, diagram]
---

# Diagram: News Feed System

> Draw this after completing [[../weeks/week-20]].

---

## What to draw

Two flows:
1. **Publish:** user posts → web server → fan-out service → write to friends' feed caches
2. **Retrieve:** user opens feed → feed service → cache → merge + rank → return

Show hybrid: fan-out-on-write for normal users, fan-out-on-read for celebrities.

---

## Components checklist

### Publish flow
- [ ] User creates post → web server
- [ ] Fan-out service
- [ ] Fan-out-on-write: push to all friends' feed caches
- [ ] Celebrity exception: fan-out-on-read (pull model)
- [ ] Post storage (DB)
- [ ] Media storage (CDN/blob)

### Retrieve flow
- [ ] User opens feed → feed service
- [ ] Feed cache lookup
- [ ] Merge + rank (chronological + relevance)
- [ ] Return to client

---

## Excalidraw drawing

> Create `09-news-feed.excalidraw.md` in this folder, then it renders here automatically.

![[09-news-feed.excalidraw]]

---

## Draw log

| Date | From memory? | Time | Gaps |
|------|:------------:|------|------|
| | | | |
| | | | |

---

*Back to [[../progress-tracker]] · Related: [[../weeks/week-20]]*
