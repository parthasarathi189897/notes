---
type: ai-eng-project
project: 1
parent: "[[README]]"
phase: 1
weeks: W8-10
done_by: 2026-10-11
repo: aieng-p01-json-extractor
repo_url: ""
status: not-started
created: 2026-05-29
tags:
  - study
  - ai-engineering
  - project
---

# P1 — LLM JSON Extractor / Classifier

> **Phase 1** · Weeks **8-10** · Done by **Oct 11, 2026**
> Repo: `aieng-p01-json-extractor` · [GitHub URL TBD]
> Full spec: [[README#🧱 Project 1 — LLM JSON Extractor / Classifier (W8-10)]]

---

## 🎯 What I'm shipping

Python CLI: takes a messy support message, returns validated JSON with category, sentiment, urgency, summary, suggested response, confidence. Tracks tokens + cost per call. Retries on bad JSON.

**No LangChain. Plain Python + Pydantic.**

---

## ✅ Acceptance criteria

- [ ] Runs on 20 hand-crafted test inputs without crashing
- [ ] 100% of outputs validate against Pydantic schema (with retry logic)
- [ ] Logs token count and $ cost per call
- [ ] README explains design choices in <300 words
- [ ] Pushed to public repo `aieng-p01-json-extractor`

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W8 | Scaffold repo, Pydantic schema, basic LLM call | ⬜ |
| W9 | Retry logic, 20 test inputs, cost tracking | ⬜ |
| W10 | Polish, README, tests, ship | ⬜ |

---

## 🛠️ Decisions log

> Capture every meaningful tradeoff. Future-you will thank you.

- LLM provider:
- Schema validation lib:
- Retry strategy:
- Cost tracking approach:

---

## 📊 Numbers

- Avg input tokens:
- Avg output tokens:
- $ per call:
- p95 latency:
- Pass rate on 20 test inputs: __/20

---

## 🐛 Failure modes observed

-

---

## 📝 Post-mortem (write after shipping)

**What worked:**
**What didn't:**
**What I'd do differently:**
**One thing I can defend in an interview:**

---

*Back to [[README]] · [[../02-progress-tracker]]*
