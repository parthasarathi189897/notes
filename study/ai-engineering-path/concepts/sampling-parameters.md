---
type: concept-note
topic: Sampling Parameters (Temperature, Top-p, Top-k)
phase: 0
week_learned: 1
confidence: H
related_courses:
  - "C1 GenAI w/ LLMs"
created: 2026-06-01
updated: 2026-06-01
tags:
  - study
  - ai-engineering
  - concept
  - inference
---

# Sampling Parameters — Temperature, Top-p, Top-k

> Phase 0, Week 1. Learned during Python ramp — first API call.

---

## One-sentence summary

Temperature, top-p, and top-k control **how "creative" vs "predictable"** the model's output is by shaping the probability distribution over next tokens.

---

## The three knobs

### Temperature (0.0 – 2.0)

- **Low (0.0-0.3):** Sharp distribution → model picks the most likely token almost every time. Good for: classification, extraction, structured output.
- **High (0.7-1.5):** Flatter distribution → model explores less likely tokens. Good for: creative writing, brainstorming.
- **0 is NOT deterministic.** It's *mostly* deterministic. Floating-point math + batching can still cause variation. Don't rely on `temperature=0` for exact reproducibility.

### Top-p (nucleus sampling, 0.0 – 1.0)

- Considers the smallest set of tokens whose cumulative probability ≥ p.
- `top_p=0.1` → only considers tokens in the top 10% of probability mass.
- Dynamic: adapts the number of candidates per step (unlike top-k which is fixed).

### Top-k

- Considers only the top k most probable tokens.
- `top_k=50` → always exactly 50 candidates, regardless of probability distribution.
- Less commonly exposed in commercial APIs (OpenAI doesn't expose it).

---

## Engineering rules of thumb

| Use case | Temperature | Top-p | Why |
|----------|-------------|-------|-----|
| JSON extraction | 0 | 1.0 | Predictable, structured |
| Classification | 0 | 1.0 | Want the most likely answer |
| RAG answers | 0.1-0.3 | 0.9 | Grounded but slightly flexible |
| Creative writing | 0.8-1.2 | 0.95 | Variety matters |
| Brainstorming | 1.0-1.5 | 1.0 | Explore the distribution |

**Don't set both temperature and top-p to extreme values.** OpenAI docs recommend adjusting one, not both.

---

## Gotcha I learned

Called the OpenAI API with `temperature=0` twice with the same prompt. Got different outputs. Researched: this is expected behavior. GPU floating-point operations are non-deterministic across batches. For reproducibility, use `seed` parameter (OpenAI) — but even that's "best effort."

**Implication for evals:** Never assert exact string equality on LLM outputs. Always use semantic comparison or structured field matching.

---

## Confidence: High

I understand the tradeoffs, can pick the right settings for each use case, and know the gotchas. Don't need to go deeper.

---

## Sources

- OpenAI API docs — Chat Completions
- First API call experiment (Week 1, Session 3)

---

*Back to [[../02-progress-tracker]] · [[../weeks/week-01]]*
