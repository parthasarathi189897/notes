---
description: Updates an initiative one-pager with recent progress from daily notes and user context
trigger: "update initiative [name]"
tools: vault (read/write)
template: templates/initiative.md (for new initiatives only)
output: work/initiatives/<name>.md
vault_path: /Users/p0d00wj/notes
---

# Initiative Updater

## Steps

1. **Find the initiative** in `work/initiatives/`. If ambiguous, list available files and ask user to pick.

2. **Scan last 7 daily notes** from `work/daily-notes/` for mentions of this initiative (by name or `[[wikilink]]`). Extract relevant decisions, blockers, wins, and meeting notes.

3. **Ask the user**: "What's the latest on this? Any phase/health changes or new risks?" (skip if daily notes already cover it)

4. **Update the initiative note** — preserve the visual structure with callouts and emoji:
   - **Progress Log** (`## 📈 Progress Log`) — Add dated `### YYYY-MM-DD` entry (latest first) with bullets from daily notes + user input. Link back with `[[YYYY-MM-DD]]`.
   - **Decisions** (`## 📌 Decisions`) — Add new rows to the table if decisions found
   - **Milestones** (`## 🗺️ Milestones`) — Update status emoji (⬜ / 🔵 / ✅ / ⏸️ / 🔴)
   - **Risks & Blockers** (`## ⚠️ Risks & Blockers`) — Add new rows
   - **References** (`## 🔗 References`) — Add new links if user shares Confluence, Figma, PR, or design links (inside the `> [!note]-` callout)
   - **Frontmatter** — Set `updated:` to today. Update `phase:` and `health:` (emoji format: `"🟢 Green"`, `"🟡 Yellow"`, `"🔴 Red"`) if changed.
   - **Status bar** — Update the `> [!multi-column]` block values if phase/health/priority changed

5. **Save** the updated file.

## New Initiative

If the file doesn't exist, create from `templates/initiative.md` using Templater syntax, then fill with whatever context is available.

## Confirm
```
Updated: work/initiatives/<name>.md
  Progress entries: X | Decisions: X | Phase: unchanged/changed
```
