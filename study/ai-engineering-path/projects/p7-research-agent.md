---
type: ai-eng-project
project: 7
parent: "[[README]]"
phase: 7
weeks: W40-43
done_by: 2027-03-28
repo: aieng-p07-research-agent
repo_url: ""
status: not-started
created: 2026-05-29
tags:
  - study
  - ai-engineering
  - project
---

# P7 — Simple Research Agent

> **Phase 7** · Weeks **40-43** · Done by **Mar 28, 2027**
> Repo: `aieng-p07-research-agent` · [GitHub URL TBD]
> Full spec: [[README#🤖 Project 7 — Simple Research Agent]]
>
> **One reliable agent > five flaky ones.**

---

## 🎯 What I'm shipping

Agent that:
- Takes a question → plans steps → retrieves from local docs → calls 1-2 tools → logs each step → synthesizes cited answer
- Includes trajectory evaluation

---

## ✅ Acceptance criteria

- [ ] Handles 10 sample queries end-to-end without crashing
- [ ] Every step logged (plan, tool calls, intermediate results)
- [ ] Final answer cites sources
- [ ] Trajectory eval scores plan quality, tool selection, answer correctness
- [ ] Manual review: 7/10 trajectories "reasonable"
- [ ] README explains design + failure modes
- [ ] Pushed to public repo `aieng-p07-research-agent`

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W40 | Scaffold agent, pick 1-2 tools (web search? calc? code exec?) | ⬜ |
| W41 | Planner loop working on simple queries | ⬜ |
| W42 | Tool integration, full trajectory logging | ⬜ |
| W43 | Trajectory eval, 10 sample run, README, ship | ⬜ |

---

## 🛠️ Decisions log

- Agent framework (manual / minimal lib):
- Tools selected:
- Planning strategy (ReAct? Plan-and-Execute?):
- Trajectory eval (manual? LLM judge?):

---

## 📊 Numbers

- Sample queries: 10
- "Reasonable" trajectories: __/10
- Avg steps per query:
- Avg cost per query:
- Avg latency per query:

---

## 🐛 Failure modes observed

> Agent failure modes are different from RAG. Categorize carefully.

- Planning failures:
- Tool selection failures:
- Tool execution failures:
- Synthesis failures:

---

## 📝 Post-mortem

**What worked:**
**What didn't:**
**Is this agent better than a well-prompted single LLM call? Be honest.**
**One thing I can defend in an interview:**

---

*Back to [[README]] · [[../02-progress-tracker]]*
