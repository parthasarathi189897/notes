---
type: ai-eng-project
project: 6
parent: "[[README]]"
phase: 6
weeks: W37-38
done_by: 2027-02-21
repo: aieng-p06-finetuning-memo
repo_url: ""
status: not-started
created: 2026-05-29
tags:
  - study
  - ai-engineering
  - project
---

# P6 — Fine-tuning Decision Memo

> **Phase 6** · Weeks **37-38** · Done by **Feb 21, 2027**
> Repo: `aieng-p06-finetuning-memo` · [GitHub URL TBD]
> Full spec: [[README#📝 Project 6 — Fine-tuning Decision Memo]]
>
> **The point of this project is to demonstrate engineering judgment, not to fine-tune.**

---

## 🎯 What I'm shipping

A ≤2-page memo answering: should we fine-tune for task X?
Optional: a narrow fine-tune experiment (classification or extraction) with before/after metrics.

---

## ✅ Acceptance criteria

- [ ] Memo ≤2 pages, written for non-AI engineer audience
- [ ] All 8 sections answered with specifics
- [ ] Concrete go / no-go recommendation
- [ ] Optional: narrow fine-tune with before/after metrics
- [ ] Pushed to public repo `aieng-p06-finetuning-memo`

---

## 📋 Memo sections (8)

1. **Task:** what specifically would we fine-tune?
2. **Why prompting is not enough** — evidence:
3. **Why RAG is not enough** — evidence:
4. **Training data needed** — size, source, quality:
5. **Expected metric improvement** — concrete numbers:
6. **Failure risks**:
7. **Cost estimate** — training + inference:
8. **Rollback plan**:

**Recommendation:** GO / NO-GO

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W37 | Pick task, gather evidence (run prompting + RAG experiments to prove inadequacy) | ⬜ |
| W38 | Write memo, polish, (optional) tiny FT experiment, ship | ⬜ |

---

## 🛠️ Optional experiment

- Task chosen (classification / extraction / formatting):
- Base model:
- Data size:
- Method (full FT / LoRA / QLoRA):
- Before metric:
- After metric:
- Cost of training run:

---

## 📝 Post-mortem

**What worked:**
**What didn't:**
**Did I convince myself? Did I convince a skeptic?**
**One thing I can defend in an interview:**

---

*Back to [[README]] · [[../02-progress-tracker]]*
