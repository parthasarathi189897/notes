---
type: concept
domain: prompting
difficulty: intermediate
confidence: medium
revisit_date: 2026-10-11
created: 2026-09-18
updated: 2026-09-18
tags:
  - concept
  - prompting
  - llm-apps
aliases: [chaining prompts, prompt pipelines]
phase: 1
week_learned: 8
related_courses:
  - "C3 Building Systems with the ChatGPT API"
---

# Prompt Chaining

## In One Sentence
> Prompt chaining is breaking one complex LLM task into a sequence of smaller, focused calls — where the output of one step becomes the input to the next — instead of trying to do everything in a single mega-prompt.

## How It Works

Instead of one prompt that tries to classify, extract, and respond all at once, you split the workflow into stages, each with a narrow job:

```
User input
   │
   ▼
[Step 1: Classify intent]  →  category
   │
   ▼
[Step 2: Extract structured fields]  →  JSON (category-specific schema)
   │
   ▼
[Step 3: Generate response]  →  final text, grounded in step 1+2 output
```

Each step is its own API call with its own focused prompt. Later steps can also **branch** based on earlier output — e.g. only run the "refund" extraction schema if step 1 classified the message as a refund request.

## Why Does It Matter?
> Four concrete reasons chaining beats one giant prompt:
> 1. **Context efficiency** — each call only sees what it needs, not the whole instruction set for every possible path.
> 2. **Separation of concerns** — a classification prompt and a generation prompt have different failure modes; mixing them makes both harder to debug.
> 3. **Cost/model optimization** — cheap, fast models can handle simple steps (classification); only route to a stronger, pricier model where the task actually needs it.
> 4. **Debuggability** — when something goes wrong, you can inspect the output of each stage individually instead of guessing which part of one enormous prompt misfired.

## Trade-offs

| Pros | Cons |
|------|------|
| Each step is simpler to prompt-engineer and test | More API calls → more latency, more cost per request |
| Failures are localized to one step | More moving parts to orchestrate and log |
| Cheaper models can be used for easy steps | Errors can compound across steps if not validated between them |

## Real-World Application
> This is the shape of P1 (`aieng-p01-json-extractor`): classify → extract structured fields with Pydantic → (optionally) draft a suggested response — three narrow steps instead of one prompt asked to do it all, with validation between steps so a bad step-1 output doesn't silently corrupt step 2.

## Related Concepts
- [[pydantic]]
- [[Model Evaluation]]
- [[LLM Application]]

## Sources
> C3 Building Systems with the ChatGPT API — Week 8

---
%%Confidence guide: low = just learned, revisit in 7 days. medium = understand it, revisit in 30 days. high = could teach it.%%
