---
type: weekly-review
week: <% tp.date.now("YYYY-[W]WW") %>
week_start: <% tp.date.now("YYYY-MM-DD", 0, tp.date.now("YYYY-MM-DD", -(tp.date.now("d")-1))) %>
week_end: <% tp.date.now("YYYY-MM-DD", 0, tp.date.now("YYYY-MM-DD", -(tp.date.now("d")-5))) %>
created: <% tp.date.now("YYYY-MM-DD") %>
tags:
  - weekly-review
---

# Weekly Review — <% tp.date.now("YYYY-[W]WW") %>

## Highlights
> Top 3 things that stood out this week.

1.
2.
3.

## Wins

-

## Decisions
> Key decisions made or influenced.

-

## Blockers & Challenges

-

## Initiative Progress

| Initiative | Status | Key Progress | Next Steps |
|------------|--------|-------------|------------|
|            |        |             |            |

## Completed

-

## Carry-Over
> What didn't get done?

- [ ]

## Learnings

-

## Next Week Focus

1.
2.
3.

---
*Previous: [[<% tp.date.now("YYYY-[W]WW", -7) %>]] | Next: [[<% tp.date.now("YYYY-[W]WW", 7) %>]]*
