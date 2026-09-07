---
type: study-path-plan
parent: "[[README]]"
total_weeks: 37
study_weeks: 26
buffer_weeks: 11
minutes_per_week: 30
book: "System Design Interview Vol 1 — Alex Xu (2nd edition)"
start_date: 2026-08-17
study_starts: 2026-08-31
target_end: 2027-05-02
created: 2026-05-31
updated: 2026-08-11
tags:
  - study
  - system-design
  - plan
---

# Study Plan — System Design Interview

> 13 chapters. 26 study weeks. **Study starts Aug 31, 2026** (after the Aug trip). 30 min/week active + passive commute videos.
> 🧳 **Travel-aware:** protected 2-week travel blocks cover your real trips (Aug 17-30, Sep 21 – Oct 4), plus a 🪔 Diwali week (Nov 2-8) and a 🎄 2-week year-end break (Dec 28 – Jan 10). You won't be trying to read a chapter while on a plane.
> 🆕 Each chapter also has a hands-on milestone in the [[projects/README|Family-Website Project Track]]
> — build the buildable chapters, design-note the billion-user ones.
>
> ⚠️ **Re-planned 2026-08-11.** Same 30 min/week pace — only added travel/holiday buffers and re-dated. New end: **~May 2, 2027** (was Feb 28). [[progress-tracker]] is the source of truth for dates.

---

## ⏱️ Time budget

```
Active:   30 min/week (Saturday, after AI study)
Passive:  15-20 min commute/walk (Mon-Fri, any day)
Total:    ~50 min/week effective — but only 30 min "costs" you
```

**Cadence per chapter (2 weeks):**

| Week | Active (30 min) | Passive (commute) |
|------|-----------------|-------------------|
| Week A | Read chapter (first half) | Watch ByteByteGo video |
| Week B | Finish chapter + draw architecture from memory | Re-watch video or blog post |

**The diagram test:** Close the book. Open Excalidraw or grab paper. Draw the full architecture. If you can't → re-read that section. If you can → you own it.

---

## 📚 The 13 chapters + videos

