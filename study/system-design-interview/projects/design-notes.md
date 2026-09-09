---
type: sysdesign-design-notes
parent: "[[README]]"
notes_total: 6
created: 2026-08-11
tags: [study, system-design, project, design-note]
---

# Design Notes — The Billion-User Chapters

> These 6 chapters are **massive-scale problems** that a single Mac mini serving ~5 family
> users will never actually exercise. Instead of building them, you write a **≤1-page note**
> answering: *"What would I add to my site, and what pain forces it?"*
>
> Do the note in the chapter's 2nd week (after the diagram). Keep it short. The value is
> connecting the book's theory to *your* concrete system, not writing an essay.

---

## Ch 5 — Consistent Hashing
> Week **W7-8 (Nov 9-22, 2026)** · 📝 Design note

**Prompt:** Your site has one origin. When would you need consistent hashing?

Answer briefly:
- If the family wall / short-links DB outgrew one box and you sharded across N nodes, how do
  you map a key → node so that adding/removing a node reshuffles minimal data?
- Sketch the hash ring + virtual nodes for *your* short-link codes.
- What pain forces it: naive `hash(key) % N` remaps almost everything when N changes.

**Your note:**
-

---

## Ch 7 — Unique ID Generator
> Week **W11-12 (Dec 14-20, 2026 + Jan 11-17, 2027)** · 📝 Design note

**Prompt:** What generates primary keys in your DB today, and when would that break?

Answer briefly:
- Today: SQLite/Postgres auto-increment (single box → fine).
- Short-link codes: base62 of what? (auto-inc id vs random vs hash)
- If you sharded writes across machines, why does auto-increment break, and would you reach
  for Snowflake? Draw the 64-bit layout: `[timestamp][datacenter][machine][sequence]`.

**Your note:**
-

---

## Ch 9 — Web Crawler
> Week **W15-16 (Feb 8-21, 2027)** · 📝 Design note *(optional build: crawl your own site → sitemap)*

**Prompt:** You don't need a web-scale crawler. But the sub-problems apply.

Answer briefly:
- The URL frontier (BFS + politeness) — where does a similar queue appear in *your* system?
  (e.g. the notification queue in M7).
- Content dedup via hashing — same idea as short-link collision detection.
- **Optional 20-min build:** a tiny script that crawls your own site and emits `sitemap.xml`.

**Your note:**
-

---

## Ch 11 — News Feed
> Week **W19-20 (Mar 8-21, 2027)** · 📝 Design note

**Prompt:** If the family wall became a real "family updates feed", how would you build it?

Answer briefly:
- Fan-out on write vs fan-out on read — for ~5 family members, which is simpler and why?
  (At this scale, fan-out on read / just query is fine — note *when* fan-out-on-write wins.)
- Where would a cache sit in the feed retrieval path?

**Your note:**
-

---

## Ch 13 — Search Autocomplete
> Week **W23-24 (Apr 5-18, 2027)** · 📝 Design note *(optional build: trie autocomplete)*

**Prompt:** Autocomplete over your site's content (short links, wall posts).

Answer briefly:
- Trie structure + top-k — how would you index your short-link codes or page titles?
- Offline trie rebuild vs live update — which fits a low-traffic site?
- **Optional 30-min build:** a tiny in-memory trie that autocompletes your page titles.

**Your note:**
-

---

## (Bonus context) Why these stay as notes

The book's diagram test still applies — **draw** these architectures from memory for the
interview. You just don't *build* them, because your project can't create the pain
(billions of keys, celebrity fan-out, web-scale crawling) that justifies the machinery.
Building them anyway would be cargo-culting. A crisp "here's when I'd add it" note is the
honest, senior answer.

---

*Back to [[README]] · [[../study-plan]]*
