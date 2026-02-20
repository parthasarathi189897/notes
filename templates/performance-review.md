---
type: performance-review
cycle:
period_start:
period_end:
created: <% tp.date.now("YYYY-MM-DD") %>
updated: <% tp.date.now("YYYY-MM-DD") %>
tags:
  - performance
  - review
---

# Performance Review — <% tp.file.title %>

## Goals & Objectives

| # | Goal | Metric | Target | Actual | Status |
|---|------|--------|--------|--------|--------|
| 1 |      |        |        |        |        |
| 2 |      |        |        |        |        |
| 3 |      |        |        |        |        |

## Impact Summary
> High-level narrative of your impact this cycle.



## Key Achievements (Auto-Aggregated)
> Pulls all `#win` entries from daily notes in this period.

```dataview
TABLE date
FROM "work/daily-notes"
WHERE contains(file.content, "#win") AND date >= this.period_start AND date <= this.period_end
SORT date DESC
```

## Decisions Made (Auto-Aggregated)
> Key decisions you drove or influenced.

```dataview
TABLE date
FROM "work/daily-notes"
WHERE contains(file.content, "## Decisions") AND date >= this.period_start AND date <= this.period_end
SORT date DESC
```

## Initiatives Led / Contributed To

| Initiative | Role | Outcome | Impact |
|------------|------|---------|--------|
|            |      |         |        |

## Technical Leadership
> Architecture decisions, code reviews, mentoring, tech debt.

-

## Collaboration & Influence
> Cross-team work, stakeholder management, mentoring.

-

## Growth Areas
> What to improve next cycle.

-

## Peer Feedback

| From | Context | Feedback |
|------|---------|----------|
|      |         |          |

## Self-Assessment
> Honest reflection on this cycle.