> Every video below is from **ByteByteGo YouTube** unless marked otherwise.
> Search the title on [youtube.com/@ByteByteGo](https://www.youtube.com/@ByteByteGo).

---

### ✈️ Travel Buffer 1 — Aug 17-30 (2 weeks · 🧳 Aug trip Aug 17-26)

> 🧳 **You're traveling — the plan doesn't start until you're back.** 0h. Optional: watch the Ch 1 ByteByteGo scaling video on the plane/commute if you're bored, but no reading. Study begins W1 on **Aug 31**.

---

### Ch 1 — Scale From Zero To Millions Of Users (W1-2)

**Core concepts:** Vertical vs horizontal scaling, load balancer, CDN, database replication, cache, message queue, database sharding.

| Week | Dates | Active (30 min) | Passive (commute) |
|------|-------|-----------------|-------------------|
| W1 | Aug 31 - Sep 6 | Read Ch 1 (first half: single server → load balancer → DB replication) | 🎬 [Vertical Vs Horizontal Scaling](https://www.youtube.com/watch?v=dvRFHG2-uYs) — ByteByteGo |
| W2 | Sep 7-13 | Finish Ch 1 (cache → CDN → sharding → summary) + **draw full architecture** | 🎬 [What is a CDN?](https://www.youtube.com/watch?v=RI9np1LWzqw) — ByteByteGo |

**Diagram to draw from memory:** Single user → web tier + data tier → load balancer → DB replication → cache layer → CDN → message queue → sharding. Label each component and explain *why* it's added.

> 🎯 **Deeper dive (if BBG felt shallow):** Gaurav Sen — [Load Balancing & Database Replication](https://www.youtube.com/watch?v=chh49EUiebg) (search his channel @gkcs for the full "Scalability" video). He derives *why* each tier is added.

---

### Ch 2 + Ch 3 — Estimation + Interview Framework (W3-4)

**Core concepts:** QPS estimation, storage estimation, bandwidth. The 4-step framework: understand → propose → deep dive → wrap up.

| Week | Dates | Active (30 min) | Passive (commute) |
|------|-------|-----------------|-------------------|
| W3 | Sep 14-20 | Read Ch 2: back-of-envelope estimation. Practice 2 estimation problems. | 🎬 [Back-Of-The-Envelope Estimation](https://www.youtube.com/watch?v=UC5xf8FbdJc) — ByteByteGo |
| W4 | Oct 5-11 | Read Ch 3: interview framework. Write the 4 steps on an index card. | 🎬 [System Design Interview: Step-By-Step](https://www.youtube.com/watch?v=i7twT3x5yv8) — ByteByteGo |

**Key numbers to memorize:**
```
QPS:     1 million requests/day ≈ 12 QPS
Storage: 1 million users × 1KB = 1GB
         1 billion users × 10KB = 10TB
Memory:  80/20 rule — cache 20% of daily requests
```

> 💡 **Extra (optional):** Bookmark Jeff Dean's "Latency Numbers Every Programmer Should Know" — it's the foundation of all estimation questions.

> 🎯 **Deeper dive (W3):** [System Design Basics: Back Of The Envelope Estimation](https://www.youtube.com/watch?v=AsJJGe5vxFM) — worked numeric examples end-to-end.
> 📝 **Note (W4):** For the framework, ByteByteGo's [Step-by-Step Guide](https://www.youtube.com/watch?v=i7twT3x5yv8) is genuinely strong — no swap needed here.

---

### ✈️ Travel Buffer 2 — Sep 21 – Oct 4 (2 weeks · 🧳 Sep trip Sep 25 – Oct 4)

> 🧳 **Second trip.** 0h. Ch 3 (framework) wraps in W3 just before you leave; Ch 4 waits until W4 on **Oct 5** when you're back. Optional commute video only.

---

### Ch 4 — Design A Rate Limiter (W5-6)

**Core concepts:** Token bucket, leaking bucket, fixed window, sliding window log, sliding window counter. Where to put the rate limiter (client, server, middleware).

| Week | Dates | Active (30 min) | Passive (commute) |
|------|-------|-----------------|-------------------|
| W5 | Oct 12-18 | Read Ch 4 (first half: algorithms — token bucket, sliding window) | 🎬 [Rate Limiting — System Design](https://www.youtube.com/watch?v=YXkOdWBwqaA) — ByteByteGo |
| W6 | Oct 19-25 | Finish Ch 4 (distributed rate limiter, race conditions) + **draw architecture** | Re-watch |

**Diagram to draw:** Client → API gateway (rate limiter middleware) → Redis counter → rules engine → response (429 or pass-through). Show the token bucket algorithm flow.

> 🎯 **Deeper dive (read):** BBG's video is fine here; for the algorithm trade-offs (token bucket vs sliding window vs fixed window, Redis race conditions) read [Arcjet — Rate Limiting Algorithms](https://blog.arcjet.com/rate-limiting-algorithms-token-bucket-vs-sliding-window-vs-fixed-window/).

---

### Ch 5 — Design Consistent Hashing (W7-8)

**Core concepts:** Hash ring, virtual nodes, server addition/removal, data rebalancing.

| Week | Dates | Active (30 min) | Passive (commute) |
|------|-------|-----------------|-------------------|
| W7 | Oct 26 - Nov 1 | Read Ch 5 (hash ring, naive approach vs consistent hashing) | 🎬 [Consistent Hashing](https://www.youtube.com/watch?v=UF9Iqmg94tk) — ByteByteGo |
| 🪔 BD | Nov 2-8 | **Diwali break — 0h.** Festival + family. Rest. | — |
| W8 | Nov 9-15 | Finish Ch 5 (virtual nodes, real-world usage) + **draw hash ring** | 🎬 [Consistent Hashing — Gaurav Sen](https://www.youtube.com/watch?v=zaRkONvyGr8) ⚠️ *Non-Alex-Xu — better virtual node animation* |

> 🪔 **Diwali (Nov 2-8) lands mid-chapter.** Read the first half of Ch 5 before the festival (W7), then finish + draw after (W8). Don't force study during Diwali.

**Diagram to draw:** Hash ring with servers + virtual nodes. Show what happens when a server is added/removed. Show key-to-server mapping.

> ⚠️ **Gaurav Sen recommended here** because his animation of virtual node distribution is more intuitive than the book's static diagrams.
> 🎯 **Deeper dive:** [Gaurav Sen — What is Consistent Hashing and Where is it used?](https://www.youtube.com/watch?v=zaRkONvyGr8) (already your primary pick for this chapter).

---

### Ch 6 — Design A Key-Value Store (W9-10)

**Core concepts:** CAP theorem, data partitioning, replication, consistency, gossip protocol, Merkle tree, write path, read path.

| Week | Dates | Active (30 min) | Passive (commute) |
|------|-------|-----------------|-------------------|
| W9 | Nov 16-22 | Read Ch 6 (first half: CAP theorem, partitioning, replication) | 🎬 [CAP Theorem Simplified](https://www.youtube.com/watch?v=BHqjEjzAicA) — ByteByteGo |
| W10 | Nov 23-29 | Finish Ch 6 (consistency, failure handling, gossip, Merkle tree) + **draw architecture** | 🎬 [How Key-Value Stores Work](https://www.youtube.com/watch?v=Dwt8R0KPu7k) — ByteByteGo |

**Diagram to draw:** Coordinator → partitioned nodes (hash ring) → replication across N nodes → write path (commit log → memtable → SSTable) → read path (memtable → Bloom filter → SSTables). Label consistency model (quorum: W + R > N).

> 🎯 **Deeper dive (read — do this one):** [Martin Kleppmann — "Please stop calling databases CP or AP"](https://martin.kleppmann.com/2015/05/11/please-stop-calling-databases-cp-or-ap.html). It's a **blog post** (not a talk — the plan previously mislabeled it), and it's the canonical correction to how CAP is taught. Read it *after* the BBG CAP video so you have the naive framing to correct.

---

### 🔄 Buffer 1 — Nov 30 - Dec 6

> After Ch 6 (Key-Value Store). Catch up on any chapters you're behind on. Re-draw diagrams that felt weak. Or just rest — you've done 6 chapters.

---

### Ch 7 — Design A Unique ID Generator (W11-12)

**Core concepts:** UUID, database auto-increment, Twitter Snowflake, multi-section ID (timestamp + datacenter + machine + sequence).

| Week | Dates | Active (30 min) | Passive (commute) |
|------|-------|-----------------|-------------------|
| W11 | Dec 7-13 | Read Ch 7 (UUID vs DB auto-increment vs Snowflake tradeoffs) | 🎬 [Design a Unique ID Generator — Ch 7](https://www.youtube.com/watch?v=Ay7A4o4AVr8) |
| W12 | Dec 14-20 | Finish Ch 7 + **draw Snowflake ID bit layout** | Re-watch or blog post |

**Diagram to draw:** Snowflake ID: `[1 bit unused][41 bits timestamp][5 bits datacenter][5 bits machine][12 bits sequence]`. Show how this enables sorted, distributed, unique IDs without coordination.

> 🎯 **Deeper dive:** [Design a Unique ID Generator — Snowflake Algorithm](https://www.youtube.com/watch?v=g3BV_holJK4) — full walkthrough of the bit layout + clock-skew problem.

---

### 🔄 Buffer 2 — Dec 21-27

> After Ch 7. Review Ch 1-7 diagrams. Can you draw all 7 from memory? If not, prioritize the weakest one. (Light week — holidays are near.)

---

### 🎄 Year-end Break — Dec 28 – Jan 10, 2027 (2 weeks)

> 🎄 **Real holiday rest. 0h.** No reading, no diagrams. Ch 8 (URL Shortener) waits until W13 on **Jan 11**. Come back fresh in the new year.

---

### Ch 8 — Design A URL Shortener (W13-14)

**Core concepts:** Hash function, base62 encoding, collision resolution, read-heavy design, 301 vs 302 redirect, analytics.

| Week | Dates | Active (30 min) | Passive (commute) |
|------|-------|-----------------|-------------------|
| W13 | Jan 11-17, 2027 | Read Ch 8 (API design, hash function, base62 vs MD5) | 🎬 [How Does a URL Shortener Work?](https://www.youtube.com/watch?v=HHUi8F_qAXM) — ByteByteGo |
| W14 | Jan 18-24, 2027 | Finish Ch 8 (collision handling, cache, analytics) + **draw architecture** | Re-watch |

**Diagram to draw:** Write path: long URL → hash → check collision → store in DB → return short URL. Read path: short URL → cache lookup → DB fallback → 301 redirect. Show the cache layer (read-heavy = cache-friendly).

> 🎯 **Deeper dive:** [URL Shortener with a FAANG Senior Engineer](https://www.youtube.com/watch?v=tm-SWO9gUAU) — trade-off-driven (301 vs 302, counter vs hash, sync vs async analytics).

---

### Ch 9 — Design A Web Crawler (W15-16)

**Core concepts:** BFS traversal, URL frontier, politeness, content dedup (hash), DNS resolver, robustness.

| Week | Dates | Active (30 min) | Passive (commute) |
|------|-------|-----------------|-------------------|
| W15 | Jan 25-31, 2027 | Read Ch 9 (seed URLs, frontier, BFS, content parsing) | 🎬 [Design a Web Crawler](https://www.youtube.com/watch?v=6u25GckPhLU) — ByteByteGo |
| W16 | Feb 1-7, 2027 | Finish Ch 9 (politeness, dedup, fault tolerance) + **draw architecture** | Re-watch |

**Diagram to draw:** Seed URLs → URL frontier (priority queue) → HTML downloader (DNS resolver → fetch) → content parser → dedup (content hash) → URL extractor → URL filter → back to frontier. Show the loop.

> 🎯 **Deeper dive (read):** [Hello Interview — Web Crawler](https://www.hellointerview.com/learn/system-design/answer-keys/web-crawler) — staff-level walkthrough; deepest on URL frontier design + distributed dedup, where BBG is thin.

---

### Ch 10 — Design A Notification System (W17-18)

**Core concepts:** Push notification, SMS, email — different providers. Fan-out, message queue per channel, rate limiting, retry, analytics.

| Week | Dates | Active (30 min) | Passive (commute) |
|------|-------|-----------------|-------------------|
| W17 | Feb 8-14, 2027 | Read Ch 10 (notification types, high-level design) | 🎬 [Design a Notification System — Ch 10](https://www.youtube.com/watch?v=fJkAnN1Ozyw) |
| W18 | Feb 15-21, 2027 | Finish Ch 10 (reliability, dedup, rate limiting) + **draw architecture** | Re-watch |

**Diagram to draw:** Service → notification service → message queues (one per channel: push/SMS/email) → workers → third-party providers (APNs, Twilio, Mailgun) → device/user. Show retry queue and analytics pipeline.

> 🎯 **Deeper dive:** [Notification Service Deep Dive with a Google SWE](https://www.youtube.com/watch?v=TpugGhXhdaU) — covers outbox/CDC pattern, retries, and dead-letter queues.

---

### Ch 11 — Design A News Feed System (W19-20)

**Core concepts:** Fan-out on write vs fan-out on read, feed publishing, feed retrieval, cache, media storage.

| Week | Dates | Active (30 min) | Passive (commute) |
|------|-------|-----------------|-------------------|
| W19 | Feb 22-28, 2027 | Read Ch 11 (feed publishing, fan-out approaches) | 🎬 [News Feeds: Fan-Out, Caching & Scalability](https://www.youtube.com/watch?v=KwgI-VJEr3E) |
| W20 | Mar 1-7, 2027 | Finish Ch 11 (cache, retrieval, optimization) + **draw architecture** | Re-watch |

**Diagram to draw:** Two flows — (1) **Publish:** user posts → web server → fan-out service → write to friends' feed caches. (2) **Retrieve:** user opens feed → feed service → cache → merge + rank → return. Show hybrid: fan-out-on-write for normal users, fan-out-on-read for celebrities.

> 🎯 **Deeper dive:** Search **"Gaurav Sen news feed / Instagram design"** (@gkcs); backup read: [DesignGurus — Social Media News Feed](https://www.designgurus.io/blog/design-social-media-news-feed). Make sure your answer handles the **celebrity threshold** (hybrid), not just fan-out-on-write.

---

### Ch 12 — Design A Chat System (W21-22)

**Core concepts:** WebSocket, connection management, message storage (1:1 vs group), presence/online status, message sync.

| Week | Dates | Active (30 min) | Passive (commute) |
|------|-------|-----------------|-------------------|
| W21 | Mar 8-14, 2027 | Read Ch 12 (WebSocket, 1:1 chat, message flow) | 🎬 [Design A Chat System](https://www.youtube.com/watch?v=okrR1KXNLtA) — ByteByteGo |
| W22 | Mar 15-21, 2027 | Finish Ch 12 (group chat, presence, sync, storage) + **draw architecture** | Re-watch |

**Diagram to draw:** Client ↔ WebSocket ↔ chat service → message queue → message DB (key-value, per-user). Separate: presence service (heartbeat). Show 1:1 vs group message fan-out difference.

> 🎯 **Deeper dive:** Search **"Gaurav Sen WhatsApp System Design"** (@gkcs); backup: [WhatsApp System Design](https://www.youtube.com/watch?v=jN1pnBVIj7M). Deeper on WebSocket handlers + connection routing.

---

### Ch 13 — Design A Search Autocomplete System (W23-24)

**Core concepts:** Trie data structure, top-k queries, data gathering service, query service, trie update vs rebuild.

| Week | Dates | Active (30 min) | Passive (commute) |
|------|-------|-----------------|-------------------|
| W23 | Mar 22-28, 2027 | Read Ch 13 (trie, top-k, query service) | 🎬 [Design Search Autocomplete System](https://www.youtube.com/watch?v=TZ_LSourdUc) |
| W24 | Mar 29 - Apr 4, 2027 | Finish Ch 13 (trie update, scaling, filter layer) + **draw architecture** | Re-watch |

**Diagram to draw:** Two services — (1) **Data gathering:** query logs → aggregation → analytics DB → trie rebuild (offline). (2) **Query service:** user types → trie lookup → return top-k → cache. Show filter layer for inappropriate content.

> 🎯 **Deeper dive:** [Typeahead Deep Dive with a Google SWE](https://www.youtube.com/watch?v=1moO3rn42uk) — explains the key insight: **precompute top-K completions at each trie node at write time** so reads are pure lookups.

---

### Review & Mock Practice (W25-26)

| Week | Dates | Active (30 min) | Passive (commute) |
|------|-------|-----------------|-------------------|
| W25 | Apr 5-11, 2027 | Pick 3 weakest chapters. Re-draw diagrams. Time yourself: 5 min per diagram. | 🎬 Browse ByteByteGo playlists for anything you missed |
| W26 | Apr 12-18, 2027 | Mock: pick a random chapter, explain the design out loud in 15 min (record yourself). Review. | 🎬 **"Top System Design Interview Questions"** — ByteByteGo |

**Week 25 drill:**
- [ ] Draw 3 architectures from memory in 15 min total (5 min each)
- [ ] Identify which ones you struggled with → re-read those sections

**Week 26 drill:**
- [ ] Pick a random chapter number (1-13). Set a 15-min timer. Explain the design out loud as if in an interview. Record on phone (voice memo).
- [ ] Listen back. Where did you get stuck? That's your gap.

---

### 🔄 Buffer 3 — Apr 19-25, 2027

> After the review + mock. Catch-up / rest week. If anything: re-watch one favorite ByteByteGo video during a walk. No active study required.

---

### 🔄 Buffer 4 — Apr 26 – May 2, 2027

> Final wrap / spring reset. Optionally record a second mock or polish the capstone walkthrough. Then you're done with Vol 1.

---

## 📊 Summary

| Block | Weeks | Dates | Chapters | Theme |
|-------|-------|-------|----------|-------|
| ✈️ Travel Buffer 1 | 2 wks | Aug 17-30 | — | 🧳 Aug trip |
| Foundation | W1-3 | Aug 31 – Sep 20 | Ch 1-3 | Scaling, estimation, framework |
| ✈️ Travel Buffer 2 | 2 wks | Sep 21 – Oct 4 | — | 🧳 Sep trip |
| Core designs (part 1) | W4-7 | Oct 5 – Nov 1 | Ch 4-5 | Rate limiter, consistent hashing |
| 🪔 Diwali Buffer | 1 wk | Nov 2-8 | — | Festival rest |
| Consistent hashing + KV | W8-10 | Nov 9-29 | Ch 5-6 | Finish hashing, KV store |
| Buffer 1 | 1 wk | Nov 30 – Dec 6 | — | Catch-up |
| Unique ID | W11-12 | Dec 7-20 | Ch 7 | Snowflake ID |
| Buffer 2 | 1 wk | Dec 21-27 | — | Catch-up (holidays near) |
| 🎄 Year-end Break | 2 wks | Dec 28 – Jan 10 | — | Real holiday rest |
| Core designs (part 3) | W13-24 | Jan 11 – Apr 4 | Ch 8-13 | URL shortener → autocomplete |
| Review + mock | W25-26 | Apr 5-18 | — | Draw + explain from memory |
| Buffer 3 | 1 wk | Apr 19-25 | — | Catch-up |
| Buffer 4 | 1 wk | Apr 26 – May 2 | — | Final wrap |
| **Total** | **37 wks** | **Aug 17 → May 2, 2027** | **13 chapters** | — |

---

## 🎬 Video index (all ByteByteGo unless noted)

| Ch | Video | Source | Notes |
|----|-------|--------|-------|
| 1 | [Vertical Vs Horizontal Scaling](https://www.youtube.com/watch?v=dvRFHG2-uYs) | ByteByteGo ✅ | Watch first |
| 1 | [What Is A CDN? How Does It Work?](https://www.youtube.com/watch?v=RI9np1LWzqw) | ByteByteGo ✅ | Supplement |
| 2 | [Back-Of-The-Envelope Estimation](https://www.youtube.com/watch?v=UC5xf8FbdJc) | ByteByteGo ✅ | |
| 3 | [System Design Interview: A Step-By-Step Guide](https://www.youtube.com/watch?v=i7twT3x5yv8) | ByteByteGo ✅ | The framework |
| 4 | [Rate Limiter System Design](https://www.youtube.com/watch?v=YXkOdWBwqaA) | ByteByteGo ✅ | |
| 5 | [Consistent Hashing](https://www.youtube.com/watch?v=UF9Iqmg94tk) | ByteByteGo ✅ | |
| 5 | [Consistent Hashing — Gaurav Sen](https://www.youtube.com/watch?v=zaRkONvyGr8) | ⚠️ Gaurav Sen | Better virtual node animation |
| 6 | [CAP Theorem Simplified](https://www.youtube.com/watch?v=BHqjEjzAicA) | ByteByteGo ✅ | |
| 6 | [How Key-Value Stores Work](https://www.youtube.com/watch?v=Dwt8R0KPu7k) | ByteByteGo ✅ | Redis, DynamoDB, Memcached |
| 7 | [Design a Unique ID Generator — Ch 7](https://www.youtube.com/watch?v=Ay7A4o4AVr8) | ⚠️ Ch walkthrough | Alex Xu book-specific |
| 8 | [How Does a URL Shortener Work?](https://www.youtube.com/watch?v=HHUi8F_qAXM) | ByteByteGo ✅ | |
| 9 | [Design a Web Crawler](https://www.youtube.com/watch?v=6u25GckPhLU) | ByteByteGo ✅ | |
| 10 | [Design a Notification System — Ch 10](https://www.youtube.com/watch?v=fJkAnN1Ozyw) | ⚠️ Ch walkthrough | Alex Xu book-specific |
| 11 | [News Feeds: Fan-Out, Caching & Scalability](https://www.youtube.com/watch?v=KwgI-VJEr3E) | ⚠️ English | Covers fan-out in depth |
| 12 | [Design A Chat System (WhatsApp, Messenger, Discord)](https://www.youtube.com/watch?v=okrR1KXNLtA) | ByteByteGo ✅ | |
| 13 | [Design Search Autocomplete System](https://www.youtube.com/watch?v=TZ_LSourdUc) | ⚠️ English | Trie, top-k, scaling |

> ✅ = verified from [ByteByteGo's official channel](https://www.youtube.com/@ByteByteGo). ⚠️ = ByteByteGo doesn't have a dedicated video; best English alternative selected.

---

## 🎯 Deeper-dive index (watch/read when ByteByteGo feels shallow)

> ByteByteGo above = light passive scaffold for the commute. These = the *teacher-quality*
> version for the same week. Watch the deeper one on the Saturday active block if the concept
> didn't fully click. Where a Gaurav Sen video ID wasn't verifiable, search his channel (@gkcs)
> by title rather than trusting a random upload.

| Ch | Deeper dive | Type | Why |
|----|-------------|------|-----|
| 1 | [Gaurav Sen — Load Balancing & DB Replication](https://www.youtube.com/watch?v=chh49EUiebg) (or search @gkcs "Scalability") | 🎬 | Derives *why* each tier is added |
| 2 | [Back Of The Envelope Estimation](https://www.youtube.com/watch?v=AsJJGe5vxFM) | 🎬 | Worked numeric examples |
| 3 | *(keep ByteByteGo — strong here)* | — | No swap needed |
| 4 | [Arcjet — Rate Limiting Algorithms](https://blog.arcjet.com/rate-limiting-algorithms-token-bucket-vs-sliding-window-vs-fixed-window/) | 📖 | Algorithm trade-offs + Redis races |
| 5 | [Gaurav Sen — Consistent Hashing](https://www.youtube.com/watch?v=zaRkONvyGr8) | 🎬 | Best virtual-node animation (your primary) |
| 6 | [Kleppmann — Please stop calling databases CP or AP](https://martin.kleppmann.com/2015/05/11/please-stop-calling-databases-cp-or-ap.html) | 📖 | Canonical CAP correction |
| 7 | [Unique ID Generator — Snowflake Algorithm](https://www.youtube.com/watch?v=g3BV_holJK4) | 🎬 | Full bit-layout + clock skew |
| 8 | [URL Shortener — FAANG Senior Engineer](https://www.youtube.com/watch?v=tm-SWO9gUAU) | 🎬 | Trade-off-driven |
| 9 | [Hello Interview — Web Crawler](https://www.hellointerview.com/learn/system-design/answer-keys/web-crawler) | 📖 | Deepest on frontier + dedup |
| 10 | [Notification Deep Dive — Google SWE](https://www.youtube.com/watch?v=TpugGhXhdaU) | 🎬 | Outbox/CDC, retries, DLQ |
| 11 | Search @gkcs "news feed"; backup [DesignGurus fan-out](https://www.designgurus.io/blog/design-social-media-news-feed) | 🎬/📖 | Celebrity/hybrid threshold |
| 12 | Search @gkcs "WhatsApp"; backup [WhatsApp System Design](https://www.youtube.com/watch?v=jN1pnBVIj7M) | 🎬 | WebSocket handlers + routing |
| 13 | [Typeahead Deep Dive — Google SWE](https://www.youtube.com/watch?v=1moO3rn42uk) | 🎬 | Precompute top-K at write time |

> 🎬 = video · 📖 = read. The **strongest upgrades over ByteByteGo** are Ch 1, 6, 7, 9, 10, 11, 12, 13.
> Ch 3 and Ch 4 keep ByteByteGo as-is (it's genuinely good there — no swap just to swap).

---

## 🚀 After Vol 1 (don't read now)

If interviews require more depth after Dec 2026:
- **Alex Xu Vol 2** — more design problems (Google Maps, hotel reservation, stock exchange)
- **DDIA (Designing Data-Intensive Applications)** — deep infrastructure knowledge
- **Mock interviews** — Pramp, Interviewing.io, or with a peer

---

*Back to [[README]] · [[progress-tracker]]*
