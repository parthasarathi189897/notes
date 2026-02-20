---
type: dashboard
created: 2026-02-19
updated: 2026-02-19
tags:
  - performance
  - dashboard
---

# Wins Dashboard

> Auto-aggregated from daily notes using Dataview. No manual updates needed — just tag your wins with `#win` in daily notes.

---

## Recent Wins (Last 30 Days)

```dataview
TABLE WITHOUT ID
  file.link AS "Day",
  date AS "Date"
FROM "work/daily-notes"
WHERE contains(file.content, "#win") AND date >= date(today) - dur(30 days)
SORT date DESC
```

## All Wins This Quarter

```dataview
TABLE WITHOUT ID
  file.link AS "Day",
  date AS "Date"
FROM "work/daily-notes"
WHERE contains(file.content, "#win") AND date >= date(today) - dur(90 days)
SORT date DESC
```

## Decisions Made (Last 30 Days)

```dataview
TABLE WITHOUT ID
  file.link AS "Day",
  date AS "Date"
FROM "work/daily-notes"
WHERE contains(file.content, "## Decisions") AND date >= date(today) - dur(30 days)
SORT date DESC
```

## Active Initiatives

```dataview
TABLE WITHOUT ID
  file.link AS "Initiative",
  status AS "Status",
  phase AS "Phase",
  health AS "Health",
  updated AS "Last Updated"
FROM "work/initiatives"
WHERE type = "initiative" AND status = "active"
SORT updated DESC
```

---

## How to Use This Dashboard

1. **Tag wins daily** — Add `#win` in your daily note's Wins section
2. **Log decisions** — Fill the Decisions table in daily notes
3. **Review weekly** — Glance at this dashboard during weekly reviews
4. **Performance review** — Use this as a source when filling your review doc
5. **Tip:** Click any "Day" link to jump to that daily note for full context
