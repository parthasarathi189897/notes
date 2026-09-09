---
type: study-path-projects
parent: "[[../README]]"
projects_total: 9
created: 2026-05-29
updated: 2026-05-29
tags:
  - study
  - ai-engineering
  - projects
---

# Projects Index

> ⛔ **SUPERSEDED — see [[PROGRESS]].** Dates and project week-ranges in this file are pre-rebase
> (it still shows P1 due Aug 9, 2026). Acceptance criteria below remain authoritative and unchanged.


> 9 projects. **Each lives in its own GitHub repo** for portfolio clarity.
> Each has **measurable acceptance criteria** in its dedicated note.
> A project is "done" only when criteria pass. Not when the code "kinda works."

---

## 🗂️ Repo strategy — separate repos

**Why separate:** Each repo = standalone portfolio piece. Hiring managers can read one project without context-switching. Easier to share, star, demo.

**Naming convention:** `aieng-pNN-<short-name>`

```
aieng-p01-json-extractor
aieng-p02-semantic-search
aieng-p03-rag-v1
aieng-p04-rag-v2-evaluated
aieng-p05-eval-harness
aieng-p06-finetuning-memo
aieng-p07-research-agent
aieng-p08-ci-eval-pipeline
aieng-p09-capstone
```

**Cross-project code reuse:**
- **P3 → P4:** Copy v1 baseline into v2 repo (cleaner than submodule for portfolio).
- **P5 eval harness:** Publish as a pip-installable package OR vendor the runner into P3, P4, P9.
- **P9 capstone:** May depend on P5 (eval harness) as installed package.

**Repo template — what every project repo needs:**
```
aieng-pNN-<name>/
├── README.md           # Problem → approach → tradeoffs → numbers → demo
├── ARCHITECTURE.md     # Diagram + design decisions
├── pyproject.toml      # uv / pip dependencies
├── src/                # Code
├── tests/              # Unit tests
├── evals/              # Golden set + eval scripts (where applicable)
├── notebooks/          # Exploration (optional)
├── docs/screenshots/   # For UI projects (P9)
└── .github/workflows/  # CI (P5+)
```

**Every README answers:**
1. What problem does this solve?
2. What was the approach?
3. What tradeoffs did I make?
4. What are the measured numbers (latency, accuracy, cost)?
5. How do I run it?
6. What would I do differently next time?

---

## 📋 The 9 projects

| # | Project | Phase | Done by | Repo | Spec |
|---|---------|-------|---------|------|------|
| 1 | LLM JSON Extractor / Classifier | 1 | W10 (Aug 9, 2026) | `aieng-p01-json-extractor` | [[p1-llm-json-extractor]] |
| 2 | Semantic Search Engine (+eval) | 2 | W15 (Sep 27) | `aieng-p02-semantic-search` | [[p2-semantic-search]] |
| 3 | RAG v1 — citations + logging | 3 | W23 (Nov 22) | `aieng-p03-rag-v1` | [[p3-rag-v1]] |
| 4 | RAG v2 — golden set + reranking | 4 | W28 (Jan 3, 2027) | `aieng-p04-rag-v2-evaluated` | [[p4-rag-v2-evaluated]] |
| 5 | Evaluation Harness | 5 | W33 (Feb 7) | `aieng-p05-eval-harness` | [[p5-eval-harness]] |
| 6 | Fine-tuning Decision Memo | 6 | W37 (Mar 7) | `aieng-p06-finetuning-memo` | [[p6-finetuning-memo]] |
| 7 | Simple Research Agent | 7 | W42 (Apr 18) | `aieng-p07-research-agent` | [[p7-research-agent]] |
| 8 | CI Eval Pipeline | 8 | W46 (May 16) | `aieng-p08-ci-eval-pipeline` | [[p8-ci-eval-pipeline]] |
| 9 | **Capstone — Knowledge Assistant** | 8 | W48 (May 30) | `aieng-p09-capstone` | [[p9-capstone]] |

---

## 🧱 Project 1 — LLM JSON Extractor / Classifier (W8-10) · [[p1-llm-json-extractor]]

**Goal:** Treat the LLM as an API. Get clean, structured outputs reliably.

**Build a Python CLI that:**
- Takes a messy customer support message
- Returns JSON with: `category`, `sentiment`, `urgency`, `summary`, `suggested_response`, `confidence`
- Validates output with Pydantic
- Retries on malformed JSON

**Constraints:**
- ❌ No LangChain
- ✅ Plain Python + Pydantic
- ✅ Track tokens + cost per call

**Acceptance criteria:**
- [ ] Runs on 20 hand-crafted test inputs without crashing
- [ ] 100% of outputs validate against Pydantic schema (with retry logic)
- [ ] Logs token count and $ cost per call
- [ ] README explains design choices in <300 words
- [ ] Pushed to public repo

---

## 🔍 Project 2 — Semantic Search Engine (W13-15) · [[p2-semantic-search]]

**Goal:** Retrieval before generation. Prove you understand embeddings + vector search.

