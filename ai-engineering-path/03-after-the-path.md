---
type: study-path-next
parent: "[[README]]"
status: future
created: 2026-05-29
updated: 2026-05-29
tags:
  - study
  - ai-engineering
  - next-steps
---

# 🚀 After the Path — What to Target Next

> Read this **after Week 48 (May 2, 2027)** — capstone deployed, 9 repos shipped.
> Don't read it now to plan ahead. Read it then to plan forward.
>
> The capstone is the floor, not the ceiling.

---

## 🧭 First decision — pick ONE track

You've built breadth. Now pick depth. **Don't try all four.**

| Track | Best if you want to... | Time horizon |
|-------|------------------------|--------------|
| **A. Applied AI Engineer (Product)** | Ship customer-facing AI features at scale | 3-6 months |
| **B. AI Platform Engineer (Infra)** | Build the infra other engineers use to ship AI | 6-9 months |
| **C. AI Research Engineer** | Bridge research → production; touch fine-tuning seriously | 9-12 months |
| **D. AI Founder / Indie** | Ship a product, charge money, build a brand | Open-ended |

Pick based on what energized you most during the path. Notes to read first: revisit your `weeks/week-*` journal entries and look for the wins that lit you up.

---

## 📚 Optional DLAI add-ons (small, focused)

These were on your skip-list during the path. Pick them up as needed:

### 1. Knowledge Graphs for RAG

**Link:** https://learn.deeplearning.ai/courses/knowledge-graphs-rag/lesson/c498d/knowledge-graph-fundamentals

**Take if:** Capstone or next project has documents with rich entity-relationship structure (orgs, products, people, hierarchies) where pure vector search underperforms.

**Build:** Hybrid retrieval (graph + vector) over a real domain. Compare to RAG v2 baseline.

---

### 2. Agentic Knowledge Graph Construction

**Link:** https://learn.deeplearning.ai/courses/agentic-knowledge-graph-construction/lesson/8860g/what-is-a-knowledge-graph

**Take if:** You want to extract structured KGs from messy unstructured documents (legal, medical, internal docs).

**Build:** A pipeline that takes 100 messy PDFs → produces a queryable KG. Eval against hand-labeled ground truth.

---

### 3. Pydantic for LLM Workflows

**Link:** https://learn.deeplearning.ai/courses/pydantic-for-llm-workflows/lesson/ov2no/pydantic-model-basics

**Take if:** Your post-capstone work involves complex structured outputs (multi-step extraction, nested schemas, function calling).

**Build:** Refactor P1 or P3 to use Instructor or Pydantic AI. Document tradeoffs.

---

### 4. How Transformer LLMs Work

**Link:** https://learn.deeplearning.ai/courses/how-transformer-llms-work/lesson/hrpcy/understanding-language-models%3A-transformers

**Take if:** You want a visual, intuitive transformer mental model without reading the original papers. Useful for interviews and credibility.

**Pair with:** Andrej Karpathy's "Let's build GPT" YouTube series.

---

## 🛤️ Track A — Applied AI Engineer (Product focus)

Ship features. Own the user-facing AI layer at a company or consultancy.

### Skills to deepen
- Streaming UX (SSE, WebSocket, token streaming patterns)
- Prompt versioning + A/B testing in production
- Safety / moderation / jailbreak resistance
- Tool calling + structured output reliability at scale
- Cost optimization (caching, prompt compression, smaller models for hot paths)

### Build (post-capstone projects)
- [ ] **P10 — Multi-tenant RAG SaaS:** auth, per-org isolation, billing meter
- [ ] **P11 — Production prompt versioning:** A/B test 2 prompts, log outcomes, pick winner
- [ ] **P12 — Streaming UX deep-dive:** rebuild capstone chat with token streaming + cancel + retry

### Resources
- "Designing ML Systems" by Chip Huyen (book — you already started)
- Hamel Husain's blog on evals + AI engineering
- Eugene Yan's writing on building w/ LLMs

