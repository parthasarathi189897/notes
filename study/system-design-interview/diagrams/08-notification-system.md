---
type: sysdesign-diagram
chapter: 10
system: "Notification System"
first_drawn: ""
can_redraw: false
confidence: ""
created: 2026-05-31
tags: [study, system-design, diagram]
---

# Diagram: Notification System

> Draw this after completing [[../weeks/week-18]].

---

## What to draw

Service → notification service → message queues (one per channel: push/SMS/email) → workers → third-party providers (APNs, Twilio, Mailgun) → device/user. Show retry queue and analytics pipeline.

---

## Components checklist

- [ ] Triggering service (or API)
- [ ] Notification service (validation, rate limiting)
- [ ] Message queues (separate per channel: push, SMS, email)
- [ ] Workers (consume from queues)
- [ ] Third-party providers (APNs, FCM, Twilio, Mailgun)
- [ ] Retry queue (failed deliveries)
- [ ] Analytics pipeline (delivery tracking)
- [ ] User preference store (opt-in/out)

---

## Excalidraw drawing

> Create `08-notification-system.excalidraw.md` in this folder, then it renders here automatically.

![[08-notification-system.excalidraw]]

---

## Draw log

| Date | From memory? | Time | Gaps |
|------|:------------:|------|------|
| | | | |
| | | | |

---

*Back to [[../progress-tracker]] · Related: [[../weeks/week-18]]*