**Build a Python CLI that:**
- Ingests markdown/PDF/text from a local folder
- Chunks, embeds, stores vectors (FAISS, Chroma, or Qdrant — pick one)
- Returns top-k matches with: source file, snippet, similarity score, section metadata
- NO generation yet — retrieval only

**Acceptance criteria:**
- [ ] Indexes 100+ documents
- [ ] Top-5 results manually relevant on 10 hand-picked queries
- [ ] Chunk metadata preserved (file, page, section)
- [ ] Indexing time + query latency logged
- [ ] **5-question retrieval eval:** query → expected top-3 sources documented, recall@5 score computed
- [ ] Eval script runs in one command and prints scores
- [ ] README explains: chunking strategy, embedding model, storage choice
- [ ] Pushed to public repo

---

## 📚 Project 3 — RAG v1 (W20-25) · [[p3-rag-v1]]

**Goal:** Build RAG end-to-end **by hand**. No framework crutch.

**Features:**
- Document ingestion → chunking → embedding → vector storage
- Query → retrieval → prompt construction → LLM call → answer
- **Citations** with source snippets
- Logging: query, retrieved chunks, prompt, final answer, cost, latency

**Constraints:**
- ❌ No LangChain, no LlamaIndex
- ✅ Python + FastAPI (if you want an API)
- ✅ Manual prompt template

**Acceptance criteria:**
- [ ] Ingests 50+ documents successfully
- [ ] Answers 10 sample questions with citations that resolve to real chunks
- [ ] Every query produces a full log entry (JSON file or DB row)
- [ ] Manual review: 7/10 sample answers are factually grounded in retrieved chunks
- [ ] Cost + latency per query tracked
- [ ] README explains the architecture with a diagram
- [ ] Pushed to public repo

---

## 🎯 Project 4 — RAG v2 with Golden Set & Reranking (W27-30) · [[p4-rag-v2-evaluated]]

**Goal:** From demo to evaluated system. Numbers, not vibes.

**Upgrade RAG v1 with:**
- Golden dataset: 30-50 questions, each with expected source doc(s)
- At least 2 retrieval improvements (pick from: query expansion, reranking, hybrid search, metadata filtering)
- Metrics: retrieval relevance, answer correctness, groundedness
- Baseline vs improved comparison report
- Failure log of bad answers

**Acceptance criteria:**
- [ ] 30+ golden questions with expected sources documented
- [ ] Baseline retrieval relevance score recorded
- [ ] Improved retrieval relevance score recorded (must be ≥ baseline)
- [ ] Groundedness metric implemented and run on golden set
- [ ] Answer correctness measured (manual or LLM-judge)
- [ ] Failure log has ≥5 categorized failure modes
- [ ] Write-up: what worked, what didn't, what's next
- [ ] Pushed to public repo

---

## 🔬 Project 5 — Evaluation Harness (W33-34) · [[p5-eval-harness]]

**Goal:** A repeatable, scriptable eval runner. The foundation for CI gating.

**Build:**
- Input: `test_questions.jsonl`
- For each question: run retrieval → run generation → score → save
- Output: `eval_results.jsonl` with retrieval, groundedness, answer quality scores
- Summary report: pass/fail rates, deltas vs baseline

**Acceptance criteria:**
- [ ] Single command runs full eval suite end-to-end
- [ ] Runs on 30+ golden questions in <10 minutes
- [ ] Produces summary report (markdown or HTML)
- [ ] Tracks deltas vs baseline (regression detection)
- [ ] Stores historical results so you can chart trends
- [ ] Can be triggered manually OR by CI hook
- [ ] Pushed to public repo

---

## 📝 Project 6 — Fine-tuning Decision Memo (W37-38) · [[p6-finetuning-memo]]

**Goal:** Resist fine-tuning hype. Write a memo that proves you know when it's right.

**Write a memo answering:**
- Task: what specifically would we fine-tune for?
- Why prompting alone isn't enough (with evidence)
- Why RAG alone isn't enough (with evidence)
- What training data is needed (size, source, quality)
- Expected metric improvement (specific numbers)
- Failure risks
- Cost estimate (training + inference)
- Rollback plan

**Optional hands-on:** Fine-tune a narrow task (classification or structured extraction). NOT a general chatbot.

**Acceptance criteria:**
- [ ] Memo is ≤2 pages, written for a non-AI engineer audience
- [ ] All 8 sections above answered with specifics, not platitudes
- [ ] Includes a concrete "go / no-go" recommendation
- [ ] Optional: narrow fine-tune experiment with before/after metrics
- [ ] Pushed to public repo

---

## 🤖 Project 7 — Simple Research Agent (W40-43) · [[p7-research-agent]]

**Goal:** One reliable agent > five flaky ones.

**Build an agent that:**
- Takes a user question
- Plans steps
- Retrieves from local docs
- Calls tools if needed (web search, calculator, code exec — pick 1-2)
- Logs each step
- Synthesizes a cited answer
- Includes a trajectory evaluation

**Acceptance criteria:**
- [ ] Handles 10 sample queries end-to-end without crashing
- [ ] Every step logged (planner output, tool calls, intermediate results)
- [ ] Final answer cites sources
- [ ] Trajectory eval: scores each run on plan quality, tool selection, answer correctness
- [ ] Manual review: 7/10 trajectories are "reasonable"
- [ ] README explains agent design + failure modes observed
- [ ] Pushed to public repo