### Interview prep
- System design for AI features (mock with peers)
- Build "what would you do differently in capstone" 1-pager
- Practice explaining cost/latency tradeoffs to non-technical PMs

---

## 🛤️ Track B — AI Platform Engineer (Infra focus)

Build the platform that other AI engineers ship on top of.

### Skills to deepen
- Vector DB internals (HNSW, IVF, quantization)
- LLM gateway / router (OpenRouter, Portkey, LiteLLM internals)
- Observability for LLM apps (Langfuse, Helicone, Arize, custom)
- GPU economics, quantization (GGUF, AWQ, GPTQ), inference servers (vLLM, TGI)
- Embedding model selection + benchmarking

### Build
- [ ] **P10 — Self-hosted LLM gateway:** routing, retries, rate limits, cost tracking, fallback chains
- [ ] **P11 — Eval-as-a-Service platform:** generalize P5 into a hosted product for teams
- [ ] **P12 — Embedding benchmark suite:** compare 5 embedding models on YOUR domain data

### Resources
- vLLM docs + papers
- "AI Engineering" by Chip Huyen (ch 9-10 deeply)
- BAML, DSPy — programming model abstractions over LLMs
- The Latent Space podcast (Swyx interviews infra builders)

### Interview prep
- System design for AI platforms (mock with senior infra engineers)
- Contribute to one open-source AI infra project (LiteLLM, Langfuse, vLLM)

---

## 🛤️ Track C — AI Research Engineer

Bridge research → production. Read papers. Fine-tune seriously. Influence model choice.

### Skills to deepen
- Reading + replicating papers (start with NeurIPS / ICLR / ACL "best paper" winners in your domain)
- PyTorch fluency
- HuggingFace ecosystem (transformers, accelerate, peft, trl)
- Distributed training basics (DDP, FSDP)
- Synthetic data generation + distillation

### Build
- [ ] **P10 — Replicate a paper:** pick one recent paper, replicate the headline result on a small scale
- [ ] **P11 — Domain-adapted small model:** fine-tune a 1-3B model for a specific task, beat a 70B model on YOUR eval set
- [ ] **P12 — Synthetic data pipeline:** generate + filter + train, end-to-end

### Resources
- Karpathy's "nanoGPT" + "Let's reproduce GPT-2" video series
- HuggingFace courses (free)
- "Build a Large Language Model (From Scratch)" by Sebastian Raschka
- Papers With Code (replicate weekly)
- Latent Space + Interconnects (Nathan Lambert) for post-training news

### Interview prep
- Be able to explain attention, RLHF, DPO, LoRA at a deep level
- Code interview: implement attention from scratch
- Reading group: replicate 1 paper per quarter

---

## 🛤️ Track D — AI Founder / Indie

Ship a product. Charge money. Build a brand.

### Skills to deepen
- Distribution > tech (writing, building in public)
- Pricing for AI products (cost-aware design becomes existential)
- Founder economics (LLM API costs as % of revenue)
- Marketing through the capstone (blog, video, X)

### Build
- [ ] **P10 — Productize the capstone:** add auth, billing (Stripe), landing page
- [ ] **P11 — Distribution:** 10 blog posts, 50 X threads, 5 YouTube videos in 6 months
- [ ] **P12 — First paying user:** charge $10/mo for capstone. One user > zero.

### Resources
- "The Mom Test" by Rob Fitzpatrick (customer interviews)
- IndieHackers (community)
- Pieter Levels' writing
- Mintlify / Posthog blog (for AI product GTM)

### Interview prep
- N/A — you ARE the interview
- But: track MRR, churn, CAC, retention from day 1

---

## 🎯 Cross-track must-do (regardless of track)

These pay off no matter which track you pick:

### 1. Publish 3-5 long-form posts about the journey
- "Building RAG from scratch in 2026: what I learned"
- "Why I didn't fine-tune (and when you shouldn't either)"
- "Evals as engineering: a 48-week journey from FE to AI engineer"
- "The 9 projects that taught me AI engineering"
- "Capstone teardown: architecture, costs, mistakes"

