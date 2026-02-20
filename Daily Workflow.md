---
type: reference
created: 2026-02-20
tags:
  - reference
---

# Daily Workflow

> How to use this vault day-to-day.

## Morning (2 min)

1. Open Wibey CLI
2. Say: **"create my daily note"**
3. It auto-creates today's note with calendar + yesterday's carry-over
4. Open the note in Obsidian → review priorities and meetings

## During the Day

**As things happen, jot them in today's daily note:**

| What Happened | Where to Write It |
|---------------|-------------------|
| Completed a task | Check off `- [x]` under Priorities or Tasks |
| Made a decision | Add a bullet under `## Decisions` with `[[Initiative]]` link |
| Hit a blocker | Add under `## Blockers` |
| Shipped something / had impact | Add under `## Wins` with `#win` tag |
| Had a meeting | Fill in the meeting block — Notes + Action Items |
| Random thought / idea | Add under `## Notes / Inbox` (sort later) |
| Ad-hoc work / helping someone | Tell Wibey: "new scratchpad [topic]" |

**Key habits:**
- Tag wins with `#win` — this is how they auto-roll up to your performance review
- Use `[[Initiative Name]]` wikilinks when something relates to an initiative
- Unchecked tasks auto-carry to tomorrow's note

## End of Day (1 min)

1. Scan your note — anything missed?
2. Unfinished tasks stay as `- [ ]` — they'll carry over tomorrow
3. If you made initiative progress, tell Wibey: **"update initiative [name]"**

## Friday / Weekend (5 min)

1. Tell Wibey: **"weekly review"**
2. It aggregates all 5 daily notes into a weekly summary
3. Add any learnings and next-week priorities

## Every 1-2 Weeks

1. Tell Wibey: **"performance snapshot"**
2. It pulls `#win` entries and decisions into your review doc
3. Check `work/performance/Wins Dashboard.md` in Obsidian to see the Dataview rollup

## When Starting a New Initiative

1. Create manually in Obsidian using the initiative template, OR
2. Tell Wibey: **"update initiative [name]"** — if the file doesn't exist, it will offer to create one

## When Learning Something New

1. Tell Wibey: **"I learned about [topic]"**
2. Explain in your own words — it creates a Zettelkasten concept note
3. It auto-links to related concepts and updates the MOC

## Quick Obsidian Navigation

| Want to... | Do this |
|------------|---------|
| Find any note fast | `Cmd + O` → type name |
| Search across all notes | `Cmd + Shift + F` → type keyword |
| See backlinks | Click the backlinks icon in right sidebar |
| See today's note | `Cmd + O` → type today's date |
| Browse a folder | Use the file explorer in left sidebar |
