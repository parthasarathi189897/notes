---
type: ai-eng-project
project: 8
parent: "[[README]]"
phase: 8
weeks: W46-47
done_by: 2027-04-25
repo: aieng-p08-ci-eval-pipeline
repo_url: ""
status: not-started
created: 2026-05-29
tags:
  - study
  - ai-engineering
  - project
---

# P8 — CI Eval Pipeline

> **Phase 8** · Weeks **46-47** · Done by **Apr 25, 2027**
> Repo: `aieng-p08-ci-eval-pipeline` · [GitHub URL TBD]
> Full spec: [[README#🚦 Project 8 — CI Eval Pipeline]]
>
> Built ON the eval harness from [[p5-eval-harness]]. Wired into the capstone [[p9-capstone]].

---

## 🎯 What I'm shipping

GitHub Action (or similar) that:
- Runs on every push to main + PRs
- Runs unit tests + 10 smoke eval questions
- Compares to baseline scores
- Fails build if groundedness/correctness drops past threshold
- Posts summary comment on PR

---

## ✅ Acceptance criteria

- [ ] Action runs on every push to main + on PRs
- [ ] Smoke eval completes in <5 min
- [ ] Baseline scores stored as artifact, updated on green main
- [ ] Failure threshold configurable
- [ ] At least one intentional regression demoed → build fails as expected
- [ ] PR summary comment includes scores + deltas
- [ ] Pushed to public repo `aieng-p08-ci-eval-pipeline`

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W46 | Scaffold action, wire P5 harness, baseline storage strategy | ⬜ |
| W47 | Threshold logic, PR comment, intentional regression demo, ship | ⬜ |

---

## 🛠️ Decisions log

- CI provider (GitHub Actions / CircleCI / other):
- Baseline storage (artifact / branch / external):
- Threshold strategy (absolute / relative / both):
- PR comment format:

---

## 📊 Performance

- Smoke run duration:
- Baseline update cadence:
- False positive rate observed:

---

## 🐛 Failure modes observed

-

---

## 📝 Post-mortem

**What worked:**
**What didn't:**
**Would I trust this gate on production? Why / why not?**
**One thing I can defend in an interview:**

---

*Back to [[README]] · [[../02-progress-tracker]]*
