---
type: concept
domain: evaluation
difficulty: intermediate
confidence: medium
revisit_date: 2026-07-16
created: 2026-06-16
updated: 2026-06-16
tags:
  - concept
  - evaluation
aliases: [model eval, evaluation metrics, ROUGE, BLEU, GLUE]
phase: 0
week_learned: 3
related_courses:
  - "C1 GenAI w/ LLMs"
---

# Model Evaluation

## In One Sentence
> Model evaluation is the process of measuring how well an LLM performs on a task using standardized metrics and benchmarks — ranging from simple accuracy for classification to specialized scores for summarization, translation, and general language understanding.

## How It Works

Evaluation metrics are grouped by task type. You pick the right metric for what the model is supposed to do.

### Accuracy (Classification tasks)
- **Formula:** `Correct predictions / Total predictions`
- Works when the output is **deterministic** — one right answer (e.g., sentiment label, category)
- Doesn't work for open-ended generation where multiple correct answers exist

### ROUGE — for Text Summarization
**ROUGE = Recall-Oriented Understudy for Gisting Evaluation**

Measures overlap between the model's generated summary and a reference (human-written) summary.

- **ROUGE-1 (Unigram):** Overlap of individual words
  - `Recall = matching unigrams / total unigrams in reference`
- **ROUGE-2 (Bigram):** Overlap of two-word sequences — penalizes broken phrases; higher score = better phrase-level fidelity
- **ROUGE-N (N-gram):** Generalizes to N-word sequences
- **ROUGE-L:** Longest common subsequence — captures sentence-level structure

> Gotcha: ROUGE measures recall — it rewards long summaries that contain more reference words. Use ROUGE-F1 (harmonic mean of precision + recall) in practice to balance both.

### BLEU — for Translation
**BLEU = Bilingual Evaluation Understudy**

Measures how much the machine-translated output matches one or more reference translations.

- Computes **modified n-gram precision** (unigram through 4-gram)
- Applies a **brevity penalty** — punishes outputs that are too short
- Score: 0 to 1 (higher = better), often reported as 0–100

> Gotcha: BLEU doesn't capture meaning or fluency — a grammatically wrong but word-overlapping sentence can score well. It's a proxy metric, not ground truth.

### Benchmark suites (General language understanding)

Standardized test suites for comparing models across tasks:

| Benchmark | Full name | What it tests | Notes |
|-----------|-----------|--------------|-------|
| **GLUE** | General Language Understanding Evaluation | 9 tasks: sentiment, NLI, paraphrase detection, QA | Was the standard pre-2020; now largely saturated |
| **SuperGLUE** | Super GLUE | Harder tasks that GLUE-trained models nearly saturated | Current standard for classification-era models |
| **MMLU** | Massive Multitask Language Understanding | 57 academic subjects: STEM, law, medicine, history | Tests breadth of world knowledge |
| **HELM** | Holistic Evaluation of Language Models | Multi-metric, multi-scenario: accuracy + calibration + robustness + fairness | Most comprehensive; used for model card comparisons |

> Rule of thumb: GLUE/SuperGLUE = language task capability. MMLU = knowledge breadth. HELM = production-readiness comparison.

## Why Does It Matter?
> You can't improve what you can't measure. Evaluation is the feedback loop for everything — choosing between models, deciding if fine-tuning helped, detecting regressions, and making "ship it" decisions. Picking the wrong metric for your task gives you a false signal: high ROUGE doesn't mean your summaries are useful; high accuracy on MMLU doesn't mean your model generalizes to your specific domain.

## Examples

```
# ROUGE-1 worked example
Reference: "The cat sat on the mat"
Generated: "The cat sat"

Recall    = 3/6 = 0.50  (3 words matched out of 6 in reference)
Precision = 3/3 = 1.00  (all 3 generated words matched reference)
F1        = 2 × (1.0 × 0.5) / (1.0 + 0.5) = 0.67
```

```
# BLEU 1-gram precision example
Reference:  "The house is small"
Generated:  "The house is tiny"
Precision = 3/4 = 0.75  ("The", "house", "is" match; "tiny" doesn't)
```

## Real-World Application
> When building a product description summarizer, use ROUGE-2 + human spot-checks — ROUGE alone isn't enough. When comparing two foundation models for a classification task (e.g., category prediction), use accuracy on your eval set and cross-reference with MMLU scores from their model cards. Don't trust a single number — triangulate across metrics.

## Trade-offs

| Pros | Cons |
|------|------|
| Automated — run at scale in CI/CD evals | Reference-based metrics can't capture paraphrase quality |
| Standardized benchmarks allow model comparison | BLEU/ROUGE don't measure meaning or factual accuracy |
| HELM gives a multi-dimensional production view | Benchmark saturation — models can overfit to MMLU-style questions |

## Related Concepts
- [[LLM Fundamentals]]
- [[Fine Tuning]]
- [[In-Context Learning]]
- [[Pre training]]
- [[sampling-parameters]]
- [[Reinforcement learning - Human feedback]]

## Sources
> C1 GenAI w/ LLMs — Week 3

---
%%Confidence guide: low = just learned, revisit in 7 days. medium = understand it, revisit in 30 days. high = could teach it.%%
