---
type: reference
created: 2026-02-20
tags:
  - reference
---

# Wibey Skills

> AI-powered automations for this vault. Run from the Wibey CLI.

## Quick Reference

| Skill | What It Does | How to Call |
|-------|-------------|-------------|
| **obsidian-daily** | Creates daily note + weekly review | `/obsidian-daily` or "create my daily note" |
| **obsidian-initiatives** | Updates initiatives + syncs to Confluence | `/obsidian-initiatives` or "update initiative X" |
| **obsidian-performance** | Aggregates wins into performance review | `/obsidian-performance` or "capture wins" |
| **obsidian-study** | Creates Zettelkasten concept notes | `/obsidian-study` or "I learned about X" |
| **obsidian-scratchpad** | Quick-captures ideas and ad-hoc work | `/obsidian-scratchpad` or "new idea X" |

## Detailed Usage

### obsidian-daily

**Daily note** — Run every morning to start your day.
```
"create my daily note"
"start my day"
```
What it does:
1. Reads yesterday's note for carry-over tasks
2. Fetches today's calendar (MS Graph)
3. Asks for priorities (optional)
4. Creates `work/daily-notes/YYYY-MM-DD.md`

**Weekly review** — Run Friday or weekend to wrap up the week.
```
"weekly review"
"summarize my week"
```
What it does:
1. Reads all daily notes Mon–Fri
2. Aggregates wins, decisions, blockers, tasks
3. Creates `work/weekly-reviews/YYYY-WXX.md`

---

### obsidian-initiatives

**Update initiative** — Add progress from daily notes.
```
"update initiative Express Delivery Badge"
"update initiative [name]"
```
What it does:
1. Scans last 7 daily notes for mentions
2. Asks for additional context
3. Updates Progress Log, Decision Log, Milestones

**Sync to Confluence** — Push latest progress to Confluence.
```
"sync initiative to confluence"
"push Express Delivery Badge to confluence"
```
What it does:
1. Reads initiative note
2. Compares with Confluence page
3. Previews changes, asks for confirmation
4. Updates Confluence page

---

### obsidian-performance

```
"performance snapshot"
"capture wins"
"update my performance doc"
```
What it does:
1. Finds review doc in `work/performance/`
2. Scans daily notes + initiatives since last update
3. Extracts wins, decisions, leadership, collaboration
4. Updates the review doc

**When to run**: Every 1-2 weeks, or before a review conversation.

---

### obsidian-study

```
"I learned about circuit breakers"
"new concept distributed consensus"
```
What it does:
1. Asks you to explain the concept
2. Creates `study/concepts/<Name>.md` using Zettelkasten format
3. Links to related concepts and updates MOC

---

### obsidian-scratchpad

```
"new idea API caching layer"
"jot this down — helped Krunal debug the auth flow"
```
What it does:
1. Asks for topic + context (2-3 questions)
2. Categorizes: idea, team-contribution, investigation, tooling
3. Creates `work/scratchpad/<slug>.md`

## Tips

- **Natural language works** — You don't need to remember exact commands. Just describe what you want.
- **Skills read your vault** — They know about your existing notes, initiatives, and daily entries.
- **Skills use templates** — Every note created follows the vault's template structure.
- **Confirm before destructive ops** — Confluence sync always previews before pushing.
