---
type: ai-eng-project
project: 2
parent: "[[README]]"
phase: 2
weeks: W13-15
done_by: 2026-09-13
repo: aieng-p02-semantic-search
repo_url: ""
status: not-started
created: 2026-05-29
tags:
  - study
  - ai-engineering
  - project
---

# P2 — Semantic Search Engine

> **Phase 2** · Weeks **13-15** · Done by **Sep 13, 2026**
> Repo: `aieng-p02-semantic-search` · [GitHub URL TBD]
> Full spec: [[README#🔍 Project 2 — Semantic Search Engine]]

---

## 🎯 What I'm shipping

Python CLI: ingest local docs (md/PDF/text), chunk, embed, vector store, top-k retrieval with file/section metadata and similarity scores.

**Retrieval only. No generation. Yet.**

---

## ✅ Acceptance criteria

- [ ] Indexes 100+ documents
- [ ] Top-5 results manually relevant on 10 hand-picked queries
- [ ] Chunk metadata preserved (file, page, section)
- [ ] Indexing time + query latency logged
- [ ] README explains: chunking strategy, embedding model, storage choice
- [ ] Pushed to public repo `aieng-p02-semantic-search`

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W13 | Scaffold, choose vector store (FAISS / Chroma / Qdrant), ingestion pipeline | ⬜ |
| W14 | Embedding + storage + retrieval, metadata | ⬜ |
| W15 | 10 queries, polish, README, ship | ⬜ |

---

## 🛠️ Decisions log

- Vector store choice:
- Embedding model:
- Chunk size / overlap:
- PDF extraction tool:

---

## 📊 Numbers

- Docs indexed:
- Total chunks:
- Index build time:
- Avg query latency:
- Top-5 relevance (manual): __/50

---

## 🐛 Failure modes observed

-

---

## 📝 Post-mortem

**What worked:**
**What didn't:**
**What I'd do differently:**
**One thing I can defend in an interview:**

---

*Back to [[README]] · [[../02-progress-tracker]]*
