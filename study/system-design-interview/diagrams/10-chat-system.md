---
type: sysdesign-diagram
chapter: 12
system: "Chat System (WebSocket)"
first_drawn: ""
can_redraw: false
confidence: ""
created: 2026-05-31
tags: [study, system-design, diagram]
---

# Diagram: Chat System

> Draw this after completing [[../weeks/week-22]].

---

## What to draw

Client ↔ WebSocket ↔ chat service → message queue → message DB (key-value, per-user). Separate: presence service (heartbeat). Show 1:1 vs group message fan-out difference.

---

## Components checklist

- [ ] Client ↔ WebSocket connection
- [ ] Chat service (connection management)
- [ ] Message queue (between chat servers)
- [ ] Message storage (key-value DB, partitioned by user/channel)
- [ ] Presence service (online/offline via heartbeat)
- [ ] 1:1 flow: sender → chat service → recipient's chat server → push
- [ ] Group flow: sender → fan-out to all group members
- [ ] Message sync (sequence IDs for offline delivery)

---

## Excalidraw drawing

> Create `10-chat-system.excalidraw.md` in this folder, then it renders here automatically.

![[10-chat-system.excalidraw]]

---

## Draw log

| Date | From memory? | Time | Gaps |
|------|:------------:|------|------|
| | | | |
| | | | |

---

*Back to [[../progress-tracker]] · Related: [[../weeks/week-22]]*
