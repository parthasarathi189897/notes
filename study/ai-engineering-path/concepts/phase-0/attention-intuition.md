---
type: concept-note
topic: Attention Mechanism (Intuition)
phase: 0
week_learned: 2
confidence: M
related_courses:
  - "C1 GenAI w/ LLMs"
created: 2026-06-08
updated: 2026-06-08
tags:
  - study
  - ai-engineering
  - concept
  - transformers
---

# Attention Mechanism — Intuition

> Phase 0, Week 2. Don't memorize the math. Own the intuition.

---

## One-sentence summary

Attention lets the model decide **which other words to focus on** when processing each word in a sequence.

---

## The analogy

Reading a sentence like "The cat sat on the mat because **it** was tired."

A human instantly knows "it" = "the cat." Attention is the mechanism that lets the model make that same connection — by computing a relevance score between "it" and every other word, then weighting them.

---

## Key ideas

1. **Self-attention** — every token attends to every other token in the same sequence. That's why it's O(n²) with sequence length — and why long contexts cost more.

2. **Query / Key / Value** — mental model:
   - **Query:** "I'm the word 'it'. What should I pay attention to?"
   - **Key:** Every other word raises its hand: "Here's what I represent."
   - **Value:** The actual information that gets passed along if attention is high.
   - Score = dot product of Query × Key. High score = high attention.

3. **Multi-head attention** — run attention multiple times in parallel with different learned weights. Each "head" can learn different relationships (syntax, semantics, coreference).

4. **Why it matters for engineering:**
   - Longer context = more attention computation = higher cost + latency
   - Attention patterns explain why models sometimes "forget" instructions at the start of long prompts
   - Chunking strategy in RAG directly affects what the model can attend to

---

## What I don't need to know (yet)

- The exact math of scaled dot-product attention
- Positional encoding formulas
- Flash attention / ring attention optimizations
- How attention differs across architectures (GPT vs BERT vs T5)

---

## Confidence: Medium

I can explain the intuition. I can't derive it from scratch. That's fine for an AI engineer — I need to know *why* context length matters, not prove the attention theorem.

---

## Sources

- C1 GenAI w/ LLMs, Lesson 1
- 3Blue1Brown "Attention in transformers, visually explained" (YouTube)

---

*Back to [[02-progress-tracker]] · [[week-02]]*
