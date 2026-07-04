---
type: concept-note
topic: "Phase 0 Synthesis — Pretraining vs Instruction-Tuning vs RLHF vs Fine-Tuning vs RAG"
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
  - synthesis
  - phase-0-exit
---

# Phase 0 Synthesis — The Five Ways to Shape an LLM

> **Phase 0 exit test.** If I can explain these five in plain English without notes, I'm ready for W5.
> The question every AI engineer answers first: *"My model isn't doing what I want — which lever do I pull?"*

---

## One-sentence summary

**Pretraining** builds raw knowledge, **instruction-tuning** teaches it to follow orders, **RLHF** aligns it to human taste, **fine-tuning** specializes it for a task, and **RAG** feeds it fresh facts at runtime — the first three *make* the model, the last two *adapt* it.

---

## The one-line mental model

| Technique | What it changes | When it happens | Plain English |
|-----------|-----------------|-----------------|---------------|
| **Pretraining** | Builds the base weights from scratch | Once, by the model maker | "Read the whole internet and learn how language works." |
| **Instruction-Tuning** | Updates weights on (instruction → response) pairs | After pretraining | "Learn to *follow instructions*, not just autocomplete." |
| **RLHF** | Updates weights toward human-preferred answers | After instruction-tuning | "Learn what humans actually *like* (helpful, honest, harmless)." |
| **Fine-Tuning** | Updates weights for *your* narrow task | When you adapt it | "Specialize in *my* job (e.g., legal summaries)." |
| **RAG** | Changes nothing — adds context at query time | At inference, every call | "Look it up *now* instead of memorizing it." |

> Key split: **Pretraining → Instruction-tuning → RLHF** is how the *foundation model* is built (the maker does it). **Fine-tuning** and **RAG** are how *you* adapt that model (you do it).

---

## 1. Pretraining — learn language from raw text

- **Self-supervised** learning on massive *unlabeled* text — the label is the next (or masked) token, so no humans needed.
- Produces a **base model** that's great at predicting text but doesn't reliably follow instructions.
- Three flavors by architecture: autoencoding (BERT, classification), autoregressive (GPT, generation), seq2seq (T5, translation/summarization).
- **You never do this** — it's millions of dollars of compute. You consume the output.

→ See [[Pre training]]

---

## 2. Instruction-Tuning — teach it to follow orders

- Supervised fine-tuning on **(instruction → response)** pairs (e.g., FLAN).
- Turns "autocomplete the text" into "do what the prompt asks."
- It's a *type* of fine-tuning, but done by the model maker on broad, multi-task instruction data.
- Risk: **catastrophic forgetting** if trained too narrowly → multi-task tuning mitigates it.

→ See [[Fine Tuning]]

---

## 3. RLHF — align it to human preference

- Instruction-tuning makes the model *capable*; RLHF makes it *agreeable* — **helpful, honest, harmless (HHH)**.
- Three stages: **SFT** → **train a reward model** on human preference rankings → **PPO** to optimize the policy toward that reward.
- Watch for **reward hacking** → fixed with a **KL-divergence penalty** that stops the model drifting too far from the SFT version.
- Variants: Constitutional AI (principles instead of labelers), RLAIF (AI feedback instead of human).

→ See [[Reinforcement learning - Human feedback]]

---

## 4. Fine-Tuning — specialize it for *your* task

- *You* take a foundation model and continue training it on *your* labeled task data.
- Use it when prompting (in-context learning) isn't reliable enough.
- **Full fine-tuning** = update all weights (expensive). **PEFT / LoRA** = freeze the base, train tiny adapters (cheap, GPU-friendly, preserves generality).
- Permanent: the new behavior is baked into weights.

→ See [[Fine Tuning]] · [[In-Context Learning]] (the cheaper alternative to try first)

---

## 5. RAG — give it fresh facts at runtime

- Changes **no weights**. Retrieves relevant documents and injects them into the prompt as context.
- Fixes the things weights can't: **knowledge cut-off** and **hallucination**.
- Cheapest way to add *new/changing* knowledge — update the document store, not the model.

→ See [[LLM Application]]

---

## The decision tree (the whole point)

```
"My LLM isn't doing what I want."

1. Does it need NEW or CHANGING facts (post-cutoff, private docs)?
     → RAG.  (Don't retrain for knowledge that changes.)

2. Does it just need the right examples / format?
     → In-context learning (zero/few-shot).  Cheapest. Try first.

3. Does it need a NEW SKILL or consistent task behavior prompting can't give?
     → Fine-tuning.  (LoRA first; full fine-tuning only if you must.)

4. Is the BEHAVIOR/TONE off — unhelpful, unsafe, sycophantic?
     → RLHF.  (Alignment, not capability.)

5. Building a foundation model from scratch?
     → Pretraining.  (You almost never are.)
```

> **Mnemonic:** *Facts → RAG. Format → prompt. Skill → fine-tune. Behavior → RLHF. From scratch → pretrain.*

---

## Knowledge vs Behavior vs Skill — the cleanest cut

- **Need knowledge?** → **RAG** (runtime) — facts change, don't bake them in.
- **Need behavior/alignment?** → **RLHF** — *how* it responds.
- **Need a skill/task?** → **Fine-tuning** — *what* it can do.
- **Building the brain itself?** → **Pretraining** + **Instruction-tuning** (the maker's job).

---

## Confidence: High

Can explain all five from memory, place them on the build-vs-adapt and weights-vs-runtime axes, and pick the right lever for a given failure mode via the decision tree. **Phase 0 exit criterion met.**

---

## Sources

- C1 GenAI with LLMs (Course 1, all 4 modules) — W1–W4
- Synthesis of my own Phase 0 concept notes (below)

---

## Related Concepts

- [[Pre training]]
- [[Fine Tuning]]
- [[Reinforcement learning - Human feedback]]
- [[In-Context Learning]]
- [[LLM Application]]
- [[Model Evaluation]]
- [[LLM Fundamentals]]
- [[Transformer Architecture]]

---

*Back to [[../02-progress-tracker]] · [[../weeks/week-04]]*
