---
type: ai-eng-project
project: 4
parent: "[[README]]"
phase: 4
weeks: W27-30
done_by: 2026-12-27
repo: aieng-p04-rag-v2-evaluated
repo_url: ""
status: not-started
created: 2026-05-29
tags:
  - study
  - ai-engineering
  - project
---

# P4 — RAG v2 with Golden Set & Reranking

> **Phase 4** · Weeks **27-30** · Done by **Dec 27, 2026**
> Repo: `aieng-p04-rag-v2-evaluated` · [GitHub URL TBD]
> Full spec: [[README#🎯 Project 4 — RAG v2 with Golden Set & Reranking]]

---

## 🎯 What I'm shipping

From demo to **evaluated** system.

- 30-50 question golden dataset with expected source(s)
- 2+ retrieval improvements (query expansion, reranking, hybrid, metadata filters)
- Metrics: retrieval relevance, answer correctness, groundedness
- Baseline vs improved comparison
- Failure log with ≥5 categorized failure modes

---

## ✅ Acceptance criteria

- [ ] 30+ golden questions with expected sources documented
- [ ] Baseline retrieval relevance recorded
- [ ] Improved retrieval relevance recorded (≥ baseline)
- [ ] Groundedness metric implemented + run
- [ ] Answer correctness measured (manual or LLM-judge)
- [ ] Failure log has ≥5 categorized modes
- [ ] Write-up: what worked, what didn't, what's next
- [ ] Pushed to public repo `aieng-p04-rag-v2-evaluated`

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W27 | Copy P3 baseline into new repo; pick 2 improvements (eg reranking + query expansion); start golden set | ⬜ |
| W28 | Golden set to 30 questions; baseline scores recorded | ⬜ |
| W29 | Implement improvements; run + score | ⬜ |
| W30 | Baseline vs improved write-up, failure log, ship | ⬜ |

---

## 🛠️ Decisions log

- Reranker choice:
- Query expansion strategy:
- Groundedness metric (LLM-judge or custom):
- Golden set creation process:

---

## 📊 Numbers

| Metric | Baseline | Improved | Delta |
|--------|----------|----------|-------|
| Retrieval relevance | | | |
| Groundedness | | | |
| Answer correctness | | | |
| Avg latency | | | |
| Avg cost per query | | | |

---

## 🐛 Failure modes (categorized — ≥5)

1.
2.
3.
4.
5.

---

## 📝 Post-mortem

**What worked:**
**What didn't:**
**Where does P5 (eval harness) need to go next?**
**One thing I can defend in an interview:**

---

*Back to [[README]] · [[../02-progress-tracker]]*
