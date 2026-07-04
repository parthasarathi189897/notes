---
type: concept
domain: fine-tuning
difficulty: intermediate
confidence: medium
revisit_date: 2026-07-16
created: 2026-06-16
updated: 2026-06-16
tags:
  - concept
  - fine-tuning
  - llm-training
aliases: [fine tuning, finetuning, instruction tuning, PEFT, LoRA]
phase: 0
week_learned: 3
related_courses:
  - "C1 GenAI w/ LLMs"
---

# Fine Tuning

## In One Sentence
> Fine-tuning adapts a pre-trained LLM to a specific task by continuing training on a smaller, task-relevant dataset — bridging the gap when in-context learning isn't reliable enough.

## How It Works

### Why fine-tune at all?
In-context learning (zero-shot / few-shot prompting) often works well, but it has limits:
- **Reliability:** Few-shot can be inconsistent on structured or specialized tasks
- **Context bloating:** Packing many examples into every prompt wastes tokens and increases cost per call
- **Complex behavior:** Some tasks (e.g., always responding in a specific format, following safety rules) are hard to teach purely via prompt

When those limits are hit, fine-tuning is the next step.

---

### Full fine-tuning (Instruction fine-tuning)
- All model weights are updated during training
- Requires a dataset of **(instruction → response)** pairs
- Example dataset format:
  ```
  Instruction: "Summarize the following customer review in one sentence."
  Response:    "The customer was satisfied with the product quality but complained about shipping time."
  ```
- **FLAN (Fine-tuned LAnguage Net)** is the canonical example: Google fine-tuned T5 using instruction datasets across many tasks
  - Used **SAMSUM** dataset (dialogue summarization)
  - Used **DialogSum** dataset (conversational summarization)

**Fine-tuning on a single task:**
- Train on one task only (e.g., only summarization)
- Risk: **catastrophic forgetting** (see below)

**Multi-task fine-tuning:**
- Train on multiple tasks simultaneously — e.g., summarization + sentiment + review rating
- More data needed, but the model retains breadth
- Reduces catastrophic forgetting

---

### Catastrophic forgetting
When you fine-tune on a narrow task, the model's weights shift to optimize for it — and it can **forget** general capabilities it had before.

Example: Fine-tune on legal document summarization → model gets worse at code generation, translation, and general Q&A.

**How to avoid it:**
1. **Multi-task fine-tuning** — train on several tasks at once so no single task dominates
2. **Parameter Efficient Fine-Tuning (PEFT)** — the preferred modern approach (see below)

---

### Parameter Efficient Fine-Tuning (PEFT)
Instead of updating all model weights, PEFT freezes the original weights and trains only a small number of new parameters.

Benefits:
- **Preserves original weights** → robust to catastrophic forgetting
- **Much cheaper** — trains in hours instead of days; fits on consumer GPUs
- **Modular** — you can swap task-specific adapters without retraining the base model

**LoRA (Low-Rank Adaptation):**
- The most widely used PEFT method
- Key idea: weight updates during fine-tuning tend to be **low-rank** — you don't need to update the full weight matrix
- LoRA decomposes the update into two small matrices: `W_original + (A × B)` where A and B are much smaller
- Only A and B are trained; W_original stays frozen
- At inference: merge A × B back into W_original — zero added latency
- Typical rank values: 4, 8, 16 (lower rank = fewer parameters = faster training, but less expressive)

**Prompt tuning (soft prompts):**
- Instead of modifying weights, learns a set of trainable "virtual tokens" prepended to every input
- These tokens aren't real words — they're continuous embeddings tuned to steer the model
- Simpler than LoRA but less powerful for complex task adaptation

---

### Decision tree: when to use what

```
Task performance with zero/few-shot?
  → Good enough → Ship it. Don't fine-tune.
  → Not reliable → Fine-tune

Have lots of GPU budget?
  → Yes → Full fine-tuning (instruction tuning, multi-task)
  → No  → PEFT (LoRA is the default choice)

Risk of forgetting other tasks?
  → Yes → Multi-task fine-tuning OR LoRA (preserves base weights)
  → No  → Single-task fine-tuning is fine
```

## Why Does It Matter?
> Fine-tuning is the lever between "the model kind of does what I want" and "the model reliably does exactly what I want." Understanding which variant to use (full vs. PEFT vs. prompt tuning) determines whether a project costs $500 or $50,000 in GPU compute. LoRA has made fine-tuning accessible — most practical fine-tuning today is LoRA-based.

## Examples

```python
# LoRA config example (using HuggingFace PEFT library)
from peft import LoraConfig, get_peft_model

config = LoraConfig(
    r=8,              # rank — how many parameters to train
    lora_alpha=32,    # scaling factor
    target_modules=["q_proj", "v_proj"],  # which layers to adapt
    lora_dropout=0.1,
    bias="none",
)
model = get_peft_model(base_model, config)
model.print_trainable_parameters()
# "trainable params: 4,194,304 || all params: 6,742,609,920 || trainable%: 0.062%"
```

## Real-World Application
> At Walmart, if you're building a product tagging model that needs to output structured categories consistently, start with few-shot prompting. If it's hitting 85% accuracy and you need 95%+, consider LoRA fine-tuning on a labeled tagging dataset. Full fine-tuning is rarely justified unless you're building a domain-specific foundation model from scratch.

## Trade-offs

| Pros | Cons |
|------|------|
| Reliably shifts model behavior for specific tasks | Full fine-tuning is expensive in compute + data |
| PEFT/LoRA is cheap and GPU-accessible | Requires labeled (instruction, response) pairs — data collection cost |
| LoRA preserves base model generality | Over-tuning on narrow data risks quality regression on other tasks |
| Swappable adapters — one base, many tasks | Harder to iterate than prompt engineering |

## Related Concepts
- [[Pre training]]
- [[In-Context Learning]]
- [[Model Evaluation]]
- [[LLM Fundamentals]]
- [[Transformer Architecture]]
- [[Reinforcement learning - Human feedback]]

## Sources
> C1 GenAI w/ LLMs — Week 2 (instruction tuning) + Week 3 (RLHF + PEFT)
> Session log: Week 3, Session 1 — Jun 16, 2026

---
%%Confidence guide: low = just learned, revisit in 7 days. medium = understand it, revisit in 30 days. high = could teach it.%%
