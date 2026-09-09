---
type: study-path-timeline
parent: "[[README]]"
total_weeks: 52
study_weeks: 46
buffer_weeks: 6
hours_per_week: 3-4
hours_target: 161
start_date: 2026-06-01
resumed: 2026-08-03
target_end: 2027-07-18
created: 2026-05-29
updated: 2026-07-25
tags:
  - study
  - ai-engineering
  - timeline
---

# Course Path & Timeline

> ⛔ **SUPERSEDED for dates and status — see [[PROGRESS]].**
> This file's week→content mapping contradicted `weeks/week-NN.md` by up to 2 weeks (it had P3 shipping
> at W23, the week files say W25). The week files won. Dates here are stale as of 2026-09-07.
> Kept for history. **Do not plan from this file.**


> The 16 courses, the 9 projects, and the 52-week schedule at 3-4h/week.
> 46 study weeks + 6 buffer weeks. Source path: [[../deeplearning_ai_engineering_path]]
>
> ⚠️ **Re-planned 2026-07-25.** Paused Jul 6 – Aug 2 (health + work). Resumed W6 on Aug 3, everything slipped ~4 weeks. Added 2 travel buffers (Aug 17-26, Sep 25-Oct 4). New end date: Jul 18, 2027. **[[02-progress-tracker]] is the source of truth for dates.**

---

## ⏱️ Time budget (honest)

**Target:** **3-4 hours/week** (avg 3.5h × 46 study weeks = ~161h total)

```
1.5h  — Course videos + labs
1.5h  — Hands-on coding / project work
0.3h  — Concept notes
0.2h  — Weekly retro + journal
```

**Reality:** Busy office + kid. Some weeks will be 2h. Some 5h. Average over time.

**Rules:**
- If a week busts the budget, push course to next week. **Project is non-negotiable per phase.**
- Miss a week → slip the schedule, don't double up. Streak protection beats heroic catchup.
- 1 hour > 0 hours. Show up, even small.
- Buffer weeks are for catch-up or concept review — not zero work.

