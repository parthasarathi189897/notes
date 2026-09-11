# Concept Note: Evaluation (Evals)

**Course:** C3 — Building Systems with the ChatGPT API
**Confidence:** M (in progress — continuing tomorrow)

## Why eval matters

Building a single good LLM response once is easy. The real problem eval solves: **how do you know if your system is actually working well, and how do you know if a change you made (prompt tweak, few-shot example, model swap) made it better or worse?**

Things eval typically checks:
- How relevant/correct the answer is
- Whether the output is in the desired format
- Whether behavior is consistent across many inputs, not just one lucky example

## The core challenge

LLM outputs are rarely word-for-word identical even when both are correct (e.g. two valid summaries of the same article will be worded differently). A naive `actual_output == expected_output` string match will falsely fail valid outputs. Different types of checks are needed depending on the type of output.

## Spectrum of eval techniques (easy → hard to grade)

1. **Structural / format checks** — plain code, no LLM needed. E.g.: does the output parse as valid JSON? Are expected keys present? Is a numeric field within a valid range? *(Pydantic validation is itself a form of automated eval for structure.)*

2. **Exact-match / containment checks** — works when there's a small, fixed set of valid answers. E.g.: a classifier that must output exactly `"billing"`, `"shipping"`, or `"other"` — plain string comparison is reliable here.

3. **Semantic / quality checks** — needed when there's no single "correct" wording, e.g. judging if a summary is faithful and high-quality. String comparison doesn't work. Two common approaches:
   - Embedding similarity scores
   - **LLM-as-judge** — a second LLM call grades the output against a rubric or reference answer (same underlying idea as the LLM-as-judge moderation check covered earlier this week)

## Open question to continue tomorrow

Human grading is the gold standard for semantic/quality checks, but generally impractical at scale (slow, expensive, doesn't scale to continuous testing) — this is why LLM-as-judge has become the practical middle ground. Need to go deeper on how to build reliable test cases and scoring rubrics for this.

## Related

- [[concept-note-prompt-chaining]] — the pipeline being evaluated
- Moderation (input/output checks) — same LLM-as-judge pattern reused for a different purpose
