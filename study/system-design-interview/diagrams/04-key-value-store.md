---
type: sysdesign-diagram
chapter: 6
system: "Key-Value Store"
first_drawn: ""
can_redraw: false
confidence: ""
created: 2026-05-31
tags: [study, system-design, diagram]
---

# Diagram: Key-Value Store

> Draw this after completing [[../weeks/week-10]].

---

## What to draw

Coordinator → partitioned nodes (hash ring) → replication across N nodes → write path (commit log → memtable → SSTable) → read path (memtable → Bloom filter → SSTables). Label consistency model (quorum: W + R > N).

---

## Components checklist

- [ ] Coordinator node
- [ ] Partitioned nodes on hash ring
- [ ] Replication to N nodes
- [ ] Write path: commit log → memtable → SSTable flush
- [ ] Read path: memtable → Bloom filter → SSTables
- [ ] Quorum notation (W + R > N)
- [ ] Gossip protocol (failure detection)
- [ ] Merkle tree (anti-entropy repair)

---

## Excalidraw drawing

> Create `04-key-value-store.excalidraw.md` in this folder, then it renders here automatically.

![[04-key-value-store.excalidraw]]

---

## Draw log

| Date | From memory? | Time | Gaps |
|------|:------------:|------|------|
| | | | |
| | | | |

---

*Back to [[../progress-tracker]] · Related: [[../weeks/week-10]]*
