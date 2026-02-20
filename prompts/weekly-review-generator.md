---
description: Generates weekly review by aggregating Mon-Fri daily notes
trigger: "weekly review" or "summarize my week"
tools: vault (read/write)
template: templates/weekly-review.md
output: work/weekly-reviews/YYYY-WXX.md
vault_path: /Users/p0d00wj/notes
---

# Weekly Review Generator

## Steps

1. **Determine week range** — Default: current Mon–Fri. If user specifies a different week, use that.

2. **Read all daily notes** for the week from `work/daily-notes/`. Extract per day:
   - `## Wins` entries (tagged `#win`)
   - `## Decisions` entries
   - `## Blockers` entries
   - Checked `- [x]` tasks (completed)
   - Unchecked `- [ ]` tasks from Friday (carry-over)
   - `[[Initiative]]` mentions

3. **Read template** from `templates/weekly-review.md`. Fill in:
   - **Highlights** — Synthesize top 3 from wins + decisions
   - **Wins** — Aggregated from all days
   - **Decisions** — Aggregated from all days
   - **Blockers** — Note which are resolved vs open
   - **Initiative Progress** — One row per initiative mentioned, summarize week's progress
   - **Completed** — Key completed tasks (plain bullets, not checkboxes)
   - **Carry-Over** — Unchecked tasks from last daily note of the week

4. **Ask the user**: "Any learnings or priorities for next week?" (skip if user says none)

5. **Save** to `work/weekly-reviews/YYYY-WXX.md`

## Confirm
```
Weekly review created: work/weekly-reviews/YYYY-WXX.md
  Days: X | Wins: X | Carry-over: X
```
