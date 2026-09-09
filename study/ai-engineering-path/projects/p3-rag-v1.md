---
type: ai-eng-project
project: 3
parent: "[[README]]"
phase: 3
weeks: W20-25
done_by: 2027-02-28
repo: aieng-p03-rag-v1
repo_url: ""
status: not-started
created: 2026-05-29
tags:
  - study
  - ai-engineering
  - project
---

# P3 — RAG v1 (citations + logging)

> **Phase 3** · Weeks **20-25** · Done by **Feb 28, 2027**
> Repo: `aieng-p03-rag-v1` · [GitHub URL TBD]
> Full spec: [[README#📚 Project 3 — RAG v1]]
> **This is your biggest project so far. 6 weeks. Pace yourself.**

---

## 🎯 What I'm shipping

End-to-end RAG, built by hand:
- Ingestion → chunking → embedding → vector storage
- Query → retrieval → prompt construction → LLM call → answer with **citations**
- Logging: query, retrieved chunks, prompt, final answer, cost, latency

**No LangChain. No LlamaIndex.** Python + (optional) FastAPI.

---

## ✅ Acceptance criteria

- [ ] Ingests 50+ documents
- [ ] Answers 10 sample questions with citations that resolve to real chunks
- [ ] Every query produces a full log entry (JSON / DB row)
- [ ] Manual review: 7/10 sample answers grounded in retrieved chunks
- [ ] Cost + latency per query tracked
- [ ] README explains architecture with a diagram
- [ ] Pushed to public repo `aieng-p03-rag-v1`

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W20 | Scaffold repo, project plan, copy P2 ingestion as starting point | ⬜ |
| W21 | Ingestion pipeline working on 50+ docs | ⬜ |
| W22 | Retrieval working, top-k tuned | ⬜ |
| W23 | Generation with prompt template, raw answers OK | ⬜ |
| W24 | Citations + structured logging | ⬜ |
| W25 | 10 sample Qs manual review, README + diagram, ship | ⬜ |

---

## 🛠️ Decisions log

- LLM provider for generation:
- Vector store (continuing from P2 or new):
- Prompt template structure:
- Citation format:
- Log storage (JSONL / SQLite / other):

---

## 📊 Numbers

- Docs ingested:
- Avg cost per query:
- Avg latency per query:
- Manual quality score: __/10
- Hallucination rate observed:

---

## 🐛 Failure modes observed

> The list you grow here = P4's golden test set seed.

-

---

## 📝 Post-mortem

**What worked:**
**What didn't:**
**Where will RAG v2 focus first?**
**One thing I can defend in an interview:**

---

*Back to [[README]] · [[../02-progress-tracker]]*
