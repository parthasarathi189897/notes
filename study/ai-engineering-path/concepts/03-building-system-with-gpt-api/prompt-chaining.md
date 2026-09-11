# Concept Note: Prompt Chaining

**Course:** C3 — Building Systems with the ChatGPT API
**Confidence:** M

## What it is

Instead of giving an LLM one large, monolithic instruction that tries to do everything at once, break the task into multiple smaller, sequential LLM calls (and/or logic steps) — each with a narrow, well-defined job. The output of one step feeds into the next.

## Example (ecommerce chatbot)

1. **Step 1 — Classify:** System prompt categorizes the user query (e.g. "billing", "shipping", "product info")
2. **Step 2 — Act:** Based on the category, invoke the appropriate tool/function (e.g. look up order status)
3. **Step 3 — Respond:** A second LLM call takes the tool's output and synthesizes a natural-language response for the customer

Each step is isolated — the classifier doesn't need to know how to use tools, and the response-synthesizer doesn't need to know how classification works.

## Why it matters (the full list)

1. **Context / token efficiency** — each step only needs the context relevant to its narrow job, not the entire conversation + tool schemas + response guidelines all at once.
2. **Separation of concerns / testability** — each step can be tested and debugged independently (e.g. "is the classifier accurate?" is a separate question from "does the final response sound good?").
3. **Cost/model optimization** — simple steps (like classification) can run on a cheaper/faster model; only the step that genuinely needs strong reasoning (like final response synthesis) needs the expensive model. A single mega-prompt forces the whole pipeline to pay premium-model cost even for trivial sub-tasks.
4. **Debuggability / observability** — when something goes wrong, you can inspect the output of each step individually to pinpoint exactly where the failure occurred (e.g. "the classifier was right, but the tool call failed") rather than guessing inside one opaque giant response.

## Key takeaway

Chaining isn't just an organizational nicety — it has direct cost, reliability, and debugging benefits. Treat each LLM call like a function with a single responsibility, the same way you would in regular software design.