**Cost budget:** ~$5-10/month. Ollama for dev, paid APIs (gpt-4o-mini) for evals only. See [[00-context-and-goal#Model strategy]].

---

## 📚 The 16 courses

| #   | Course                                                                                                                                                            | Provider                   | Phase            | Weeks  | Repo |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- | ---------------- | ------ | ---- |
| 1   | [Generative AI with Large Language Models](https://www.coursera.org/learn/generative-ai-with-llms)                                                                | DLAI + AWS (Coursera)      | 0. Foundation    | W1-4   | —    |
| 2   | [ChatGPT Prompt Engineering for Developers](https://learn.deeplearning.ai/courses/chatgpt-prompt-eng/lesson/dfbds/introduction)                                   | DLAI                       | 1. App Basics    | W6-7   | —    |
| 3   | [Building Systems with the ChatGPT API](https://learn.deeplearning.ai/courses/chatgpt-building-system/lesson/k0pk1/introduction)                                  | DLAI                       | 1. App Basics    | W8-9   | —    |
| 4   | [Vector Databases: from Embeddings to Applications](https://learn.deeplearning.ai/courses/vector-databases-embeddings-applications/lesson/g6d1d/vector-databases) | DLAI + Weaviate            | 2. Embeddings    | W11-12 | —    |
| 5   | [Building Applications with Vector Databases](https://learn.deeplearning.ai/courses/building-applications-vector-databases/lesson/tl7on/introduction)             | DLAI + Pinecone            | 2. Embeddings    | W13-14 | —    |
| 6   | [Retrieval Augmented Generation (RAG)](https://www.coursera.org/learn/retrieval-augmented-generation-rag)                                                         | DLAI (Coursera)            | 3. Core RAG      | W16-22 | —    |
| 7   | [Advanced Retrieval for AI with Chroma](https://learn.deeplearning.ai/courses/advanced-retrieval-for-ai/lesson/kb5oj/introduction)                                | DLAI + Chroma              | 4. Adv Retrieval | W24-25 | —    |
| 8   | [Building and Evaluating Advanced RAG](https://learn.deeplearning.ai/courses/building-evaluating-advanced-rag/lesson/nwy74/introduction)                          | DLAI + LlamaIndex + TruEra | 4. Adv Retrieval | W26-27 | —    |
| 9   | [Improving Accuracy of LLM Applications](https://learn.deeplearning.ai/courses/improving-accuracy-of-llm-applications/lesson/zd29x/introduction)                  | DLAI + Lamini              | 5. Accuracy      | W30-31 | —    |
| 10  | [Evaluating and Debugging Generative AI](https://learn.deeplearning.ai/courses/evaluating-debugging-generative-ai/lesson/t7eoa/introduction)                      | DLAI + W&B                 | 5. Accuracy      | W32    | —    |
| 11  | [Finetuning Large Language Models](https://learn.deeplearning.ai/courses/finetuning-large-language-models/information)                                            | DLAI + Lamini              | 6. Fine-tuning   | W34-35 | —    |
| 12  | [Fine-tuning & RL for LLMs: Intro to Post-training](https://www.deeplearning.ai/courses/fine-tuning-and-reinforcement-learning-for-llms-intro-to-post-training/)  | DLAI                       | 6. Fine-tuning   | W36    | —    |
| 13  | [Agentic AI](https://learn.deeplearning.ai/courses/agentic-ai/lesson/pu5xbv/welcome)                                                                              | DLAI                       | 7. Agents        | W38-39 | —    |
| 14  | [Evaluating AI Agents](https://learn.deeplearning.ai/courses/evaluating-ai-agents/lesson/sqkza/introduction)                                                      | DLAI + Arize               | 7. Agents        | W40-41 | —    |
| 15  | [LLMOps](https://learn.deeplearning.ai/courses/llmops/lesson/jupuw/introduction)                                                                                  | DLAI + Google Cloud        | 8. Production    | W43-44 | —    |
| 16  | [Automated Testing for LLMOps](https://learn.deeplearning.ai/courses/automated-testing-llmops/lesson/oy7qu/introduction)                                          | DLAI + CircleCI            | 8. Production    | W45    | —    |

---

## 🏗️ The 9 projects — separate repos

> **Strategy:** Each project = its own GitHub repo. Clean portfolio. Hireable artifacts.
>
> Naming convention: `aieng-pNN-<short-name>` (e.g., `aieng-p01-json-extractor`, `aieng-p09-capstone`).

| # | Project | Phase | Done by | Suggested Repo Name |
|---|---------|-------|---------|---------------------|
| 1 | LLM JSON Extractor / Classifier (CLI) | 1 | W10 (Sep 16) | `aieng-p01-json-extractor` |
| 2 | Semantic Search Engine over local docs | 2 | W15 (Nov 15) | `aieng-p02-semantic-search` |
| 3 | RAG v1 — citations + logging | 3 | W23 (Jan 10, 2027) | `aieng-p03-rag-v1` |
| 4 | RAG v2 — reranking + golden eval set | 4 | W28 (Feb 21) | `aieng-p04-rag-v2-evaluated` |
| 5 | Evaluation Harness — CI-runnable | 5 | W33 (Mar 28) | `aieng-p05-eval-harness` |
| 6 | Fine-tuning Decision Memo (+ optional narrow fine-tune) | 6 | W37 (Apr 25) | `aieng-p06-finetuning-memo` |
| 7 | Simple Research Agent w/ trajectory eval | 7 | W42 (Jun 6) | `aieng-p07-research-agent` |
| 8 | CI Eval Pipeline (regression gate) | 8 | W46 (Jul 4) | `aieng-p08-ci-eval-pipeline` |
| 9 | **Capstone** — AI Engineering Knowledge Assistant, deployed | 8 | W48 (Jul 18) | `aieng-p09-capstone` |

> P3 and P4 build on each other but live in different repos. Copy the v1 baseline into the v2 repo.
> P5 (eval harness) is reusable — wire it into P3, P4, and P9 as a dependency or vendored copy.

---

## 🗓️ Phase-by-phase schedule (52 weeks: 46 study + 6 buffer)

> 🔁 **Re-planned 2026-07-25.** Tables below now reflect the CURRENT schedule (post Jul-2026 pause: ~4-week slip + 2 travel buffers). [[02-progress-tracker#🗓️ The 52 weeks|The tracker]] remains the day-to-day source of truth. Old→new milestone map for reference:
>
> | | Original | New |
> |---|---|---|
> | Resume point | W6 Jul 6 | **W6 Aug 3, 2026** |
> | P1 ship (W10) | Aug 9 | **Sep 16, 2026** |
> | P2 ship (W15) | Sep 27 | **Nov 15, 2026** |
> | P3 ship / RAG v1 (W23) | Nov 22 | **Jan 10, 2027** |
> | P4 ship (W28) | Jan 3 | **Feb 21, 2027** |
> | P5 ship (W33) | Feb 7 | **Mar 28, 2027** |
> | P6 ship (W37) | Mar 7 | **Apr 25, 2027** |
> | P7 ship (W42) | Apr 18 | **Jun 6, 2027** |
> | P8 ship (W46) | May 2 | **Jul 4, 2027** |
> | **Capstone (W48)** | May 30 | **Jul 18, 2027** |
> | New buffers | — | **Aug 17-26 (travel), Sep 25-Oct 4 (travel)** |

### Phase 0 — Foundation (W1-5)

**Goal:** LLM mental model first, then Python tooling. Theory → tools, not the other way around.

| Week | Dates | Course | Focus | Deliverable |
|------|-------|--------|-------|-------------|
| W1 | Jun 1-7, 2026 | C1 (1/4) | Intro, transformers high-level | Concept notes |
| W2 | Jun 8-14 | C1 (2/4) | Pretraining + instruction tuning | Concept notes |
| W3 | Jun 15-21 | C1 (3/4) | RLHF + evaluation | Concept notes |
| W4 | Jun 22-28 | C1 (4/4) | Deployment + 1-page synthesis | 1-page synthesis note |
| W5 | Jun 29 - Jul 5 | — (Python ramp) | uv, Pydantic, httpx, pytest, first API call, Ollama setup | Working dev environment + first LLM call |

**Phase exit criteria:** Can explain pretraining vs instruction-tuning vs RLHF vs fine-tuning vs RAG in plain English without notes. Python dev environment is friction-free. First API call made with understanding of *why* structured outputs matter.

---

### Phase 1 — LLM App Basics (W6-10)

**Goal:** Treat the LLM as a software interface. Ship a working CLI app.

| Week | Dates          | Course       | Focus                                   | Deliverable      |
| ---- | -------------- | ------------ | --------------------------------------- | ---------------- |
| W6   | Aug 3-9        | C2 (1/2)     | Instruction clarity, structured outputs | Notes            |
| W7   | Aug 10-16      | C2 (2/2)     | Few-shot, summarization, classification | Prompt library   |
| ✈️ BT1 | Aug 17-26    | —            | 🧳 Aug travel buffer                     | Rest (0h)        |
| W8   | Aug 27 - Sep 2 | C3 (1/2)     | Chaining, breakdowns                    | P1 scaffold      |
| W9   | Sep 3-9        | C3 (2/2)     | Output checking, moderation             | P1 main build    |
| W10  | Sep 10-16      | (build week) | Polish + tests                          | ✅ **P1 shipped** |

**Phase exit criteria:** [[projects/p1-llm-json-extractor]] passes acceptance criteria. Repo public.

---

### 🔄 Buffer 1 — Sep 17-24

> Catch-up on Phase 0-1. Review prompt engineering concepts. Prep before the Sep travel buffer.

### ✈️ Travel Buffer 2 — Sep 25 - Oct 4

> 🧳 Sep travel. 0h expected. Rest is productive. Optionally skim C4 intro before Phase 2.

---

### Phase 2 — Embeddings & Semantic Search (W11-15)

**Goal:** Retrieval before generation. Understand why RAG quality lives or dies in retrieval.

| Week | Dates | Course | Focus | Deliverable |
|------|-------|--------|-------|-------------|
| W11 | Oct 5-11 | C4 (1/2) | Embeddings, similarity | Notes |
| W12 | Oct 12-18 | C4 (2/2) | ANN, sparse vs dense | Concept notes |

**🔄 Buffer 2 — Oct 19-25**

> Catch-up on embeddings. Review chunking concepts. If on track: explore embedding models in Ollama (`nomic-embed-text` vs `mxbai-embed-large`).

| Week | Dates | Course | Focus | Deliverable |
|------|-------|--------|-------|-------------|
| W13 | Oct 26 - Nov 1 | C5 (1/2) | Semantic search, hybrid | P2 scaffold |
| W14 | Nov 2-8 | C5 (2/2) | Recommenders, anomaly detection | P2 main build |
| W15 | Nov 9-15 | (build week) | Polish + README + 5-question retrieval eval | ✅ **P2 shipped** |

**Phase exit criteria:** [[projects/p2-semantic-search]] passes acceptance criteria. Semantic search returns relevant chunks on your own docs. **5-question retrieval eval with recall@5 score documented.**

---

### Phase 3 — Core RAG (W16-23) — 8 weeks

**Goal:** Build RAG v1 by hand. No LangChain. Citations + logging. Pick a tracing tool (Phoenix/Langfuse/Arize).

| Week | Dates | Course | Focus | Deliverable |
|------|-------|--------|-------|-------------|
| W16 | Nov 16-22 | C6 (1+2/9) | RAG architecture + document ingestion | Notes |
| W17 | Nov 23-29 | C6 (3/9) | Chunking strategies | Notes (chunking is critical — don't rush) |
| W18 | Nov 30 - Dec 6 | C6 (4/9) | Embedding strategies | P3 scaffold + tracing tool setup |
| W19 | Dec 7-13 | C6 (5+6/9) | Hybrid search + query parsing | P3 ingestion working |
| W20 | Dec 14-20 | C6 (7/9) | Prompt construction with context | P3 retrieval working |
| W21 | Dec 21-27 🎄 | C6 (8/9) — *light, holiday week (0-2h)* | RAG evaluation | P3 generation working |
| W22 | Dec 28 - Jan 3, 2027 | C6 (9/9) | Deployment concerns | P3 logging + citations |
| W23 | Jan 4-10 | (build week) | Polish + diagram + README | ✅ **P3 shipped (RAG v1)** |

**Phase exit criteria:** [[projects/p3-rag-v1]] passes acceptance criteria. Every query + retrieved chunks + answer logged. Tracing tool captures all requests.

---

### Phase 4 — Advanced Retrieval & RAG Quality (W24-28)

**Goal:** Make RAG good. Add reranking, query expansion. Build a golden set.

| Week | Dates | Course | Focus | Deliverable |
|------|-------|--------|-------|-------------|
| W24 | Jan 11-17 | C7 (1/2) | Query expansion, reranking | Notes |
| W25 | Jan 18-24 | C7 (2/2) | Cross-encoders, embedding adaptors | Add 2 improvements to RAG v1 |
| W26 | Jan 25-31 | C8 (1/2) | RAG triad metrics | Notes + golden set draft |
| W27 | Feb 1-7 | C8 (2/2) | Sentence-window, auto-merging | P4 build |

**🔄 Buffer 3 — Feb 8-14**

> Catch-up on Phase 4. Re-read RAG concept notes. Review + expand golden set draft. Re-run evals on RAG v1 if time.

| Week | Dates | Course | Focus | Deliverable |
|------|-------|--------|-------|-------------|
| W28 | Feb 15-21 | (build week) | Eval-driven iteration | ✅ **P4 shipped (RAG v2 + golden set)** |

**Phase exit criteria:** [[projects/p4-rag-v2-evaluated]] has 30+ golden questions. Baseline vs improved retrieval numbers in repo.

---

### Phase 5 — Accuracy & Debugging (W29-33)

**Goal:** Systematic evaluation. Tracing. Experiment tracking.

| Week | Dates | Course | Focus | Deliverable |
|------|-------|--------|-------|-------------|
| W29 | Feb 22-28 | — | Ramp-back | Light review of Phase 4 + plan P5 |
| W30 | Mar 1-7 | C9 (1/2) | Creating evals, accuracy measurement | Notes |
| W31 | Mar 8-14 | C9 (2/2) | Prompt iteration, memory tuning | Iteration log |
| W32 | Mar 15-21 | C10 (1/1) | Tracing, experiment tracking | Notes + P5 scaffold |
| W33 | Mar 22-28 | (build week) | Debugging workflows, versioning | ✅ **P5 shipped (eval harness)** |

**Phase exit criteria:** [[projects/p5-eval-harness]] runs golden set in one command and produces scores.

---

### Phase 6 — Fine-tuning & Post-training (W34-37)

**Goal:** Understand fine-tuning so you can choose NOT to do it. Decision memo > experiment.

| Week | Dates | Course | Focus | Deliverable |
|------|-------|--------|-------|-------------|
| W34 | Mar 29 - Apr 4 | C11 (1/2) | When to fine-tune, instruction FT | Notes |
| W35 | Apr 5-11 | C11 (2/2) | Data prep, training, evaluation | Notes |
| W36 | Apr 12-18 | C12 (1/1) | RL intuition, LoRA, post-training | Notes |
| W37 | Apr 19-25 | (write week) | Memo draft + (optional) tiny FT experiment on local 7B via QLoRA | ✅ **P6 shipped (decision memo)** |

**Phase exit criteria:** [[projects/p6-finetuning-memo]] answers all 8 sections. Recommendation is go/no-go.

---

### Phase 7 — Agents (W38-42)

**Goal:** Concept-first agents. Evaluation > multi-agent hype.

| Week | Dates | Course | Focus | Deliverable |
|------|-------|--------|-------|-------------|
| W38 | Apr 26 - May 2 | C13 (1/2) | Task decomposition, reflection | Notes |
| W39 | May 3-9 | C13 (2/2) | Tool use, agentic patterns | P7 scaffold |
| W40 | May 10-16 | C14 (1/2) | Decomposition, tracing | P7 plan loop |

**🔄 Buffer 4 — May 17-23 (reset before capstone)**

> Mental reset before capstone push. Catch up on P7 if behind. If on track: sketch capstone architecture.

| Week | Dates | Course | Focus | Deliverable |
|------|-------|--------|-------|-------------|
| W41 | May 24-30 | C14 (2/2) | Trajectories, LLM-as-judge | P7 tool integration |
| W42 | May 31 - Jun 6 | (build week) | Trajectory eval + polish | ✅ **P7 shipped (research agent)** |

**Phase exit criteria:** [[projects/p7-research-agent]] handles 10 queries reliably. Trajectory eval scores each run.

---

### Phase 8 — Production & Capstone (W43-48)

**Goal:** Operationalize. Deploy. Gate on evals. Polish the FE.

| Week | Dates | Course | Focus | Deliverable |
|------|-------|--------|-------|-------------|
| W43 | Jun 7-13 | C15 (1/2) | Data prep, orchestration | Notes |
| W44 | Jun 14-20 | C15 (2/2) | Deployment workflow, prompt safety | Capstone scaffold (start early!) |
| W45 | Jun 21-27 | C16 (1/1) | CI for LLM apps, model-graded evals | P8 scaffold |
| W46 | Jun 28 - Jul 4 | (build week) | Test design + CI integration | ✅ **P8 shipped (CI eval pipeline)** |
| W47 | Jul 5-11 | (capstone) | Capstone polish + deploy | — |
| W48 | Jul 12-18 | (capstone) | Capstone deploy + demo video | 🎉 **P9 Capstone live** |

**Phase exit criteria:** [[projects/p9-capstone]] is deployed publicly. CI runs on every push. Eval regression breaks the build. Demo video recorded.

> **Note:** Capstone reuses P3 RAG backend as baseline. Don't rewrite — extend.
> Start capstone scaffold in W44, not W47. The FE (your edge) needs runway.

---

## 📊 Phase summary

| Phase | Weeks | Courses | Projects | Hours (est) | Theme |
|-------|-------|---------|----------|-------------|-------|
| 0 — Foundation | 5 | 1 | 0 | ~18h | Python ramp + mental model |
| 1 — App Basics | 5 | 2 | 1 | ~18h | LLM as interface |
| ✈️ Travel Buffer 1 | 1 | — | — | 0h | Aug trip |
| Buffer 1 | 1 | — | — | ~2h | Catch-up |
| ✈️ Travel Buffer 2 | 1 | — | — | 0h | Sep trip |
| 2 — Embeddings | 5 | 2 | 1 | ~18h | Retrieval first |
| Buffer 2 | 1 | — | — | ~2h | Catch-up |
| 3 — Core RAG | 8 | 1 (big) | 1 | ~28h | Build RAG manually |
| 4 — Adv Retrieval | 5 | 2 | 1 | ~18h | Make RAG good |
| Buffer 3 | 1 | — | — | ~1h | Catch-up |
| 5 — Accuracy | 5 | 2 | 1 | ~18h | Evals as engineering |
| 6 — Fine-tuning | 4 | 2 | 1 | ~14h | Decide, don't default |
| 7 — Agents | 5 | 2 | 1 | ~18h | One reliable agent |
| Buffer 4 | 1 | — | — | ~2h | Reset before capstone |
| 8 — Production | 5 | 2 | 2 | ~18h | Deploy + capstone |
| **Total** | **52** | **16** | **9** | **~175h** | — |

---

## 🔄 Buffer weeks — rules

The 6 buffer weeks (post re-plan) are placed around travel, holidays, and phase transitions:

| Buffer | Dates | Location | Purpose |
|--------|-------|----------|---------|
| ✈️ BT1 | Aug 17-26, 2026 | Mid Phase 1 | 🧳 Aug travel. 0h expected. |
| B1 | Sep 17-24 | After Phase 1 | Catch-up on P1, review prompting |
| ✈️ BT2 | Sep 25 - Oct 4 | Before Phase 2 | 🧳 Sep travel. 0h expected. |
| B2 | Oct 19-25 | Mid Phase 2 | Catch-up on embeddings |
| B3 | Feb 8-14, 2027 | After Phase 4 | Catch-up / re-read RAG notes / review golden set |
| B4 | May 17-23 | Before capstone | Mental reset, sketch capstone |

> Note: The real Christmas week (Dec 21-27) now lands on **W21** (a study week) — treat it as light (0-1h), don't force it.

**Rules for buffer weeks:**
- ✅ Review concept notes you're unsure about
- ✅ Catch up on missed course material
- ✅ Re-run evals on previous projects
- ✅ Sketch architecture for upcoming project
- ❌ Don't start new course material
- ❌ Don't try to "get ahead" — rest is productive

---

## 🚫 Explicitly skipped (until after this path)

- LangChain / LangGraph / CrewAI / AutoGen courses
- LlamaIndex agentic RAG course (use LlamaIndex through Course 8 only)
- Multimodal / image generation courses
- Pretraining from scratch
- Knowledge Graphs for RAG (optional add-on later)

---

## ✅ Optional add-ons (post-path)

Take these only after capstone is live:

- Knowledge Graphs for RAG
- Agentic Knowledge Graph Construction
- Pydantic for LLM Workflows
- How Transformer LLMs Work (visual)

---

*Back to [[README]] · Open [[02-progress-tracker]] to start*
