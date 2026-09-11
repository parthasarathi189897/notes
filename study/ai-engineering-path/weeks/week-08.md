---
type: ai-eng-week
week: 8
phase: 1
dates: "Sep 7-13, 2026"
original_target: "Aug 27 - Sep 2, 2026"
course: C3 Building Systems (1/2)
project: P1 scaffold
hours_target: 3.5
hours_logged: 1
status: in-progress
streak_before: 0
created: 2026-05-29
tags:
  - study
  - ai-engineering
  - weekly
  - phase-1
---
# Week 8 — Phase 1: App Basics
> Dates: **Sep 7-13, 2026**
> Course: **C3 Building Systems (1/2)**
> 📚 Course: [Building Systems with the ChatGPT API](https://learn.deeplearning.ai/courses/chatgpt-building-system/lesson/k0pk1/introduction) — DeepLearning.AI
> Project: **P1 scaffold**
> Time budget: **3-4h**
> Project spec: [[../projects/p1-llm-json-extractor]]

---

## 🎯 This week's focus
> Chaining + breakdowns; scaffold `aieng-p01-json-extractor` repo

---

## ✅ This week's goals
> Set on Monday. 3 max.
- [x] **Course:** complete this week's lessons — chaining, moderation, and evaluation (intro) covered
- [ ] **Project:** P1 scaffold — not started, deferred to focus on course completion first
- [x] **Notes:** 1-2 concept notes — Pydantic concept note + prompt chaining + evaluation notes captured

---

## ✅ Done when
> The single checkable condition for this slot. Approved 2026-09-07.
> A written note is not a shipped artifact.
- [ ] Repo `aieng-p01-json-extractor` is public, with `pyproject.toml` and one passing test committed.

---

## 📅 Realistic plan (3-4h, kid + work)
| Day | Time | Activity |
|-----|------|----------|
| Mon eve | 30m | Course lesson (after bedtime) |
| Wed eve | 30m | Reading / notes |
| Sat AM | 1.5-2h | Project work (nap window) |
| Sun eve | 30m | Course wrap + retro |

---

## 📝 Session log
### Session 1 — Mon, 17 August
- Duration: 30 min
- Did: Watched the first video in the course
- Learned: Recap my past learnings on the concept of token, prompt, completion, context window, transformer and different type of language models

### Session 2 — Fri, 21 August
- Duration: 30 min
- Did: Watched few video
- Learned: Classification, moderation and prompt injection prevention

### Session 3 — Sep 11, 2026
- Duration: ~30 min
- Did: Watched chaining prompts + moderation sections; discussed with coach
- Learned: Chaining rationale (context efficiency, separation of concerns, cost/model optimization, debuggability); moderation API vs. LLM-as-judge are complementary, not either/or — moderation API catches generic harm categories, LLM-as-judge catches business-specific issues (hallucination, policy violations, off-topic responses) that moderation API structurally can't detect

### Session 4 — Sep 11, 2026 (later)
- Duration: ~20 min
- Did: Started evaluation section of the course
- Learned: Why eval matters (relevance, format correctness, consistency across inputs); the core challenge of grading non-deterministic LLM output; spectrum of eval techniques — structural/format checks (code-only, e.g. Pydantic validation), exact-match checks (small fixed answer sets), semantic/quality checks (embedding similarity or LLM-as-judge). Eval section not yet finished — continuing tomorrow.

---

## 🧠 Concept notes captured
| Concept | Confidence (L/M/H) | Note |
|---------|--------------------|------|
| Pydantic fundamentals | H | [[concept-note-pydantic]] |
| Prompt chaining | M | [[concept-note-prompt-chaining]] |
| Evaluation (evals) | M (in progress) | [[concept-note-evaluation]] |

---

## 🛠️ Code / project progress
- Repo: (see [[../projects/p1-llm-json-extractor]] for repo name)
- Commits this week: none yet
- Demo / screenshot: none yet — extensive Pydantic hands-on practice done outside the repo (field_validator, model_validator, nested models) in preparation for P1

---

## 💸 Cost & usage
- Tokens (in/out):
- Cost: $
- API calls:

---

## 📓 Weekly journal
> Write on Sunday. ≥1 paragraph. Future-you + interviewer will read this.
<write here>

---

## ✅ Sunday retro
- [ ] Hours logged: ___ / 3.5
- [ ] Goals hit: ___ / 3
- [ ] Streak intact? (Y/N)
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

*Prev: [[week-07]] · Back to [[../02-progress-tracker]] · Next: [[week-09]]*