### 2. Speak publicly at least once
- Local meetup, internal tech talk, podcast guest
- Topic: a specific lesson from the path (not "I learned AI")

### 3. Contribute to one major OSS project
- LangChain, LlamaIndex, vLLM, Langfuse, Instructor — pick what aligns with your track
- Goal: 3+ merged PRs

### 4. Mentor someone
- Find a junior engineer / FE engineer starting their AI path
- Share your weekly notes, project repos, journal
- Teaching forces clarity

### 5. Audit your golden set quarterly
- The capstone golden set should grow over time
- Re-baseline metrics every quarter
- Track drift in your own AI app

---

## 📖 Books (post-path reading order)

> Don't start before W48. They distract from the build.

| Order | Book | Why |
|-------|------|-----|
| 1 | "AI Engineering" — Chip Huyen | You're already reading it slowly; finish properly post-path |
| 2 | "Designing ML Systems" — Chip Huyen | Production ML systems context |
| 3 | Track-specific (see above) | Depth |

---

## 🎤 Interview targeting (if job-seeking)

After capstone, you can target:

| Role | Realistic target | Stretch |
|------|------------------|---------|
| Senior AI Engineer | ✅ With portfolio | — |
| Staff AI Engineer | Stretch, with strong system design | ✅ With 1-2 years applied work |
| AI Engineering Lead | With current FE seniority + capstone | ✅ |
| AI Research Engineer | Stretch, depends on Track C work | Requires Track C deep-dive |
| AI Founder | Anytime, no permission needed | — |

### Interview prep checklist
- [ ] 30-min capstone walkthrough rehearsed
- [ ] 3 "tell me about a time you debugged a hard AI problem" stories (mine from journal)
- [ ] Whiteboard-able: RAG architecture, eval design, fine-tune decision flow
- [ ] Cost estimation drill: estimate $/user/month for a hypothetical AI feature
- [ ] One opinion you'll defend strongly (e.g., "fine-tuning is overrated for most teams")

---

## 🚫 What NOT to do post-path

- ❌ Start 5 new projects simultaneously. **Pick one track, ship one thing.**
- ❌ Chase every new model release. **Your skills compound; model churn doesn't.**
- ❌ Abandon the capstone. **Keep it alive — it's your living portfolio.**
- ❌ Take a 3-month break. **Streak protection still matters.** Drop to 1-2h/week, but don't go dark.
- ❌ Compare yourself to people who started 5 years ago. **Compare to W1 you.**

---

## 🧘 Sustainable cadence post-path

The 48-week sprint earned you the right to slow down. New cadence:

```
2h/week sustained — capstone maintenance + 1 deep-dive area
1 blog post per month
1 OSS contribution per quarter
1 conference talk per year
```

This is forever. The path was the foundation. The career is the building.

---

## 🎬 Definition of "successful next step" (12 months post-path)

By **May 2, 2028** you should have:

- [ ] Picked a track and shipped 2-3 track-specific projects
- [ ] Published 5+ long-form posts about your work
- [ ] Spoken publicly at least once
- [ ] Either: moved into an AI engineering role, OR: shipped a product earning real money
- [ ] Capstone still alive, still evaluated, still deployed
- [ ] Mentored at least one other engineer through AI fundamentals

If 4/6 of those are true → you successfully transitioned. The path worked.

---

## 🔄 When you read this (May 2027) — reflection prompts

Before picking a track, sit with these for an hour:

```
1. Which of the 9 projects did I most enjoy building?
2. Which weekly journal entries had the highest confidence score?
3. What did I find myself reading / watching in my spare time?
4. If I never had to do FE work again, would I be relieved or sad?
5. What's the smallest AI product I could imagine charging $20/mo for?
6. Who do I admire in AI right now — and which track are they on?
```

The answers point at your track.

---

*Back to [[README]] · [[02-progress-tracker]] · [[projects/README]]*
