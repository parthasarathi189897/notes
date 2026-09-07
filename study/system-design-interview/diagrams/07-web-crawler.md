---
type: sysdesign-diagram
chapter: 9
system: "Web Crawler"
first_drawn: ""
can_redraw: false
confidence: ""
created: 2026-05-31
tags: [study, system-design, diagram]
---

# Diagram: Web Crawler

> Draw this after completing [[../weeks/week-16]].

---

## What to draw

Seed URLs → URL frontier (priority queue) → HTML downloader (DNS resolver → fetch) → content parser → dedup (content hash) → URL extractor → URL filter → back to frontier. Show the loop.

---

## Components checklist

- [ ] Seed URLs (starting point)
- [ ] URL frontier (priority queue with politeness)
- [ ] DNS resolver
- [ ] HTML downloader (fetcher)
- [ ] Content parser
- [ ] Content dedup (hash comparison)
- [ ] URL extractor (find links in page)
- [ ] URL filter (already seen? robots.txt?)
- [ ] Loop back to frontier
- [ ] Content storage

---

## Excalidraw drawing

> Create `07-web-crawler.excalidraw.md` in this folder, then it renders here automatically.

![[07-web-crawler.excalidraw]]

---

## Draw log

| Date | From memory? | Time | Gaps |
|------|:------------:|------|------|
| | | | |
| | | | |

---

*Back to [[../progress-tracker]] · Related: [[../weeks/week-16]]*
