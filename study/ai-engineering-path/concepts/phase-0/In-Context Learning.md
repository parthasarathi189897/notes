---
type: concept
domain: prompting
difficulty: beginner
confidence: medium
revisit_date: 2026-07-04
created: 2026-06-04
updated: 2026-06-04
tags:
  - concept
  - prompting
aliases: [ICL, in-context learning, zero-shot, one-shot, few-shot]
phase: 0
week_learned: 1
related_courses:
  - "C1 GenAI w/ LLMs"
---

# In-Context Learning

## In One Sentence
> In-context learning is when an LLM learns to perform a task from examples provided in the prompt itself — without any fine-tuning or weight updates.

## How It Works
> The model uses examples in the prompt to infer the pattern and apply it to a new input. Three levels:
>
> **Zero-shot prompting:**
> - No examples given — just the instruction
> - "Classify this review as positive or negative: 'Great product!'"
> - Works when the task is straightforward and the model has seen similar patterns in training
>
> **One-shot prompting:**
> - One example of input → output, then the actual question
> - "Review: 'Loved it!' → Positive. Review: 'Terrible quality' → ?"
> - Helps the model understand the expected format and task
>
> **Few-shot prompting:**
> - Multiple examples (typically 3-5) before the actual question
> - More examples = more reliable pattern recognition
> - Diminishing returns — usually 3-5 examples is enough

## Why Does It Matter?
> In-context learning is the cheapest and fastest way to steer model behavior — no training data, no fine-tuning, no compute costs beyond the API call. It's the first tool an AI engineer reaches for before considering more expensive approaches.

## Examples
> **Zero-shot:**
> ```
> Translate to French: "Hello, how are you?"
> ```
>
> **One-shot:**
> ```
> English: "The cat is on the table" → French: "Le chat est sur la table"
> English: "Hello, how are you?" → French:
> ```
>
> **Few-shot:**
> ```
> Review: "Amazing!" → Sentiment: Positive
> Review: "Worst ever" → Sentiment: Negative
> Review: "It was okay" → Sentiment: Neutral
> Review: "Pretty good value" → Sentiment:
> ```

## Real-World Application
> When building a classification feature at work, start with few-shot prompting. If accuracy is above your threshold (e.g., 90%), ship it. Only consider fine-tuning if few-shot consistently fails — it's 100x cheaper and faster to iterate on prompt examples than to fine-tune.

## Trade-offs
> —

| Pros | Cons |
|------|------|
| No training required — instant iteration | Uses up context window with examples |
| Works across all LLM providers | Quality depends on example selection |
| Cheapest approach to task-specific behavior | Complex tasks may need fine-tuning instead |

## Related Concepts
- [[LLM Fundamentals]]
- [[sampling-parameters]]
- [[Transformer Architecture]]

## Sources
> C1 GenAI w/ LLMs — Lesson 1

---
%%Confidence guide: low = just learned, revisit in 7 days. medium = understand it, revisit in 30 days. high = could teach it.%%
