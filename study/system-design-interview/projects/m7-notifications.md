---
type: sysdesign-milestone
milestone: 7
chapter: 10
parent: "[[README]]"
weeks: "W17-18 (Dec 7-20)"
track: build
status: not-started
created: 2026-08-11
tags: [study, system-design, project, milestone]
---

# M7 — Contact Form → Email Notification

> **Ch 10: Design a Notification System** · Weeks **W17-18 (Dec 7-20)** · 🔨 Build (light)
> One channel (email), one provider — but the fan-out/queue/retry shape is real.

---

## 🎯 What I'm shipping

A contact form on the family site that, on submit, sends an email notification via a provider
(e.g. an SMTP relay or a transactional email API), with a simple queue + retry so a failed
send doesn't lose the message.

---

## ✅ Acceptance criteria

- [ ] Contact form submits → message stored → email sent to you
- [ ] Send goes through a queue (even an in-process one) rather than blocking the request
- [ ] Retry on provider failure (at least 1 retry with backoff)
- [ ] Failed sends land in a dead-letter list/log (not silently dropped)
- [ ] `docs/notifications.md`: the single-channel design + how you'd add SMS/push later

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W17 | Read Ch 10 (types, high-level). Build form → store → send. | ⬜ |
| W18 | Read Ch 10 rest (reliability, dedup, retry). Add queue + retry + DLQ. Draw diagram. | ⬜ |

---

## 🧠 Concept ↔ reality

| Book concept | In this project |
|--------------|-----------------|
| Notification service → per-channel queues | One queue, one channel (email) — note where you'd fan out |
| Third-party providers (APNs/Twilio/Mailgun) | Your email provider |
| Retry + dedup | Retry with backoff; dedup on message id |
| Analytics pipeline | Just a sent/failed log for now |

---

## 📊 Numbers

- Sends attempted / succeeded / retried / dead-lettered:
- Provider used + why:

---

## 📝 Post-milestone note

**What worked:**
**One thing I can defend in an interview:**

---

*Back to [[README]] · Prev: [[m6-short-links]] · Next: [[m8-family-wall]]*
