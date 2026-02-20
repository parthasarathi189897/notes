---
type: reference
created: 2026-02-20
tags:
  - reference
---

# Vault Structure

> How this vault is organized and what goes where.

## Overview

```
notes/
├── _reference/           ← You are here
├── work/
│   ├── daily-notes/      ← Daily log files
│   ├── weekly-reviews/   ← Weekly aggregations
│   ├── initiatives/      ← Strategic projects
│   ├── performance/      ← Year-end review docs
│   ├── scratchpad/       ← Ideas & ad-hoc work
│   └── reference/        ← Work reference docs
├── personal/
│   ├── finance/
│   ├── health/
│   ├── misc/
│   └── tax/
├── study/
│   ├── concepts/         ← Zettelkasten notes
│   ├── MOCs/             ← Maps of Content
│   └── sources/          ← Books, articles, courses
├── templates/            ← Note templates
├── prompts/              ← AI skill instructions
├── attachments/          ← Images, files
└── Designs/              ← Symlink to design files
```

## Folder Guide

### `work/daily-notes/`
**One file per day.** Named `YYYY-MM-DD.md`. Captures priorities, tasks, meetings, decisions, blockers, and wins. This is the **source of truth** — everything else aggregates from here.

### `work/weekly-reviews/`
**One file per week.** Named `YYYY-WXX.md`. Auto-generated from daily notes. Summarizes wins, decisions, blockers, initiative progress, and carry-over tasks.

### `work/initiatives/`
**One file per strategic initiative.** Named by initiative title. Tracks phase, health, stakeholders, milestones, decisions, risks, and progress. Can sync to Confluence.

### `work/performance/`
**One file per review cycle.** Named like `FY27-H1-Review.md`. Auto-aggregates `#win` entries and decisions from daily notes via Dataview. Used for year-end reviews.

### `work/scratchpad/`
**Quick-capture for anything.** Ideas, POCs, team contributions, investigations, tooling experiments. Lightweight notes that may graduate into initiatives.

### `work/reference/`
**Static reference docs.** Architecture notes, runbooks, team processes — things you look up but don't update daily.

### `study/concepts/`
**Zettelkasten notes.** One concept per file. Atomic, linked, in your own words. Each note connects to others via `[[wikilinks]]`.

### `study/MOCs/`
**Maps of Content.** Index pages that organize concepts by domain (e.g., `Distributed Systems.md` linking to all related concepts).

### `study/sources/`
**Where you learned things.** Books, courses, articles, videos. Linked from concept notes.

### `personal/`
**Non-work notes.** Finance, health, tax, misc. Intentionally minimal structure — organize as needed.

### `templates/`
**Note templates.** Used by Templater plugin and Wibey skills. Don't create notes here — this folder is only for templates.

### `prompts/`
**AI workflow instructions.** Each file defines a skill that Wibey executes. Don't edit unless you're changing a workflow.

### `attachments/`
**Images and files.** Obsidian auto-saves pasted images here. Referenced via `![[image.png]]`.

## Naming Conventions

| Folder | File Name Format | Example |
|--------|-----------------|---------|
| daily-notes | `YYYY-MM-DD.md` | `2026-02-20.md` |
| weekly-reviews | `YYYY-WXX.md` | `2026-W08.md` |
| initiatives | `Title Case.md` | `Express Delivery Badge.md` |
| performance | `Cycle-Review.md` | `FY27-H1-Review.md` |
| scratchpad | `kebab-case.md` | `api-caching-idea.md` |
| concepts | `Title Case.md` | `Circuit Breaker Pattern.md` |

## Data Flow

```
Daily Notes (daily input)
    ↓
Weekly Reviews (weekly aggregation)
    ↓
Performance Reviews (cycle aggregation via Dataview)

Daily Notes → Initiative mentions → Initiative Progress Log
Initiative Notes → Confluence sync
Scratchpad → may graduate to Initiative
```

## Key Tags

| Tag | Purpose | Used In |
|-----|---------|---------|
| `#win` | Marks an accomplishment | Daily notes → auto-rolls up to Performance |
| `#daily` | Daily note type | Daily notes |
| `#initiative` | Initiative type | Initiative notes |
| `#concept` | Learning note | Study concepts |
| `#scratchpad` | Ad-hoc work | Scratchpad notes |
