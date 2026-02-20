---
date: <% tp.date.now("YYYY-MM-DD") %>
day: <% tp.date.now("dddd") %>
type: daily-note
tags:
  - daily
---

# <% tp.date.now("dddd, MMMM D, YYYY") %>

## Priorities
> Top 3 things to accomplish today. Mark with `[[Initiative]]` if applicable.

- [ ]
- [ ]
- [ ]

## Tasks

- [ ]

### Carried Over
> From last working day. Auto-populated by the daily note skill.



## Meetings

> One sub-section per meeting. Delete this block if no meetings.

### Meeting Name
- **Time:**
- **Attendees:**
- **Notes:**
  -
- **Action Items:**
  - [ ]

## Decisions
> Tag with `[[Initiative]]` for rollup.

-

## Blockers

-

## Wins
> Tag with `#win` for performance review rollup.

-

## Notes / Inbox
> Quick capture — sort later.

-

---
*Previous: [[PREV_DATE]] | Next: [[NEXT_DATE]]*
%%PREV_DATE = most recent daily note before today (auto-filled by skill). NEXT_DATE = next weekday.%%
