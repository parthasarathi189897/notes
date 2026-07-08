---
type: ai-eng-week
week: 5
phase: 0
dates: "Jun 29 - Jul 5, 2026"
course: "— (Python Ramp)"
project: "—"
hours_target: 3.5
hours_logged: 1.67
status: in-progress
streak_before: 2
created: 2026-05-29
updated: 2026-07-04
tags:
  - study
  - ai-engineering
  - weekly
  - phase-0
  - python-ramp
---

# Week 5 — Phase 0: Python / Tooling Ramp

> Dates: **Jun 29 - Jul 5, 2026**
> Course: **— (No course this week. Tooling setup + Python fluency.)**
> Project: **—**
> Time budget: **3-4h**

---

## 🎯 This week's goals

> You now have 4 weeks of LLM mental model. This week you make it tangible with code.
> You know *what* transformers, instruction-tuning, and RLHF are. Now build the tools to *use* them.

- [ ] **Setup:** Install uv, create `aieng-sandbox` project, add openai + pydantic + httpx + pytest
- [ ] **Practice:** Make first LLM API call (OpenAI or Ollama), get structured JSON response validated by Pydantic
- [ ] **Stretch:** Write 3 pytest tests for a Pydantic model

---

## 📖 Reference material (~2h reading, skim before Saturday)

| Topic | Link | Time | Notes |
|-------|------|------|-------|
| **uv** | [Getting Started](https://docs.astral.sh/uv/getting-started/) | 10 min | `init`, `add`, `run` — that's all you need |
| **Pydantic v2** | [Models](https://docs.pydantic.dev/latest/concepts/models/) | 30 min | BaseModel, Field, validators. Skim once, reference later |
| **Pydantic v2** | [JSON Schema](https://docs.pydantic.dev/latest/concepts/json_schema/) | 15 min | `model_json_schema()` — how you tell the LLM what format to return |
| **OpenAI SDK** | [Quickstart](https://platform.openai.com/docs/quickstart) | 10 min | First API call in 5 min |
| **OpenAI SDK** | [Structured Outputs](https://platform.openai.com/docs/guides/structured-outputs) | 20 min | JSON mode + response_format. Used in every project |
| **Ollama** | [README](https://github.com/ollama/ollama/blob/main/README.md) | 10 min | Install + pull + run |
| **Ollama Python** | [ollama-python](https://github.com/ollama/ollama-python) | 10 min | Nearly drop-in for OpenAI SDK |
| **pytest** | [Getting Started](https://docs.pytest.org/en/stable/getting-started.html) | 15 min | First 2 sections only. Write a test, run it, done |

> **Skip for now** (will improve naturally): advanced Pydantic (generics, unions), httpx deep dive, Python type hints guide, FastAPI (not until P3).

---

## 📋 Python ramp checklist

> Complete these in order. Each builds on the last.

- [x] **uv setup** (30 min) — [docs](https://docs.astral.sh/uv/getting-started/) ✅ 2026-07-03
  - Install uv: `curl -LsSf https://astral.sh/uv/install.sh | sh`
  - `uv init aieng-sandbox && cd aieng-sandbox`
  - `uv add openai pydantic httpx pytest`
  - Verify: `uv run python -c "import openai; print('ready')"`

- [x] **Pydantic v2 basics** (60 min) ✅ 2026-07-03
  - Build 2-3 BaseModel classes (e.g., `SupportTicket`, `SentimentResult`)
  - Use `Field(description=...)` for each field
  - Use `model_validate_json()` to parse a raw JSON string
  - Use `model_json_schema()` to generate JSON schema — this becomes your LLM output format
  - Try a `field_validator` for custom validation

- [x] **First LLM API call** (45 min)
  - Call OpenAI (gpt-4o-mini) or Ollama (llama3.1:8b) with a system + user message
  - Prompt: "Given this product review, return JSON with {sentiment, summary, confidence}"
  - Parse response with Pydantic model
  - Test with `temperature=0` and `temperature=1` — now you know *why* these matter from C1
  - If using OpenAI: note the token count and cost from response headers

- [x] **pytest basics** (30 min, stretch)
  - Write a test: valid JSON → Pydantic model parses correctly
  - Write a test: invalid JSON → raises ValidationError
  - Write a test: missing required field → raises ValidationError
  - Run: `uv run pytest -v`

- [x] **Ollama setup** (30 min, optional)
  - Install Ollama: https://ollama.com
  - `ollama pull llama3.1:8b` (or `mistral:7b` if RAM is tight)
  - `ollama pull nomic-embed-text` (for later embedding work)
  - Test: same prompt as above, compare output quality to gpt-4o-mini
  - Notice how local model handles structured output differently — this connects to C1's discussion of model capabilities

---

## 📅 Realistic plan (3-4h, kid + work)

| Day | Time | Activity |
|-----|------|----------|
| Mon eve | 30m | Install uv, create project, add deps |
| Wed eve | 30-45m | Pydantic v2 basics |
| Sat AM | 1.5-2h | First API call + JSON extraction + Ollama setup |
| Sun eve | 15-30m | Stretch: pytest + retro |

---

## 📝 Session log

### Session 1 — Tue June 30
- **Duration:** 40
- **Did:** Watched pydantic basics https://www.youtube.com/watch?v=vVGXPRjtAJE 
- **Learned:** Basics of pydantic using BaseModel, custom validation, different type hints
- **Stuck on:**

### Session 2 — Sat July 4
- **Duration:** 60 min
- **Did:** Set up Ollama models, started watching httpx and async videos for python
- **Learned:**

### Session 3 — _date_
- **Duration:**
- **Did:**
- **Learned:**

---

## 🧠 Concept notes captured

| Concept         | Confidence (L/M/H) | Note                                            |
| --------------- | ------------------ | ----------------------------------------------- |
| pydantic        | M                  | [[pydantic]]                                    |
| async and httpx | M                  | [[../concepts/phase-1/async + httpx in python]] |
|                 |                    | [[../concepts/phase-1/event-loop-step-by-step]] |

> See [[_example-filled]] for how to fill concept notes.
> See `concepts/` folder for examples: [[../concepts/phase-0/sampling-parameters|sampling-parameters]], [[../concepts/phase-0/attention-intuition|attention-intuition]].

---

## 🛠️ Code / project progress

- Repo: `aieng-sandbox` (local only)
- Commits this week:
- Demo / screenshot:

---

## 💸 Cost & usage

- Tokens (in/out):
- Cost: $
- API calls:
- Ollama calls:

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

## 🔗 Why this week is here (not at W1)

You could have done this in Week 1. But doing it *after* C1 means:

- You know what temperature/top-p do → you test them **with understanding**
- You know about instruction-tuning → Pydantic structured outputs feel **purposeful**
- You've seen the LLM landscape → your first API call **connects to 4 weeks of context**
- The Phase 0 exit criteria ("explain pretraining vs RAG without notes") is satisfied → now you code

Next week (W6) you start C2 (Prompt Engineering). Your Python env is ready. No excuses.

---

*Prev: [[week-04]] · Back to [[../02-progress-tracker]] · Next: [[week-06]]*
