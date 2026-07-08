---
type: dashboard
created: 2026-02-26
updated: 2026-07-04
tags:
  - dashboard
  - study
---

# 📚 Study Dashboard

> Two active paths. Open trackers on Sunday.

---

## 🛤️ Study Paths

```dataview
TABLE WITHOUT ID
  file.link AS "Path",
  topic AS "Topic",
  status AS "Status",
  weeks_completed + " / " + weeks_total AS "Weeks",
  hours_logged AS "Hours"
FROM "study"
WHERE type = "study-path-tracker"
SORT file.name ASC
```

---

## 🔗 Quick Links

| | Link |
|---|------|
| 📖 Study Plan | [[study/Study Plan]] |
| 🤖 AI Engineering Path | [[study/ai-engineering-path/README]] |
| 📐 System Design Interview | [[study/system-design-interview/README]] |

---

*Back to [[Home]]*
