---
type: concept
domain: llm-alignment
difficulty: intermediate
confidence: low
revisit_date: 2026-06-28
created: 2026-06-21
updated: 2026-06-21
tags:
  - concept
  - llm-alignment
  - rlhf
  - fine-tuning
aliases: [RLHF, RLAIF, reinforcement learning from human feedback]
phase: 0
week_learned: 3
related_courses:
  - "C1 GenAI w/ LLMs"
---

# Reinforcement Learning from Human Feedback (RLHF)

## In One Sentence
> RLHF is a training technique that aligns LLM outputs with human preferences by training a reward model on human-labeled comparisons and then using reinforcement learning (PPO) to optimize the LLM toward that reward signal.

## How It Works

### The Alignment Problem
A pre-trained or instruction-tuned LLM can generate fluent text but doesn't inherently behave in a **helpful, honest, harmless (HHH)** way:
- **Helpful** — answers the user's actual intent
- **Honest** — doesn't fabricate or mislead
- **Harmless** — avoids illegal, immoral, or unethical outputs

RLHF is the primary technique used to close this gap.

![[reinforcement_learning.excalidraw]]

---

### The Three-Stage Pipeline

![[RLHF.excalidraw|600x200]]

![[RLHF.png]]

**Stage 1 — Supervised Fine-Tuning (SFT)**
- Start from the base or instruction-tuned model
- Fine-tune on high-quality human-written (prompt, response) pairs
- Produces a starting policy for RL training

**Stage 2 — Train a Reward Model**
- Human labelers rank model outputs: given the same prompt, which response is better?
- Train a separate reward model (binary classifier / scoring model) on these preference pairs
- Once trained, no more human labelers needed — the reward model approximates human judgment at scale
- Key insight: **clarity of instruction to labelers** has a large impact on reward model quality — ambiguous rubrics produce noisy labels

**Stage 3 — RL Fine-Tuning (PPO)**
- Treat the SFT model as a policy
- For each prompt: generate a response → score with reward model → update policy weights to increase expected reward
- Algorithm: **Proximal Policy Optimization (PPO)**

---

### Reward Hacking
When the LLM learns to maximize the reward model's score in ways that don't reflect genuine quality — e.g., generating verbose, sycophantic, or superficially impressive text that tricks the reward model.

**Fix: KL-divergence penalty**
- A penalty term is added to the RL objective: `total_reward = reward_score − β × KL(π_RL || π_SFT)`
- This penalizes the RL-tuned policy for drifting too far from the original SFT model
- Prevents reward hacking while still allowing meaningful alignment improvement

![[KL divergence and PEFT in RLHF.png]]

![[KL Divergence.png]]

---

### Constitutional AI (CAI)
An alternative alignment approach from Anthropic:
- Instead of human-labeled preferences, a **set of principles (the "constitution")** defines what counts as helpful, harmless, and honest
- The model critiques and revises its own outputs against these principles
- Avoids relying on human labelers for every RLHF iteration

### RLAIF — Reinforcement Learning from AI Feedback
- A variant of RLHF where the reward signal comes from **another LLM** rather than human labelers
- The AI evaluator labels which outputs are better, replacing the human labeling step
- Scalable: human labeling is the bottleneck in RLHF; RLAIF removes it
- Trade-off: the AI evaluator can have its own biases

## Why Does It Matter?
> RLHF is the reason modern chat models (ChatGPT, Claude, Gemini) behave helpfully in conversation rather than just completing text patterns. Understanding RLHF explains why model behavior can differ dramatically from the same base model's raw outputs, and why reward hacking is a real risk when deploying fine-tuned models in production.

## Examples
> The PPO training loop, simplified:
> 1. Sample a prompt from the dataset
> 2. Generate a response with the current policy
> 3. Score with reward model → `r`
> 4. Compute KL penalty against SFT policy → `−β × KL`
> 5. Update policy to maximize `r − β × KL`
> 6. Repeat until reward stabilizes or KL divergence exceeds threshold

## Real-World Application
> At Walmart, if a customer-facing LLM (e.g., a shopping assistant) is generating responses that are technically correct but tone-deaf or harmful, RLHF is the right tool — not more prompt engineering. In practice: collect preference data from human reviewers on a sample of live responses, train a reward model, run PPO fine-tuning. Start with RLAIF if labeling budget is tight.

## Trade-offs

| Pros | Cons |
|------|------|
| Aligns model to human values without requiring perfect training data | Human labeling is expensive, slow, and subjective |
| Reward model generalizes — no labeler needed at inference | Reward hacking: model can game the reward signal |
| KL penalty keeps alignment stable | PPO is complex to tune (β, learning rate, rollout length) |
| RLAIF scales without human labelers | RLAIF inherits AI evaluator biases |

## Related Concepts
- [[Fine Tuning]]
- [[Pre training]]
- [[Model Evaluation]]
- [[In-Context Learning]]
- [[LLM Fundamentals]]

## Sources
> C1 GenAI w/ LLMs — Week 3 (RLHF + evaluation)
> Session log: Week 3, Session 3 — Jun 20, 2026
> Rough notes: `Reinforcement learning - Human feedback.md` (pre-restructure)

---
%%Confidence guide: low = just learned, revisit in 7 days. medium = understand it, revisit in 30 days. high = could teach it.%%
%%Confidence set to LOW: W3 session logs show only ~30m on this topic with partial notes. Revisit Jun 28.%%
