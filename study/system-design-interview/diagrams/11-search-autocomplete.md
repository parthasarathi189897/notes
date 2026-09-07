---
type: sysdesign-diagram
chapter: 13
system: "Search Autocomplete (Trie)"
first_drawn: ""
can_redraw: false
confidence: ""
created: 2026-05-31
tags: [study, system-design, diagram]
---

# Diagram: Search Autocomplete

> Draw this after completing [[../weeks/week-24]].

---

## What to draw

Two services:
1. **Data gathering:** query logs → aggregation → analytics DB → trie rebuild (offline)
2. **Query service:** user types → trie lookup → return top-k → cache

Show filter layer for inappropriate content.

---

## Components checklist

### Data gathering (offline)
- [ ] Query logs (raw search data)
- [ ] Log aggregation service
- [ ] Analytics DB (query frequencies)
- [ ] Trie builder (offline rebuild, e.g., weekly)
- [ ] Trie storage (distributed)

### Query service (online)
- [ ] User input → API server
- [ ] Trie lookup (prefix match)
- [ ] Top-k results (pre-computed at each node)
- [ ] Cache layer (popular prefixes)
- [ ] Filter layer (inappropriate/blocked content)
- [ ] Return suggestions to client

---

## Excalidraw drawing

> Create `11-search-autocomplete.excalidraw.md` in this folder, then it renders here automatically.

![[11-search-autocomplete.excalidraw]]

---

## Draw log

| Date | From memory? | Time | Gaps |
|------|:------------:|------|------|
| | | | |
| | | | |

---

*Back to [[../progress-tracker]] · Related: [[../weeks/week-24]]*
