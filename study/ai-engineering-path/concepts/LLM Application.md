---
type: concept-note
topic: LLM Application — Optimization, Tooling & Agents
phase: 0
week_learned: 4
confidence: H
related_courses:
  - "C1 GenAI w/ LLMs"
created: 2026-06-26
updated: 2026-06-26
tags:
  - study
  - ai-engineering
  - concept
  - deployment
  - agents
---

# LLM Application — Optimization, Tooling & Agents

> Phase 0, Week 4. C1 (4/4): deployment, model optimization, and getting an LLM to *do* things via external tools and reasoning loops.

---

## One-sentence summary

To ship an LLM you **shrink it for deployment** (distillation, quantization, pruning) and **extend it with external tools + structured reasoning** (RAG, CoT, PAL, ReAct) to cover what it can't do alone.

---

## Part 1 — Model optimization for deployment

Big models are accurate but expensive/slow to serve. Three ways to make them deployable:

| Technique | What it does | Trade-off |
|-----------|--------------|-----------|
| **Distillation** | A large **teacher** model trains a smaller **student** model to mimic its outputs | Student is faster/cheaper but slightly less capable |
| **Quantization** | Stores weights in lower precision (e.g. FP32 → INT8). *Post-training quantization (PTQ)* applies it after training | Smaller + faster; tiny accuracy loss |
| **Pruning** | Removes weights near 0 (or ~1) that barely contribute to output | Smaller model; aggressive pruning hurts quality |

> Rule of thumb: distillation = "train a smaller model," quantization = "store the same model cheaper," pruning = "delete dead weight."

---

## Part 2 — Why a raw LLM isn't enough

LLMs have built-in limitations that break real apps:

- **Knowledge cut-off** — no awareness of events after training data.
- **Complex tasks** — struggle with multi-step math / precise calculations.
- **Hallucination** — confidently generate plausible-but-wrong text when they don't know the answer.

**Fix:** give the model *external help* — tools (web search, DB / API calls), grounding data (RAG), and structured reasoning prompts.

---

## Part 3 — Techniques to overcome the limits

### RAG — Retrieval Augmented Generation
Fetch relevant external documents first, then feed them into the prompt as context so the answer is **grounded** in real data instead of the model's memory. Fixes knowledge cut-off + hallucination.

### Chain-of-Thought (CoT) prompting
Prompt the model to reason **step by step** before answering, using one-shot or few-shot examples. Improves multi-step / reasoning tasks.

### PAL — Program-Aided Language Model
Offload exact computation to code instead of trusting the LLM's arithmetic.
- The model writes the **reasoning as Python code** (guided by one/few-shot examples).
- Flow: `question + PAL-formatted prompt (few-shot python examples)` → **LLM** → python script → **external interpreter** → result → **LLM** → final answer.
- Fixes the "LLMs are bad at math" limitation by letting a real interpreter do the math.

### ReAct — Reason + Act (the agent loop)
The model interleaves **thinking** and **doing** in a loop:

```
Question
  → Thought      (reason about what's needed)
  → Action       (pick one of the provided tools)
  → Observation  (read the tool's output)
  → … repeat …
  → Answer
```

This is the core **agent loop** — the model decides which tool to call, observes the result, and keeps going until it can answer.

---

## Part 4 — LangChain

A library that makes building these LLM applications easier — it provides the plumbing for:
- Chaining prompts + model calls together.
- Wiring up tools / agents (ReAct-style loops).
- Connecting retrieval (RAG) into the prompt flow.

So instead of hand-coding the Thought→Action→Observation loop, LangChain gives reusable components for it.

---

## Confidence: High

Can explain each optimization technique, the three LLM limitations, and how RAG/CoT/PAL/ReAct each address them. Comfortable with the ReAct agent loop conceptually.

---

## Sources

- C1 GenAI with LLMs — Course 1, module 4 (videos, lab, quiz)
- Week 4 sessions (Jun 23 / Jun 24 / Jun 26)

---

## Related Concepts

- [[In-Context Learning]] — CoT builds on one/few-shot prompting
- [[Fine Tuning]] — alternative to RAG for adapting model behavior
- [[../weeks/week-04]]

---

*Back to [[../02-progress-tracker]] · [[../weeks/week-04]]*
