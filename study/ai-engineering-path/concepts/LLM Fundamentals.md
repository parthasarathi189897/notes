---
type: concept
domain: llm-basics
difficulty: beginner
confidence: medium
revisit_date: 2026-07-04
created: 2026-06-04
updated: 2026-06-04
tags:
  - concept
  - llm-basics
aliases: [LLM basics, LLM terminology]
phase: 0
week_learned: 1
related_courses:
  - "C1 GenAI w/ LLMs"
---

# LLM Fundamentals

## In One Sentence
> LLMs take text input (prompts), process it through a neural network (inference), and predict the most likely next words (completion) within a fixed memory space (context window).

## How It Works
> - **Prompt**: The instruction or text you give to the model as input
> - **Completion**: The output the model generates — it predicts the next most likely words based on the prompt
> - **Inference**: The process of taking a prompt as input and producing a completion — this is what happens every time you "call" an LLM
> - **Context window**: The maximum amount of text (measured in tokens) the model can process at once — both input and output must fit within this window
> - Smaller, focused models can be pre-trained to perform specific tasks better than large general-purpose models

## Why Does It Matter?
> Understanding these terms is the foundation for everything in AI engineering. You can't design prompts, evaluate outputs, or reason about costs without knowing what inference is, what a context window constrains, and how completions are generated.

## Examples
> - GPT-4o has a 128K token context window — roughly 96K words
> - A single API call = one inference = one prompt → completion cycle
> - Cost is typically measured per 1K tokens (input + output)

## Real-World Application
> When building an LLM-powered feature, the context window determines how much data you can pass in. If your documents exceed the window, you need chunking strategies (RAG) instead of stuffing everything into one prompt.

## Trade-offs
> —

| Pros | Cons |
|------|------|
| Simple mental model to start with | Easy to confuse "training" vs "inference" |
| Applies across all LLM providers | Context window limits vary by model and change frequently |

## Related Concepts
- [[Transformer Architecture]]
- [[In-Context Learning]]
- [[sampling-parameters]]

## Sources
> C1 GenAI w/ LLMs — Lesson 1

---
%%Confidence guide: low = just learned, revisit in 7 days. medium = understand it, revisit in 30 days. high = could teach it.%%
