---
type: concept
domain: transformers
difficulty: beginner
confidence: medium
revisit_date: 2026-07-04
created: 2026-06-04
updated: 2026-06-04
tags:
  - concept
  - transformers
aliases: [Transformer, Transformers]
phase: 0
week_learned: 1
related_courses:
  - "C1 GenAI w/ LLMs"
---

# Transformer Architecture

## In One Sentence
> The Transformer is a neural network architecture that uses self-attention to understand the relationship between every word in a sequence, replacing the sequential processing of RNNs with parallel computation.

## How It Works
> **Before Transformers — RNNs:**
> - Recurrent Neural Networks processed words one at a time, sequentially
> - Limited by available compute — couldn't scale to large datasets
> - Needed to see enough previous context to produce stable, predictable output
>
> **The Transformer (2017 — "Attention Is All You Need"):**
> - Processes all words in parallel, not sequentially
> - Uses **self-attention** to compute how strongly each word relates to every other word in the input
> - Key components:
>   - **Encoder** — reads and understands the input text
>   - **Decoder** — generates the output text
>   - **Multi-headed attention** — runs multiple attention computations in parallel, each learning different relationships (syntax, meaning, coreference)
>   - **Feed-forward network** — processes the attention output
>   - **Softmax output** — converts final values into probability distribution over vocabulary
>
> **Tokenization:**
> - Input text is first converted to numbers using a **tokenizer** — this process is called **tokenization**
> - Tokens are numeric representations of words or sub-words from a dictionary
> - The same tokenizer must be used for both training and text generation
> - Each token is mapped to a **vector** (in the original paper, vector size was 512)

## Why Does It Matter?
> Transformers are the architecture behind every modern LLM (GPT, Claude, LLaMA, Gemini). Understanding the components helps you reason about why models behave the way they do — why longer inputs cost more (self-attention is O(n²)), why tokenizer choice matters, and why different models have different strengths.

## Examples
> - GPT models use only the **decoder** portion of the Transformer
> - BERT uses only the **encoder** portion
> - T5 uses both encoder and decoder (sequence-to-sequence)

## Real-World Application
> Knowing that the same tokenizer must be used for training and inference explains why you can't mix tokenizers across models. It also explains why some languages use more tokens than English — leading to higher costs and shorter effective context windows for non-English text.

## Trade-offs
> —

| Pros | Cons |
|------|------|
| Parallel processing — much faster than RNNs | Self-attention is O(n²) with sequence length — expensive for long inputs |
| Captures long-range dependencies between words | Requires massive compute for training |
| Scales with data and compute | Token-based — not all languages tokenize equally |

## Related Concepts
- [[LLM Fundamentals]]
- [[attention-intuition]]
- [[In-Context Learning]]

## Sources
> C1 GenAI w/ LLMs — Lesson 1

---
%%Confidence guide: low = just learned, revisit in 7 days. medium = understand it, revisit in 30 days. high = could teach it.%%