---

## 🚦 Project 8 — CI Eval Pipeline (W46-47) · [[p8-ci-eval-pipeline]]

**Goal:** Evals run on every push. Bad changes fail the build.

**Build:**
- GitHub Action (or similar) that runs on every PR
- Runs unit tests
- Runs ≥10 smoke eval questions from golden set
- Compares against baseline scores
- Fails the build if groundedness or correctness drops >threshold
- Posts a summary comment on the PR

**Acceptance criteria:**
- [ ] Action runs on every push to main and on PRs
- [ ] Eval smoke run completes in <5 minutes
- [ ] Baseline scores stored as artifact and updated on green main
- [ ] Failure threshold is configurable
- [ ] At least one intentional regression demonstrated → build fails as expected
- [ ] PR summary comment includes scores + deltas
- [ ] Pushed to public repo

---

## 🎉 Project 9 — Capstone: AI Engineering Knowledge Assistant (W45-48) · [[p9-capstone]]

**Goal:** One polished, deployed, evaluated product that combines everything.

**Pick a domain you care about:**
- Engineering notes / architecture docs / RFCs
- API docs / onboarding docs
- Personal learning vault
- Product documentation

**Minimum features:**

**Backend (Python + FastAPI):**
- Document upload + ingestion pipeline
- Chunking + embedding pipeline
- Vector search + RAG generation
- Source citations
- Eval harness integration (depend on P5 package or vendored copy)
- Structured logging
- Cost + latency tracking per query
- Failure log

**Frontend (React or Next.js — your edge):**
- Document upload UI
- Chat / search interface with streaming
- Source citation viewer (clickable, shows chunks)
- Evaluation dashboard (golden set status, recent scores, trends)
- Cost meter

**Quality:**
- Golden dataset committed to repo
- Retrieval relevance + groundedness + answer correctness metrics
- CI eval pipeline gates deploys
- Deployed publicly (Render / Fly.io / Vercel / Railway)
- Monitoring set up (basic)

> **Repo:** `aieng-p09-capstone` — monorepo with `backend/` + `frontend/` folders.

**Stretch features (pick 1-2):**
- Reranking
- Query expansion
- Hybrid search
- Metadata filters
- Simple agentic step
- Automated nightly eval run

**Acceptance criteria:**
- [ ] Deployed to public URL
- [ ] Backend + frontend in one repo (monorepo or separate)
- [ ] CI pipeline runs evals + unit tests on every push
- [ ] Golden set has ≥30 questions
- [ ] Eval dashboard live and accurate
- [ ] Cost tracking visible
- [ ] README tells the story: problem → architecture → tradeoffs → numbers
- [ ] At least one user (you, a friend, a colleague) actually uses it
- [ ] Demo video (3-5 min) recorded
- [ ] Blog post or LinkedIn post written about the journey

**This is the artifact you put on your resume.**

---

## 🔗 Live repos

> Replace `<your-username>` with your GitHub username. Add links as you create each repo.
> **Create repos as you reach each project, not all upfront.** Empty repos look worse than no repos.

| # | Repo | Status |
|---|------|--------|
| 1 | [`aieng-p01-json-extractor`](https://github.com/<your-username>/aieng-p01-json-extractor) | ⬜ |
| 2 | [`aieng-p02-semantic-search`](https://github.com/<your-username>/aieng-p02-semantic-search) | ⬜ |
| 3 | [`aieng-p03-rag-v1`](https://github.com/<your-username>/aieng-p03-rag-v1) | ⬜ |
| 4 | [`aieng-p04-rag-v2-evaluated`](https://github.com/<your-username>/aieng-p04-rag-v2-evaluated) | ⬜ |
| 5 | [`aieng-p05-eval-harness`](https://github.com/<your-username>/aieng-p05-eval-harness) | ⬜ |
| 6 | [`aieng-p06-finetuning-memo`](https://github.com/<your-username>/aieng-p06-finetuning-memo) | ⬜ |
| 7 | [`aieng-p07-research-agent`](https://github.com/<your-username>/aieng-p07-research-agent) | ⬜ |
| 8 | [`aieng-p08-ci-eval-pipeline`](https://github.com/<your-username>/aieng-p08-ci-eval-pipeline) | ⬜ |
| 9 | [`aieng-p09-capstone`](https://github.com/<your-username>/aieng-p09-capstone) | ⬜ |

---

## 🧭 Rules of engagement

1. **No project starts before its prerequisites.** Don't skip ahead.
2. **No project is "done" without acceptance criteria checked.** Be ruthless.
3. **Every project gets a README.** If you can't explain it, you don't own it.
4. **Public repos by default.** Build in public. Future-you needs the receipts.
5. **Tests where it matters.** Unit test the deterministic bits (chunking, parsing). Eval the non-deterministic bits (retrieval, generation).
6. **Commit often. Tag releases.** v0.1, v0.2, v1.0 for each project.

---

*Back to [[../README]] · [[../02-progress-tracker]]*
