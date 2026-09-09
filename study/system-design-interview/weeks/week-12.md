---
type: sysdesign-week
week: 12
chapter: 7
dates: "Jan 11-17, 2027"
original_target: "Dec 14-20, 2026"
book_section: "Ch 7: Snowflake bit layout"
diagram: "[[../diagrams/05-snowflake-id]]"
status: not-started
created: 2026-05-31
tags: [study, system-design, weekly]
---

# Week 12 — Ch 7: Unique ID Generator (Part 2) + Diagram

> Dates: **Jan 11-17, 2027**
> Read: Finish Ch 7 — Snowflake deep dive
> Draw: [[../diagrams/05-snowflake-id]]
>
> 📝 Project: [[../projects/design-notes#ch-7-unique-id|📝 Design note — DB PK strategy]] (Ch 7)
>
> 🎯 Deeper dive: [Unique ID Generator — Snowflake Algorithm](https://www.youtube.com/watch?v=g3BV_holJK4) — full bit layout + clock-skew problem.

---

## 🎯 This week's focus

- [ ] Finish Ch 7: Snowflake implementation details
- [ ] **Draw Snowflake ID bit layout from memory**

---

## ✅ Done when

> The single checkable condition for this slot. Approved 2026-09-07.
> A written note is not a shipped artifact.

- [ ] Design note written: Snowflake vs UUID for your own DB keys.

---

## 📝 Reading notes

### Snowflake bit layout
```
[1 bit unused][41 bits timestamp][5 bits datacenter][5 bits machine][12 bits sequence]
```

### Why this layout enables distributed unique sorted IDs
-

---

## 🎨 Diagram attempt

- [ ] Drew bit layout from memory
- Sections I forgot:
- Time taken:

---

## 📓 Session log

### Session 1 — _date_
- **Duration:**
- **Did:**
- **Learned:**

---

*Prev: [[week-11]] · Back to [[../progress-tracker]] · Next: [[week-13]]*
