# Concept Note: Evaluation (Evals)

**Course:** C3 — Building Systems with the ChatGPT API
**Confidence:** M-H

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

## Building a reliable LLM-as-judge rubric

Human grading is the gold standard for semantic/quality checks, but generally impractical at scale (slow, expensive, doesn't scale to continuous testing) — this is why LLM-as-judge has become the practical middle ground. Two ingredients make a judge prompt actually reliable:

### 1. Score each criterion separately, not one blended score

Don't ask for a single "rate this 1-10." Break the judgment into specific, independent criteria (e.g. faithfulness, relevance, tone, completeness) and score each one on its own. Why this matters:

- **Diagnosability** — a single score of "6/10" tells you nothing actionable. Separate scores (e.g. relevance: 9, completeness: 4) show exactly what's broken so you know what to fix.
- **Independent pass/fail thresholds** — some dimensions can be a hard dealbreaker regardless of other scores (e.g. low faithfulness = auto-fail, even if tone and relevance are perfect), while others may be more tolerable (e.g. low completeness, since the user can just ask a follow-up). A single blended score can't express this.
- **Trend tracking over time** — if you tweak a prompt and one dimension improves while another quietly regresses, a blended score can stay flat and hide the regression. Separate scores expose it.

### 2. Give the judge few-shot examples, not just written criteria

There's no objectively true numeric scale for something like "good customer service tone" — an LLM's default sense of what counts as an "8/10" can be arbitrary or inconsistent. Showing the judge concrete examples of what a low-scoring vs. high-scoring response actually looks like anchors its scoring to *your* specific definition of good/bad, rather than its own default notion.

### 3. Ask for reasoning before the score (chain-of-thought)

Have the judge explain *why* it's assigning a score before it states the number, rather than outputting a bare score. This forces the judge to actually reason through the criteria instead of pattern-matching to a number, and — just as importantly — gives you a human-readable explanation to audit when a score looks wrong or surprising.

### Example rubric (customer support response judge)

```
You are grading a customer support response for an ecommerce chatbot.

Score the response on each criterion below from 1 (poor) to 5 (excellent).
For each criterion, first write 1-2 sentences of reasoning, then give the score.

Criteria:
1. Faithfulness — Does the response avoid contradicting the
   retrieved order/tool data? (A false claim here is a hard fail
   regardless of other scores.)
2. Relevance — Does the response directly address what the
   customer actually asked?
3. Completeness — Does the response include all necessary
   information (e.g. order status, next steps) without leaving
   out key details?
4. Tone — Is the response polite, professional, and consistent
   with a helpful support-agent voice?

Examples:
- A response scoring 5 on Faithfulness: [example]
- A response scoring 1 on Faithfulness: [example]
(similar anchor examples for the remaining criteria)

Output format:
{
  "faithfulness": {"reasoning": "...", "score": <1-5>},
  "relevance": {"reasoning": "...", "score": <1-5>},
  "completeness": {"reasoning": "...", "score": <1-5>},
  "tone": {"reasoning": "...", "score": <1-5>}
}
```

Note the output is itself structured JSON — which means the judge's own output can be validated with Pydantic, same as any other LLM output in the pipeline.

## Related

- [[concept-note-prompt-chaining]] — the pipeline being evaluated
- Moderation (input/output checks) — same LLM-as-judge pattern reused for a different purpose
