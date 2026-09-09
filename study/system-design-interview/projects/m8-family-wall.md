---
type: sysdesign-milestone
milestone: 8
chapter: 12
parent: "[[README]]"
weeks: "W21-22 (Mar 22 - Apr 4, 2027)"
original_target: "W21-22 (Jan 4-17, 2027)"
track: build-stretch
status: not-started
created: 2026-08-11
tags: [study, system-design, project, milestone]
---

# M8 — WebSocket "Family Wall" (Stretch)

> **Ch 12: Design a Chat System** · Weeks **W21-22 (Mar 22 - Apr 4, 2027)** · 🔨 Build (stretch)
> A real WebSocket feature. Stretch because it's the most involved build — skip to a design
> note if time is tight and you're behind.

---

## 🎯 What I'm shipping

A "family wall" / guestbook where a posted message shows up **live** for anyone with the page
open — via a WebSocket connection to the app server on the Mac mini.

---

## ✅ Acceptance criteria

- [ ] Open the wall in two browser tabs; post in one → appears in the other without refresh
- [ ] Messages persist (stored in DB, reload shows history)
- [ ] Connection handling: reconnect after drop
- [ ] Note how Cloudflare passes WebSockets through the tunnel
- [ ] `docs/family-wall.md`: connection mgmt, message flow, 1:1 vs group difference

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W21 | Read Ch 12 (WebSocket, 1:1, message flow). Basic WS echo → broadcast. | ⬜ |
| W22 | Read Ch 12 rest (group, presence, sync). Persist + reconnect. Draw diagram. | ⬜ |

---

## 🧠 Concept ↔ reality

| Book concept | In this project |
|--------------|-----------------|
| WebSocket connection mgmt | Your app server holds open connections |
| Message storage | DB table, per-message rows |
| Group fan-out | Broadcast to all connected wall viewers |
| Presence / heartbeat | Optional: show who's online (stretch-within-stretch) |

> **Tunnel note:** Cloudflare Tunnel supports WebSockets; confirm your `cloudflared`
> config and any CF proxy settings don't buffer/close the connection.

---

## 📝 Post-milestone note

**What worked (or why I deferred it):**
**One thing I can defend in an interview:**

---

*Back to [[README]] · Prev: [[m7-notifications]] · Next: [[capstone-wrap]]*
