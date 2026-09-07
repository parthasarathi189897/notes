---
type: sysdesign-diagram
chapter: 1
system: "Scale From Zero To Millions"
first_drawn: ""
can_redraw: false
confidence: ""
created: 2026-05-31
tags: [study, system-design, diagram]
---

# Diagram: Scale From Zero To Millions

> Draw this after completing [[../weeks/week-02]].

---

## What to draw

Single user → web tier + data tier → load balancer → DB replication → cache layer → CDN → message queue → sharding.

**Label each component and explain *why* it's added.**
- vertical scaling vs horizontal scaling:

### Vertical vs Horizontal Scaling (draw.io)

> Click to open in draw.io editor. After first save in the editor, this will render inline.

![[vertical-horizontal-scaling.drawio]]

[[vertical-horizontal-scaling.drawio|Open in draw.io editor →]]

---

## Components checklist

- [ ] Single server (web + DB on one machine)
- [ ] Separate web tier and data tier
- [ ] Load balancer (distribute traffic)
- [ ] Database replication (master → read replicas)
- [ ] Cache layer (Redis/Memcached between app and DB)
- [ ] CDN (static assets closer to users)
- [ ] Message queue (async processing)
- [ ] Database sharding (horizontal partitioning)

---

## Excalidraw drawing

> Open the Excalidraw file to draw, then it embeds here. Click the image to edit.

![[01-scale-zero-to-millions.excalidraw.md]]

---

## Draw log

| Date | From memory? | Time | Gaps |
|------|:------------:|------|------|
| | | | |
| | | | |
| | | | |

---

*Back to [[../progress-tracker]] · Related: [[../weeks/week-02]]*
