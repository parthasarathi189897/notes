---
type: ai-eng-week
week: 3
phase: 0
dates: "Jun 15-21, 2026"
course: "C1 GenAI w/ LLMs (2/4 finish + 3/4)"
project: "—"
hours_target: 4.0
hours_logged: 1.33
status: done
streak_before: 0
catch_up_note: "W2 slipped — absorbing W2 remainder (C1 2/4) + W3 original content (C1 3/4) this week. Hours target bumped to 4h."
created: 2026-05-29
updated: 2026-06-21
tags:
  - study
  - ai-engineering
  - weekly
  - phase-0
  - catch-up
---

# Week 3 — Phase 0: Foundation (Catch-up Week)

> Dates: **Jun 15-21, 2026**
> Course: **C1 GenAI w/ LLMs (2/4 finish + 3/4)**
> Project: **—**
> Time budget: **3.5-4h** _(+0.5h to absorb W2 slip)_

> ⚠️ **Catch-up note:** W2 slipped (0.83h / 3.5h). This week absorbs the C1 (2/4) remainder (instruction tuning) **plus** the original W3 content (RLHF + evaluation basics). This is achievable — instruction tuning + RLHF are tightly related and combine well in one week.

---

## 🎯 This week's focus

> **Instruction tuning → RLHF → evaluation basics.** These three form a chain: base model → instruction-tuned → aligned via RLHF → evaluated. Understand the chain end-to-end before moving on.

---

## ✅ This week's goals

> 3 max. One must-have, one core, one stretch.

- [x] **Course (must-have):** Finish C1 (2/4) — instruction tuning. Then complete C1 (3/4) — RLHF + evaluation metrics ✅ 2026-06-16
- [x] **Notes:** 1-2 concept notes (RLHF intuition and/or instruction tuning mechanics) ✅ 2026-06-21
- [ ] **Stretch:** Watch the [RLHF + PPO intuition video](https://www.youtube.com/watch?v=2MBJOuVq380) if time allows (~15 min)

---

## 📅 Realistic plan (4h, kid + work)

| Day | Time | Activity |
|-----|------|----------|
| Mon eve | 30m | Finish C1 (2/4) — instruction tuning remainder |
| Wed eve | 45m | C1 (3/4) — RLHF + evaluation basics |
| Fri eve | 30m | Concept note: RLHF intuition |
| Sat AM | 1.5-2h | C1 (3/4) labs + RLHF deep dive + concept note |
| Sun eve | 30m | Retro + tracker update |

> **Sat AM is non-negotiable.** If Mon or Wed fall through → shift to Tue/Thu. Don't skip — shift.
> Fri evening added as backup slot for the catch-up buffer.

---

## 📝 Session log

### Session 1 — Tue Jun 16
- **Duration:** 20 min
- **Did:** Watched videos on Parameter Efficient Fine-Tuning (PEFT)
- **Learned:** PEFT / LoRA fundamentals — why updating only low-rank adapters is more efficient than full fine-tuning and avoids catastrophic forgetting

### Session 2 — Wed Jun 17
- **Duration:** 30 min
- **Did:** Completed C1 lab (instruction tuning / fine-tuning lab)
- **Learned:** Hands-on: LoRA config, trainable parameter count, how to attach adapters to a HuggingFace model

### Session 3 — Sat Jun 20
- **Duration:** 30 min
- **Did:** Watched C1 (3/4) videos on RLHF
- **Learned:** RLHF pipeline — reward model training, PPO, KL-divergence penalty, reward hacking, Constitutional AI, RLAIF

---

## 🧠 Concept notes captured

| Concept                              | Confidence (L/M/H) | Note                                                      |
| ------------------------------------ | ------------------ | --------------------------------------------------------- |
| Fine Tuning                          | M                  | [[../concepts/phase-0/Fine Tuning]]                          |
| Model Evaluation                     | M                  | [[../concepts/phase-0/Model Evaluation]]                     |
| Reinforcement Learning from Human Feedback | L            | [[../concepts/phase-0/Reinforcement learning - Human feedback]] |

---

## 🛠️ Code / project progress

- Repo: —
- Commits this week: —
- Demo / screenshot: —

---

## 💸 Cost & usage

- Tokens (in/out): —
- Cost: $0
- API calls: 0

---

## 📓 Weekly journal

> Write on Sunday. ≥1 paragraph. Future-you + interviewer will read this.

<write here>

---

## ✅ Sunday retro

- [x] Hours logged: 1.33 / 4.0  _(3 sessions × ~20-30m)_
- [x] Goals hit: 2 / 3  _(course + concept notes ✅; stretch video ⏭️)_
- [ ] Streak intact? (Y/N)
- [x] Catch-up complete? C1 (2/4) ✅ + C1 (3/4) ✅  _(content covered; hours below target)_
- [ ] Updated [[../02-progress-tracker]]
- [ ] Next week's calendar blocked

### What worked
-

### What didn't
-

### Adjustment for next week
-

### Confidence in path (1-10): _

---

*Prev: [[week-02]] · Back to [[../02-progress-tracker]] · Next: [[week-04]]*
