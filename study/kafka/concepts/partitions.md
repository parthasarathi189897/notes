---
type: concept-note
topic: Kafka Partitions — Parallelism and Ordering
context: work-project
week_learned: ~
confidence: L
related_sources:
  - "Confluent Apache Kafka 101 (2025) ft. Tim Berglund — Video 3"
created: 2026-06-09
updated: 2026-06-09
tags:
  - study
  - kafka
  - concept
  - partitions
  - scaling
---

# Kafka Partitions — Parallelism and Ordering

> How Kafka scales: one topic split across many independent logs.

---

## One-sentence summary

A **partition** is a single, ordered log. A **topic is made of many partitions** running in parallel, allowing Kafka to scale throughput while preserving order per partition key.

---

## Why partitions exist

One broker can only handle so much throughput. To scale:

**Without partitions:**
```
Topic: orders
  [one log]  ← single broker, single consumer reads all
  → bottleneck: one machine processes everything
```

**With partitions:**
```
Topic: orders
  Partition 0: [log]  → Consumer A reads
  Partition 1: [log]  → Consumer B reads
  Partition 2: [log]  → Consumer C reads
  → scale: 3 consumers read in parallel
```

More partitions = more parallelism = higher throughput.

![[diagrams/kafka-partitions.excalidraw]]

---

## The core concept: how keys map to partitions

When you write an event with a key:

```
Producer writes:
  key="user_123", value={...}
    ↓
  Hash key to choose partition
    ↓
  key="user_123" → Partition 0 (always the same partition)
  key="user_456" → Partition 2 (always the same partition)
    ↓
  All events for user_123 go to Partition 0
  All events for user_456 go to Partition 2
```

**Critical invariant:** Same key = same partition = **ordered**.

![[diagrams/kafka-key-routing.excalidraw]]

| Scenario | Partition Chosen | Order Guarantee |
|---|---|---|
| key="user_123" | Always Partition 0 | ✅ Ordered (all user_123 events in sequence) |
| key="user_456" | Always Partition 2 | ✅ Ordered (all user_456 events in sequence) |
| key=null | Round-robin | ❌ No order (events scattered) |

---

## Partitions and consumers: the scaling play

A topic with N partitions can be read by up to N consumers **in parallel**.

```
Topic: orders (3 partitions)

Partition 0 ──→ Consumer A (reads partition 0)
Partition 1 ──→ Consumer B (reads partition 1)
Partition 2 ──→ Consumer C (reads partition 2)

Result: 3× throughput vs 1 consumer reading all
```

**What if you have more partitions than consumers?**
```
Partitions 0, 1, 2, 3, 4
Consumers A, B

→ A gets partitions 0, 1, 2
→ B gets partitions 3, 4
→ Still parallel, but uneven load
```

**What if you have more consumers than partitions?**
```
Partitions 0, 1
Consumers A, B, C

→ A gets partition 0
→ B gets partition 1
→ C gets nothing (idle)
→ Can't go faster than 2 consumers
```

**Ideal:** # consumers ≤ # partitions for full parallelism.

---

## Consumer groups: who reads what?

A **consumer group** is a team of consumers reading one topic.

```
Topic: orders (3 partitions)
Consumer Group "app-1":
  - Consumer A reads partition 0
  - Consumer B reads partition 1
  - Consumer C reads partition 2

Consumer Group "analytics":
  - Consumer X reads partition 0
  - Consumer Y reads partition 1
  - Consumer Z reads partition 2

↓ Same topic, two independent groups, each reads all partitions
```

Each group tracks its own **offset** (position) per partition. They don't interfere.

![[diagrams/kafka-consumer-groups.excalidraw]]

---

## Partition anatomy

Each partition is a append-only log on disk:

```
Partition 0:
  [offset 0] → key="user_123", value={...}
  [offset 1] → key="user_456", value={...}
  [offset 2] → key="user_123", value={...}
  [offset 3] → key="user_789", value={...}
  
Consumer A reads from offset 0 → processes all 4 events in order
```

Offsets are **per partition**, not global:
- Partition 0: has offsets 0, 1, 2, 3
- Partition 1: has offsets 0, 1, 2, 3, 4
- They're independent

---

## Replication (teaser)

Partitions are replicated across brokers for durability:

```
Topic: orders (3 partitions, replication factor = 3)

Partition 0:
  Leader on Broker A
  Replicas on Broker B, C

Partition 1:
  Leader on Broker B
  Replicas on Broker A, C

Partition 2:
  Leader on Broker C
  Replicas on Broker A, B
```

Producers write to the **leader**. Leader syncs to **replicas**. If leader dies, a replica becomes the new leader.

(Don't need to know internals yet — just know partitions are backed up.)

---

## Key takeaways

| Concept | What it does |
|---|---|
| **Partition** | Single ordered log. Partitions exist to parallelize. |
| **Key** | Determines which partition. Same key → same partition → order. |
| **Offset** | Position in a partition. Each partition has its own offsets. |
| **Consumer** | Reads from partitions. One consumer reads one partition. |
| **Consumer Group** | Team of consumers. Each gets a subset of partitions. Multiple groups read independently. |

---

## What I don't need to know yet

- How Kafka chooses which broker gets which partition replica
- Partition rebalancing (what happens when a consumer joins/leaves)
- How to choose the "right" number of partitions (depends on throughput needs)
- Rack awareness and disaster recovery

---

## Confidence: Low → building

I understand what partitions are, why they exist (parallelism), how keys map to them (ordering), and how consumers read them. I haven't designed partition strategies or dealt with rebalancing.

---

## Sources

- [Confluent Apache Kafka 101 (2025), Video 3 — Partitions](https://www.youtube.com/watch?v=8L-1HSTf97E&list=PLf38f5LhQtheK16nwnCYFqH23WUUvZfSb&index=3) — ft. Tim Berglund

---

*Back to [[../README]]*
