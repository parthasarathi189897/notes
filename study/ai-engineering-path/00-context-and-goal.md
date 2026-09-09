---
type: study-path-context
parent: "[[README]]"
created: 2026-05-29
updated: 2026-05-29
tags:
  - study
  - ai-engineering
  - goals
---

# Context & Goal

> The "why" file. Read this on low-motivation days.

---

## 🎯 Goal

**Become a strong practical AI engineer.**

Not a researcher. Not a prompt-tinkerer. An engineer who can:

- Take a vague business problem and ship a working LLM-powered system
- Decide between prompting, RAG, and fine-tuning with evidence
- Build evaluation harnesses that catch regressions before users do
- Deploy, monitor, and iterate on AI systems in production
- Hold their own in an AI engineering interview at any tier

---

## 👤 Where I'm starting from

- **15 years of frontend engineering.** Strong on shipping, UI, product thinking.
- **Python:** Working knowledge. Not my native language. Week 5 is a dedicated Python/uv/Pydantic ramp — after C1 gives context for *why* you need these tools.
- **ML/AI background:** Light. Have used LLM APIs. Have not built RAG or evals from scratch.
- **Backend/API:** Comfortable enough — FastAPI will be the bottleneck, not the blocker.

---

## ⚡ My unfair advantage

15 years of FE means I can build the **interface to my AI systems** better than most.
Most AI engineers ship Jupyter notebooks. I will ship products.

The capstone will lean into this — polished UI, real eval dashboards, citation viewers, observability that's actually pleasant to look at. **This is my edge. Don't waste it.**

---

## 🧠 Learning style (honest constraints)

- ❌ Get bored by long theory lectures and 40-hour Coursera marathons
- ✅ Engaged by short, hands-on, project-driven work
- ✅ Learn fastest when shipping something at the end of each phase
- ❌ Will drop a course if I can't see why it matters
- ✅ Need visible progress and small wins to stay motivated

**Implication:** Use DeepLearning.AI short courses as primary. Skip lecture-heavy passes. Every phase ends with a build.

## ⏰ Life constraints (real)

- **3-4 hours/week is realistic.** Busy office hours + kid. Some weeks will be 2h, some 5h. Average over 48 weeks.
- **Path runs Jun 1, 2026 → Aug 22, 2027** after the Sep-2026 rebase. 48 study weeks + 4 buffers + 4 holiday blocks. See [[PROGRESS]] for live dates.
- **No heroic catchup.** Miss a week → slip the schedule by 1 week and move on.
- **Saturday morning is sacred study time.** Kid-nap windows are gold. Block them.
- **One alive thing > five dead things.** Quality > quantity over the year.

---

## 🛠️ Ground rules

1. **Build after every phase.** No phase is "done" without a project artifact in a repo.
2. **Avoid framework lock-in early.** Build RAG manually before touching LangChain/LlamaIndex.
3. **Evals are core engineering.** Every feature needs: what should happen, what can go wrong, how I measure it, how I prevent regression. Start eval thinking from P2, not P4.
4. **Fine-tune late.** Try better prompts → retrieval → chunking → metadata → reranking → eval data → *then* fine-tuning.
5. **One capstone alive.** Don't ship 20 disconnected notebooks. Keep evolving one serious app.
6. **Cost-aware from day 1.** Track $/query and tokens/query. Real engineers know their numbers.
7. **Write the journal.** One paragraph per week in the week note. Future me + interview material.
8. **Miss a week → slip, don't double up.** Streak protection beats heroic catchup.
9. **Ollama for dev, paid APIs for evals.** Use local models (`llama3.1:8b`, `nomic-embed-text`) for daily development. Only use paid APIs (gpt-4o-mini, Claude Haiku) for eval runs and LLM-as-judge.
10. **Budget cap: $10/month on API costs.** Track in weekly notes. If a month busts the budget, switch more work to Ollama.
11. **Pick one tracing tool from P3 onward.** Use Phoenix, Langfuse, or Arize free tier from the first RAG project. One tool, five projects.

---

## ✅ Definition of done

I am done when I can confidently **build, explain, and demonstrate**:

| # | Capability |
|---|-----------|
| 1 | Build a RAG pipeline from scratch in a weekend without referencing course code |
| 2 | Debug a RAG app returning wrong answers and fix it in under 2 hours |
| 3 | Explain when to choose prompting vs RAG vs fine-tuning with concrete tradeoffs |
| 4 | Design an eval harness for a new LLM feature with golden set, metrics, CI gate |
| 5 | Estimate cost and latency for an LLM system before building it |
| 6 | Evaluate an agent's trajectory and identify where it fails |
| 7 | Deploy a small AI system with monitoring, regressions caught, and rollback plan |
| 8 | Walk into an AI engineering interview and answer architecture questions credibly |

**Final proof:** the capstone app is live, instrumented, eval-gated, and would pass a senior engineer's code review.

---

## 🚫 What I will NOT do

- Spend weeks memorizing transformer math
- Pretrain a model from scratch
- Hoard 30 half-finished projects
- Chase every new agent framework
- Use "I'll just watch one more course" as procrastination
- Skip evals "for now" — that's how demos become production fires

---

## 💸 Resources I have

- **Coursera subscription** (company-provided) → use it
- **DeepLearning.AI direct courses** (mostly free) → use them
- **15 years of context** on shipping software → trust the instinct
- **Wibey CLI + Claude** → use as pair programmer, not as crutch
- **Ollama** → free local LLMs for dev loops (llama3.1:8b, mistral:7b, nomic-embed-text)
- **Budget: ~$5-10/month** → gpt-4o-mini for evals + LLM-as-judge only

## 🖥️ Model strategy (cost-aware)

| Use case | Model | Cost |
|----------|-------|------|
| Prompt iteration / dev loop | Ollama `llama3.1:8b` | Free |
| Embeddings (P2-P9) | Ollama `nomic-embed-text` | Free |
| RAG generation dev | Ollama `llama3.1:8b` | Free |
| LLM-as-judge evals (P4+) | `gpt-4o-mini` | ~$0.15/1M tokens |
| Reranking (P4) | Cohere free tier or `gpt-4o-mini` | Free / cheap |
| Fine-tuning experiments (P6) | QLoRA on local 7B | Free |
| Capstone production | `gpt-4o-mini` or Claude Haiku | ~$5-8/mo |
| DLAI course labs | Lab-provided API keys | Free |

**Rule:** Develop against Ollama. Run eval suite against target production model once per phase. Catch drift early.

**Hardware req:** 16GB+ RAM for 7B models. M-series Mac handles this well.

---

## 🔄 When motivation drops (read this)

You picked this path because:

1. AI is reshaping software engineering and you don't want to be left behind
2. Your FE skills + AI skills = a rare and valuable combination
3. You want to ship products that didn't exist 2 years ago
4. The interview market favors engineers who can prove they ship AI systems
5. **You are bored of just frontend.** This is the door.

The path is long. **The compound effect is the point.** Week 8 you in won't look like Week 1 you. Just show up.

---

*Back to [[README]]*
