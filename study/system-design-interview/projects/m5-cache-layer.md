---
type: sysdesign-milestone
milestone: 5
chapter: 6
parent: "[[README]]"
weeks: "W9-10 (Nov 23 - Dec 6, 2026)"
original_target: "W9-10 (Oct 12-25)"
track: build
status: not-started
created: 2026-08-11
tags: [study, system-design, project, milestone]
---

# M5 — Add a Cache Layer to One Endpoint

> **Ch 6: Design a Key-Value Store** · Weeks **W9-10 (Nov 23 - Dec 6, 2026)** · 🔨 Build (light)
> You won't build a distributed KV store (that's a billion-user problem — see the design
> note). But you *will* add a real cache in front of a DB call and feel the read path.

---

## 🎯 What I'm shipping

A cache layer (Redis, or SQLite-backed in-memory) in front of one dynamic endpoint on the
site, so a repeated read is served from cache instead of the DB. You'll measure the difference.

---

## ✅ Acceptance criteria

- [ ] One endpoint reads through a cache (cache hit path + DB fallback path)
- [ ] Cache miss populates the cache; second request is a hit
- [ ] Log/measure latency: cache HIT vs MISS
- [ ] TTL or invalidation strategy chosen and documented
- [ ] `docs/caching.md`: read path, write path, eviction, why quorum/replication is overkill here

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W9 | Read Ch 6 (CAP, partitioning, replication). Add cache to one endpoint. | ⬜ |
| W10 | Read Ch 6 rest (consistency, gossip, Merkle). Measure HIT vs MISS. Draw diagram. | ⬜ |

---

## 🧠 Concept ↔ reality

| Book concept | In this project |
|--------------|-----------------|
| Read path (memtable → Bloom filter → SSTable) | Your cache → DB fallback (same shape, simpler) |
| Cache-aside pattern | Exactly what you're implementing |
| CAP / quorum (W+R>N) | **Overkill for one box** — design-note it, don't build it |
| TTL / eviction | Real decision you'll make and document |

---

## 📊 Numbers

- Latency cache HIT:
- Latency cache MISS (DB):
- Speedup:
- TTL chosen + why:

---

## 📝 Post-milestone note

**What worked:**
**One thing I can defend in an interview:**

---

*Back to [[README]] · Prev: [[m4-rate-limiter]] · Next: [[m6-short-links]]*
