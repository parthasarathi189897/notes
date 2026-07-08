---
type: ai-eng-week
week: 1
phase: 0
dates: "Jun 1-7, 2026"
course: "C1 GenAI w/ LLMs (1/4)"
project: "—"
hours_target: 3.5
hours_logged: 1.0
status: partial
streak_before: 0
created: 2026-05-29
updated: 2026-06-15
tags:
  - study
  - ai-engineering
  - weekly
  - phase-0
---

# Week 1 — Phase 0: Foundation

> Dates: **Jun 1-7, 2026**
> Course: **C1 GenAI w/ LLMs (1/4)**
> Project: **—**
> Time budget: **3-4h**

---

## 🎯 This week's focus

> Intro, transformers high-level. Build the mental model before touching code.

---

## ✅ This week's goals

> Set on Monday. 3 max.

- [x] **Course:** Complete C1 Lesson 1 — intro + transformer architecture (high-level) ✅ 2026-06-03
- [x] **Notes:** 1-2 concept notes ✅ 2026-06-03
- [ ] **Stretch:** Watch 3Blue1Brown "Attention in transformers" (YouTube, 26 min)

---

## 📅 Realistic plan (3-4h, kid + work)

| Day | Time | Activity |
|-----|------|----------|
| Mon eve | 30m | Course lesson (after bedtime) |
| Wed eve | 30m | Reading / notes |
| Sat AM | 1.5-2h | Course labs / reading |
| Sun eve | 30m | Course wrap + retro |

---

## 📝 Session log

### Session 1 — Mon Jun 01
- Duration: 30 min
- Did: Watched C1 Lesson 1 — intro to generative AI, took rough notes
- Learned: LLM fundamentals (prompts, completion, inference, context window), RNN limitations, Transformer architecture at a high level (encoder, decoder, self-attention, tokenization)

### Session 2 — Wed Jun 03
- Duration: 30 min
- Did: Continued C1 Lesson 1 — in-context learning and LLM configuration
- Learned: In-context learning patterns (zero-shot, one-shot, few-shot prompting), how sampling parameters (temperature, top-p) alter text generation quality

### Session 3 — _(not completed — week ended)_
- _(stretch goal: 3Blue1Brown video — rolled to free time)_

---

## 🧠 Concept notes captured

| Concept                  | Confidence (L/M/H) | Note                                          |
| ------------------------ | ------------------- | --------------------------------------------- |
| LLM Fundamentals         | M                   | [[../concepts/phase-0/LLM Fundamentals]]         |
| Transformer Architecture | M                   | [[../concepts/phase-0/Transformer Architecture]] |
| In-Context Learning      | M                   | [[../concepts/phase-0/In-Context Learning]]      |
| Sampling Parameters      | H                   | [[../concepts/phase-0/sampling-parameters]]      |

> See [[_example-filled]] for how to fill weekly notes.
> See `concepts/` folder for example notes: [[../concepts/phase-0/sampling-parameters|sampling-parameters]], [[../concepts/phase-0/attention-intuition|attention-intuition]].

---

## 🛠️ Code / project progress

- Repo: —
- Commits this week: —
- Demo / screenshot: —

---

## 💸 Cost & usage

- Tokens (in/out): —
- Cost: $0 (no API calls yet — that's W5)
- API calls: 0

---

## 📓 Weekly journal

> Write on Sunday. ≥1 paragraph. Future-you + interviewer will read this.

Week 1 done — partial, but real. Two sessions (Mon + Wed), 60 minutes total. Watched C1 Lesson 1 start to finish across both sessions: transformer architecture, in-context learning, sampling parameters. 4 concept notes captured. The stretch (3Blue1Brown) didn't happen — that's fine, it wasn't a must-have.

The rhythm is not locked in yet. Sat AM block didn't happen this week. That's the slot that will make or break this path — 1.5h of uninterrupted time is worth more than 3 fragmented evenings. Need to protect it from W2 onward.

Mental model is starting to form: LLMs aren't magic, they're next-token prediction trained on massive data, tuned with instruction fine-tuning and RLHF. The gap between "completion model" and "assistant model" is instruction tuning. That clicked.

---

## ✅ Sunday retro

- [x] Hours logged: **1.0** / 3.5 _(partial — 2 sessions, no Sat AM)_
- [x] Goals hit: **2 / 3** (course ✅, notes ✅, stretch ❌)
- [x] Streak intact? **Y** (week 1 = streak starts)
- [x] Updated [[../02-progress-tracker]]
- [x] Next week's calendar blocked

### What worked
- Mon + Wed evening sessions worked well — short, focused, after bedtime
- 4 concept notes captured across 2 sessions — good density

### What didn't
- Sat AM block didn't happen — no protected slot for deeper work
- Session 3 / stretch goal never started

### Adjustment for next week
- Block Sat AM explicitly on calendar before Monday
- If Sat AM falls through → Fri night as backup. Never skip entirely.

### Confidence in path (1-10): **7**

Solid start mentally. The content clicked. The rhythm isn't locked yet — that's the real W1 risk. Need Sat AM to become automatic.

---

## 🎬 Kickoff note (read this first)

This is **Week 1**. The hardest week is usually Week 1.

You're not behind. You haven't started. **The path begins when you open the first lesson.**

This week's goal is **not** to master transformers. It's to:

1. Establish the weekly rhythm (Mon eve / Wed eve / Sat AM / Sun eve)
2. Get the mental model started — what are LLMs, how do they work at a high level
3. Prove to yourself you can show up

Python tooling comes in **W5** — after you have context for *why* you need structured outputs, Pydantic, and API calls. Theory first, tools second.

The path is **50 weeks**. The goal compounds. Just show up.

---

*Back to [[../02-progress-tracker]] · Next: [[week-02]]*
