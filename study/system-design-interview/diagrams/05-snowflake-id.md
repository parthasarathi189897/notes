---
type: sysdesign-diagram
chapter: 7
system: "Snowflake ID (Bit Layout)"
first_drawn: ""
can_redraw: false
confidence: ""
created: 2026-05-31
tags: [study, system-design, diagram]
---

# Diagram: Snowflake ID Bit Layout

> Draw this after completing [[../weeks/week-12]].

---

## What to draw

```
[1 bit unused][41 bits timestamp][5 bits datacenter][5 bits machine][12 bits sequence]
 = 64 bits total
```

Show how this enables sorted, distributed, unique IDs without coordination.

---

## Components checklist

- [ ] 64-bit ID total
- [ ] 1 bit: unused (sign bit)
- [ ] 41 bits: millisecond timestamp (~69 years)
- [ ] 5 bits: datacenter ID (32 datacenters)
- [ ] 5 bits: machine ID (32 machines per DC)
- [ ] 12 bits: sequence number (4096 per ms per machine)
- [ ] Arrow showing time-sortable property
- [ ] Note: no coordination needed between machines

---

## Excalidraw drawing

> Create `05-snowflake-id.excalidraw.md` in this folder, then it renders here automatically.

![[05-snowflake-id.excalidraw]]

---

## Draw log

| Date | From memory? | Time | Gaps |
|------|:------------:|------|------|
| | | | |
| | | | |

---

*Back to [[../progress-tracker]] · Related: [[../weeks/week-12]]*
