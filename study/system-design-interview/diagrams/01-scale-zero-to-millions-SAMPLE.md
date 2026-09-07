---
type: sysdesign-diagram
chapter: 1
system: "Scale From Zero To Millions"
first_drawn: "2026-06-14"
can_redraw: true
confidence: "high"
last_reviewed: "2026-07-19"
created: 2026-05-31
tags: [study, system-design, diagram]
---

# Diagram: Scale From Zero To Millions

> Draw this after completing [[../weeks/week-02]].

---

## One-liner

Progressively add components (LB, cache, CDN, queue, sharding) to move a single-server app to millions of users — each layer solves a specific bottleneck.

---

## Excalidraw drawing

> Create your drawing in the `.excalidraw.md` file, it renders here automatically.

![[01-scale-zero-to-millions.excalidraw]]

---

## What to draw

Single user → web tier + data tier → load balancer → DB replication → cache layer → CDN → message queue → sharding.

**Label each component and explain *why* it's added.**

---

## Components checklist

- [x] Single server (web + DB on one machine)
- [x] Separate web tier and data tier
- [x] Load balancer (distribute traffic)
- [x] Database replication (master → read replicas)
- [x] Cache layer (Redis/Memcached between app and DB)
- [x] CDN (static assets closer to users)
- [x] Message queue (async processing)
- [x] Database sharding (horizontal partitioning)

---

## Concept notes

### Stage 1: Single server
- Everything on one box — web server, app code, DB
- Fine for development/hobby projects
- **Breaks when**: the box dies = total outage. Can't scale vertically forever.

### Stage 2: Separate web + data tiers
- Web servers are stateless, DB is stateful — different scaling needs
- Web tier can be replaced/restarted independently
- **Why**: isolate failure domains, allow each tier to scale independently

### Stage 3: Load balancer
- Sits between users and web tier (public IP → LB → private IPs)
- Distributes requests across N web servers (round-robin, least connections, etc.)
- **Why**: eliminates single point of failure in web tier, enables horizontal scaling
- Users never talk directly to web servers — security benefit too

### Stage 4: Database replication (master-replica)
- 1 master (writes) → N replicas (reads)
- Most apps are read-heavy (80-90% reads) so replicas handle the bulk
- If master dies → promote a replica
- **Why**: read throughput scales linearly, write availability via failover

### Stage 5: Cache layer
- Redis/Memcached between app servers and DB
- Read-through pattern: check cache → miss → query DB → populate cache → return
- TTL-based expiration; cache invalidation is genuinely hard
- **Why**: DB queries are slow (disk I/O), cache is fast (memory). 80/20 rule — cache 20% of data, serve 80% of reads from memory

### Stage 6: CDN
- Edge servers cache static assets (images, CSS, JS, video)
- Users hit the nearest CDN PoP instead of origin server
- Pull CDN (lazy): first request goes to origin, CDN caches response
- **Why**: reduces latency for global users, offloads bandwidth from origin

### Stage 7: Message queue
- Producer → Queue → Consumer (async processing)
- Decouples components: web server enqueues work, workers process independently
- If consumers are slow/down, messages buffer in queue (no data loss)
- **Why**: handle spikes gracefully, isolate slow operations (email, image resize, analytics)

### Stage 8: Database sharding
- Split data across multiple DBs by a shard key (e.g., user_id % N)
- Each shard holds a subset of data — queries only hit relevant shard
- Choose shard key carefully: even distribution, avoid hotspots
- **Challenges**: joins across shards are expensive, resharding when adding nodes, celebrity/hotspot problem
- **Why**: single DB can't hold infinite data; sharding distributes both storage and write load

---

## Where it's used (real systems)

| Component | Real-world example |
|-----------|-------------------|
| Load balancer | AWS ALB/NLB, Nginx, HAProxy |
| DB replication | MySQL master-replica, PostgreSQL streaming replication |
| Cache layer | Redis at Twitter (timeline cache), Memcached at Facebook |
| CDN | CloudFront (AWS), Akamai, Cloudflare |
| Message queue | Kafka at LinkedIn, SQS at AWS, RabbitMQ |
| Sharding | MongoDB auto-sharding, Vitess (YouTube's MySQL sharding) |

---

## Interview talking points

1. **Start simple**: "Let's begin with a single server and scale up as bottlenecks emerge"
2. **Each step has a trigger**: don't add complexity without a reason — name the bottleneck each component solves
3. **Stateless vs stateful**: web tier stateless (scale horizontally), DB stateful (scale with replication/sharding)
4. **Numbers matter**: "80% of requests are reads → read replicas. 20% of data serves 80% of traffic → cache that 20%"
5. **Tradeoffs unprompted**: mention cache invalidation difficulty, cross-shard join cost, sharding key selection

---

## My analogies / mnemonics

- **Restaurant analogy**: Single server = one-person food truck. Separate tiers = kitchen + front counter. LB = hostess seating people at open tables. Replicas = multiple cooks reading the same recipe. Cache = prep station (pre-chopped ingredients). CDN = satellite food trucks in other neighborhoods. Queue = order tickets on the rail. Sharding = franchise locations, each serving a different zip code.

---

## Questions I had (and answers)

**Q: When do you choose vertical vs horizontal scaling?**
A: Vertical first (simpler) until you hit hardware limits or single-point-of-failure becomes unacceptable. Then go horizontal. In interviews, always lean toward horizontal — that's what they want to discuss.

**Q: Why not add all components from day one?**
A: Over-engineering kills velocity. Each layer adds operational complexity (monitoring, debugging, deployment). Add when the bottleneck demands it.

---

## Confidence check

- [x] Can name all 8 stages in order
- [x] Can explain *why* each component is added (not just *what*)
- [x] Can draw full architecture from memory in under 15 min
- [x] Can name a real system using each component
- [x] Can discuss tradeoffs of each stage

---

## Draw log

| Date | From memory? | Time | Gaps |
|------|:------------:|------|------|
| Jun 14 | No — drew while reading | 25 min | N/A, first attempt with book open |
| Jun 15 | Yes — closed book | 18 min | Forgot message queue placement. Drew it after CDN but book puts it after cache. Order matters less than knowing *why* it's there. |
| Jun 22 | Yes — weekly review | 12 min | Got everything. Hesitated on sharding challenges — reviewed celebrity problem. |
| Jul 19 | Yes — 4-week recall | 10 min | Clean redraw. Confident. Added my own note about pull vs push CDN. |

---

*Back to [[../progress-tracker]] · Related: [[../weeks/week-02]]*
