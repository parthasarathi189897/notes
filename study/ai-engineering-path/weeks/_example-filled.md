---
type: ai-eng-week
week: 5
phase: 0
dates: "Jun 29 - Jul 5, 2026"
course: "—"
project: "—"
hours_target: 3.5
hours_logged: 3.0
status: completed
streak_before: 0
created: 2026-06-01
updated: 2026-06-07
tags:
  - study
  - ai-engineering
  - weekly
  - phase-0
  - example
---

# 📌 EXAMPLE — How to fill a weekly note

> **This is a reference file.** It shows what a completed week looks like.
> Copy the patterns here into your real `week-NN.md` files.
> Delete this file once you're comfortable with the format.

---

# Week 5 — Phase 0: Python Ramp

> Dates: **Jun 29 - Jul 5, 2026**
> Course: **— (Python/tooling setup, after C1)**
> Project: **—**
> Time budget: **3-4h**

---

## 🎯 This week's goals

- [x] **Setup:** Install uv, create sandbox project, add openai + pydantic
- [x] **Practice:** Make first LLM API call, get JSON response
- [ ] **Stretch:** Write 3 pytest tests _(didn't get to this — moved to next week)_

---

## 📅 Realistic plan (3-4h, kid + work)

| Day | Time | Activity |
|-----|------|----------|
| Mon eve | 30m | Install uv, create project |
| Wed eve | 30m | Pydantic v2 basics — BaseModel, validators |
| Sat AM | 1.5h | First API call + JSON extraction experiment |
| Sun eve | 30m | Review + retro |

---

## 📝 Session log

### Session 1 — Mon Jun 29
- **Duration:** 35m
- **Did:** Installed uv (`curl -LsSf https://astral.sh/uv/install.sh | sh`). Created `aieng-sandbox` project. Added openai, pydantic, httpx.
- **Learned:** `uv init` + `uv add` is dramatically faster than pip. Creates `pyproject.toml` automatically. Virtual env is managed — no more `source venv/bin/activate` dance.
- **Stuck on:** Nothing — smooth start. Good momentum.

### Session 2 — Wed Jul 1
- **Duration:** 40m
- **Did:** Went through Pydantic v2 docs. Built 3 models: `SupportTicket`, `SentimentResult`, `LLMResponse`. Tested validators and `model_json_schema()`.
- **Learned:** Pydantic v2 has `model_validate_json()` which parses raw JSON string directly — useful for LLM output parsing. `Field(description=...)` is key for generating schemas that can be passed to the LLM.
- **Stuck on:** Pydantic v2 breaking changes from v1. `validator` → `field_validator`, `.dict()` → `.model_dump()`. Quick to fix once I knew.

### Session 3 — Sat Jul 4
- **Duration:** 1h45m
- **Did:** First OpenAI API call. Tested system/user messages. Tried temperature 0 vs 0.7 vs 1.5. Built a tiny script: input a product review → get JSON with {sentiment, summary, confidence}. Used Pydantic to validate the response.
- **Learned:**
  - `temperature=0` is NOT deterministic — got slightly different outputs on 2 identical calls. Need to use `seed` param for best-effort reproducibility.
  - JSON mode requires BOTH `response_format={"type": "json_object"}` AND explicit instruction in the prompt. API errors if you forget the prompt instruction.
  - Cost per call with gpt-4o-mini: ~$0.001 for a simple extraction. Cheap enough for dev. Eval runs at scale will add up though.
- **Stuck on:** Got a 429 rate limit after rapid-fire testing. Need to add exponential backoff. Will address in P1.

### Session 4 — Sun Jul 5
- **Duration:** 15m
- **Did:** Retro + concept notes + tracker update
- **Learned:** The weekly rhythm works. Sat AM nap window is gold.

---

## 🧠 Concept notes captured

| Concept                           | Confidence (L/M/H) | Note                                |
| --------------------------------- | ------------------ | ----------------------------------- |
| Sampling parameters (temp, top-p) | H                  | [[../concepts/sampling-parameters]] |
| Pydantic v2 for LLM outputs       | M                  | _(write next week)_                 |

---

## 🛠️ Code / project progress

- Repo: `aieng-sandbox` (local only, not published)
- Commits this week: 4 (init, pydantic models, first API call, json extraction)
- Demo / screenshot: CLI prints validated JSON from product review input ✅

---

## 💸 Cost & usage

- Tokens: 8,200 in / 2,100 out (gpt-4o-mini)
- Cost: $0.02
- API calls: 31
- Ollama: not set up yet — will try `llama3.1:8b` next week

---

## 📓 Weekly journal

> Write on Sunday. ≥1 paragraph. Future-you + interviewer will read this.

Week 5 done — the bridge between theory and code. After 4 weeks of C1, doing the Python ramp felt *purposeful* rather than abstract. When I tested temperature=0 vs 1, I already knew from C1 that this controls sampling from the probability distribution. When I built Pydantic models for structured outputs, I understood *why* the model needs explicit format instructions — instruction-tuned models are trained to follow instructions, not magically produce JSON.

The real insight was from the Saturday session: temperature=0 is not deterministic. I assumed it was. It's not — GPU floating point + batching introduces variation. This has direct implications for evals: never assert exact string equality on LLM outputs. Always compare structured fields or use semantic similarity. Filing that under "things I would only learn by building."

Skipped pytest this week. Not worried — it's a stretch goal and I'll pick it up alongside C2. Momentum matters more than completeness. Python environment is ready. No more excuses.

---

## ✅ Sunday retro

- [x] Hours logged: **3.0** / 3.5
- [x] Goals hit: **2 / 3** (missed pytest stretch)
- [x] Streak intact? **Y** (streak = 1 🔥)
- [x] Updated [[../02-progress-tracker]]
- [x] Next week's calendar blocked

### What worked
- Saturday nap window = uninterrupted deep work. Protect this slot.
- uv made Python tooling feel as good as Node tooling. No friction.

### What didn't
- Monday evening was tight — kid woke up at 9pm, cut session short.
- Didn't get to pytest. Planned too much for week 1.

### Adjustment for next week
- If Mon fails → shift to Tue. Don't skip, shift.
- Cap weekly goals at 2 must-haves + 1 stretch. Don't overplan.

### Confidence in path (1-10): **8**

High because: 4 weeks of theory made this week's code feel grounded, not random. The first API call felt like the first `fetch()` call 15 years ago. Same energy, different era. This is going to work.

---

*Back to [[../02-progress-tracker]] · Next: [[week-06]]*
