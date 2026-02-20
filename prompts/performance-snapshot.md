---
description: Extracts wins, decisions, and impact from daily notes into the performance review doc
trigger: "performance snapshot" or "capture wins"
tools: vault (read/write)
template: templates/performance-review.md (for new review docs only)
output: work/performance/<cycle>-Review.md
vault_path: /Users/p0d00wj/notes
---

# Performance Snapshot

## Steps

1. **Find the review doc** in `work/performance/` (e.g., `FY27-H1-Review.md`). If none exists, ask the user for the cycle name and create one from `templates/performance-review.md`.

2. **Determine scan range** — From the review doc's `updated:` date to today. If first run, ask: "How far back should I look?"

3. **Scan daily notes** in range. Extract:
   - `#win` entries → Key Achievements
   - `## Decisions` entries → Decisions Made
   - `[[Initiative]]` mentions → cross-reference with `work/initiatives/` for outcomes
   - Resolved blockers → evidence of problem-solving

4. **Scan initiative notes** in `work/initiatives/`. Extract:
   - Milestones hit during the period
   - User's role and contributions

5. **Update the review doc**:
   - **Key Achievements** — Append wins with format: `**YYYY-MM-DD** — [Win] → [Impact]`
   - **Initiatives Led / Contributed To** — Update table with latest outcomes
   - **Technical Leadership** — Add architecture decisions, reviews, mentoring from daily notes
   - **Collaboration** — Add cross-team mentions
   - **Frontmatter** — Set `updated:` to today

6. **Save** the updated file.

## Confirm
```
Performance updated: work/performance/<cycle>-Review.md
  Scanned: X daily notes | Wins added: X | Initiatives: X
```
