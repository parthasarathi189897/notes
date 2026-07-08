---
type: concept-note
topic: Pre-Training of Large Language Models
phase: 0
week_learned: 2
confidence: M
related_courses:
  - "C1 GenAI w/ LLMs"
created: 2026-06-09
updated: 2026-06-09
tags:
  - study
  - ai-engineering
  - concept
  - pretraining
  - transformers
---

# Pre-Training of Large Language Models

> Phase 0, Week 2. Understand the three model families and when to use each.

---

## One-sentence summary

Pre-training is the initial large-scale training step where a model learns language patterns from massive unlabeled text — before any task-specific fine-tuning.

---

## Model selection starting point

After you decide your use case, choose the right model type:

1. **Pre-trained models** (foundational LLMs) — general-purpose, ready to use
2. **Custom-trained models** — domain-specific, fine-tuned for your task

Model hubs like Hugging Face and PyTorch Hub list open-source models with benchmarks so you can evaluate fit for your use case.

---

## The three model families

LLMs are trained using **self-supervised learning** — the labels come from the data itself, no human annotation needed.

### 1. Autoencoding models (Encoder-only)

- Training objective: **Masked Language Modeling (MLM)** — randomly mask tokens, predict them
- Context: **Bidirectional** — sees the full sequence (past + future)
- Best for:
  - Sentiment analysis
  - Named entity recognition
  - Text classification
- Example: BERT, RoBERTa

### 2. Autoregressive models (Decoder-only)

- Training objective: **Causal Language Modeling (CLM)** — predict the next token
- Context: **Unidirectional** — only sees previous tokens
- Best for:
  - Text generation
  - Completion tasks
- Example: GPT series, LLaMA

### 3. Sequence-to-sequence models (Encoder + Decoder)

- Training objective: **Span corruption** — mask spans with sentinel tokens, reconstruct them
- The encoder processes the masked input; the decoder reconstructs the masked spans autoregressively
- Best for:
  - Translation
  - Text summarization
  - Question answering
- Example: T5, BART

---

## Quick reference

| Model type | Architecture | Training objective | Context | Use when |
|---|---|---|---|---|
| Autoencoding | Encoder only | Masked LM | Bidirectional | Classification, understanding |
| Autoregressive | Decoder only | Causal LM | Unidirectional | Generation, completion |
| Seq2seq | Encoder + Decoder | Span corruption | Both | Translation, summarization |

---

## What I don't need to know (yet)

- The exact compute / data scale for pretraining runs
- Chinchilla scaling laws
- How to run pretraining yourself (not needed at this stage)

---

## Confidence: Medium

I can explain the three families and pick the right one for a use case. I can't explain the math behind masked LM loss or span corruption in depth yet.

---

## Sources

- C1 GenAI w/ LLMs, Week 2 video
- Session notes from Jun 09, 2026

---

*Back to [[02-progress-tracker]] · [[week-02]]*
