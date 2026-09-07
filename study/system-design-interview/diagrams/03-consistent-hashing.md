---
type: sysdesign-diagram
chapter: 5
system: "Consistent Hashing (Hash Ring)"
first_drawn: ""
can_redraw: false
confidence: ""
created: 2026-05-31
tags: [study, system-design, diagram]
---

# Diagram: Consistent Hashing

> Draw this after completing [[../weeks/week-08]].

---

## What to draw

Hash ring with servers + virtual nodes. Show what happens when a server is added/removed. Show key-to-server mapping.

---

## Components checklist

- [ ] Hash ring (circular space, e.g., 0 to 2^32)
- [ ] Server nodes placed on the ring
- [ ] Virtual nodes (multiple positions per physical server)
- [ ] Keys mapped clockwise to nearest server
- [ ] Server addition: show which keys move
- [ ] Server removal: show which keys remap

---

## Excalidraw drawing

> Create `03-consistent-hashing.excalidraw.md` in this folder, then it renders here automatically.

![[03-consistent-hashing.excalidraw]]

---

## Draw log

| Date | From memory? | Time | Gaps |
|------|:------------:|------|------|
| | | | |
| | | | |

---

*Back to [[../progress-tracker]] · Related: [[../weeks/week-08]]*
