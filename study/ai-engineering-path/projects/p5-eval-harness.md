---
type: ai-eng-project
project: 5
parent: "[[README]]"
phase: 5
weeks: W33-34
done_by: 2027-05-09
repo: aieng-p05-eval-harness
repo_url: ""
status: not-started
created: 2026-05-29
tags:
  - study
  - ai-engineering
  - project
---

# P5 — Evaluation Harness

> **Phase 5** · Weeks **33-34** · Done by **May 9, 2027**
> Repo: `aieng-p05-eval-harness` · [GitHub URL TBD]
> Full spec: [[README#🔬 Project 5 — Evaluation Harness]]
>
> **Reusable target.** Plan to install this into P3, P4, P9.

---

## 🎯 What I'm shipping

A repeatable, scriptable eval runner. Foundation for CI gating (P8).

- Input: `test_questions.jsonl`
- Per question: retrieval → generation → score → save
- Output: `eval_results.jsonl` (retrieval, groundedness, answer quality)
- Summary report (markdown / HTML), historical trend tracking

---

## ✅ Acceptance criteria

- [ ] Single command runs full eval suite
- [ ] Runs 30+ golden questions in <10 min
- [ ] Produces summary report (markdown / HTML)
- [ ] Tracks deltas vs baseline (regression detection)
- [ ] Stores historical results
- [ ] Triggerable manually OR via CI hook
- [ ] Pushed to public repo `aieng-p05-eval-harness`
- [ ] **Installable via pip** (publish to TestPyPI or just `pip install git+...`)

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W33 | Scaffold package, CLI entrypoint, JSONL input/output | ⬜ |
| W34 | Retrieval/groundedness/correctness scorers, summary report, history, ship | ⬜ |

---

## 🛠️ Decisions log

- Package structure (`pyproject.toml`):
- Scorer plugin interface:
- Report format:
- History storage (JSONL append / sqlite):

---

## 📊 Performance

- Run time on 30 questions:
- Memory footprint:
- Parallelization?:

---

## 🐛 Failure modes observed

-

---

## 📝 Post-mortem

**What worked:**
**What didn't:**
**How will I wire this into P9 capstone?**
**One thing I can defend in an interview:**

---

*Back to [[README]] · [[../02-progress-tracker]]*
