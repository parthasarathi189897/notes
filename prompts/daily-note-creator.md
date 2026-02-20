---
description: Creates today's daily note with carry-over from most recent previous note and calendar events
trigger: "create my daily note" or "start my day"
tools: msgraph (calendar), vault (read/write)
template: templates/daily-note.md
output: work/daily-notes/YYYY-MM-DD.md
vault_path: /Users/p0d00wj/notes
---

# Daily Note Creator

## Steps

1. **Find and read the most recent previous daily note**
   - List all files in `work/daily-notes/` and sort by filename descending
   - Pick the first file whose date is **before** today (skip today if it already exists)
   - This handles weekends, holidays, and PTO gaps automatically
   - If no previous note exists, skip carry-over
   - From the previous note, extract:
     - Unchecked `- [ ]` tasks (from Priorities, Tasks, and Meeting Action Items) → Carried Over section
     - Unresolved blockers → Blockers section
   - In the Carried Over section, add a reference: `> From [[YYYY-MM-DD]]` using the actual previous note's date (not hardcoded "yesterday")

2. **Check calendar authentication** before fetching:
   - First attempt to fetch calendar: `bun ~/.wibey/skills/msgraph/scripts/calendar.ts today`
   - If authentication fails, ask user: "Calendar authentication expired. Would you like to refresh login for automatic calendar integration?"
     - If YES: Instruct user to run `bun ~/.wibey/skills/msgraph/scripts/auth.ts login` then re-run daily note creation
     - If NO: Skip calendar fetch and add comment `<!-- Calendar fetch skipped — add meetings manually -->`

3. **Fetch today's calendar** via msgraph skill (if authenticated):
   ```
   bun ~/.wibey/skills/msgraph/scripts/calendar.ts today
   ```
   - Filter events to include ONLY actual meetings happening today
   - **Skip these calendar events:**
     - Out of office meeting invites (OOO, PTO, leave, vacation)
     - Multi-day or all-day events (`is_all_day: true`)
     - Lunch or break invites
     - Events not starting on today's date
   - Create one `### Meeting Name` block per event with time pre-filled
   - Convert UTC times to local timezone (PST/PDT)

4. **Ask the user**: "Any priorities or additional tasks for today?" (skip if user says none)

5. **Read template** from `templates/daily-note.md`. Fill in:
   - Frontmatter dates and heading
   - Carried Over from step 1 — prefix with `> From [[YYYY-MM-DD]]` using the actual previous note's date
   - Meetings from step 2/3
   - Priorities from step 4
   - Link initiative names as `[[Initiative Name]]` wikilinks
   - **Previous/Next navigation**: Set `Previous: [[YYYY-MM-DD]]` to the actual previous note date found in step 1 (not yesterday). Set `Next` to the next weekday from today.

6. **Save** to `work/daily-notes/YYYY-MM-DD.md`

## Confirm
```
Daily note created: work/daily-notes/YYYY-MM-DD.md
  Meetings: X | Carried over: X tasks
```
