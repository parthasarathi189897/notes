---
type: concept-note
topic: What is Apache Kafka
context: work-project
week_learned: ~
confidence: L
related_sources:
  - "Confluent Apache Kafka 101 (2025) ft. Tim Berglund — Video 1"
created: 2026-06-09
updated: 2026-06-09
tags:
  - study
  - kafka
  - messaging
  - concept
---

# What is Apache Kafka

> Work context study. Confluent Kafka 101 (2025), Video 1.
> Goal: understand the *why* and the mental model — not ops depth.

---

## One-sentence summary

Kafka is a **distributed event streaming platform** — a durable, append-only log of events that decouples the systems that produce data from the systems that consume it.

---

## The core idea: events, not messages

Kafka's framing in this course is important. It doesn't call itself a "message queue." It calls itself an **event streaming platform**.

- An **event** is a record of something that happened: `user_clicked`, `order_placed`, `payment_processed`
- Events are immutable — once written, they don't change
- Kafka stores events in order, durably, for as long as you configure

This framing matters: you're not sending commands between services, you're recording a history of what happened.

---

## The problem it solves

Traditional architectures have services talking directly to each other (point-to-point):

```
ServiceA ──► ServiceB
ServiceA ──► ServiceC
ServiceA ──► ServiceD
```

Problems:
- Tight coupling — A must know about B, C, D
- If B is down, A either retries, waits, or drops the message
- Adding a new consumer E requires changing A
- N services = N×(N-1) potential connections

With Kafka:

```
ServiceA ──► [Kafka Topic] ──► ServiceB
                          ──► ServiceC
                          ──► ServiceD
```

A publishes once. Everyone consumes independently. A doesn't know or care who's reading.

---

## Core mental model

![[diagrams/kafka-overview.excalidraw]]

```
Producer  ──►  Topic (append-only log)  ──►  Consumer(s)
```

| Component | What it is |
|---|---|
| **Event** | An immutable record of something that happened |
| **Topic** | A named, ordered, durable log of events |
| **Producer** | An app that writes events to a topic |
| **Consumer** | An app that reads events from a topic at its own pace |
| **Broker** | A Kafka server node that stores topics |
| **Offset** | A consumer's position in the log — consumers own this |
| **Partition** | A topic split into parallel shards for scale and throughput |
| **Consumer group** | Multiple consumers splitting partitions to share load |

**Key insight:** Kafka is a log, not a queue. Messages are not deleted when consumed. Consumers move through the log at their own pace using offsets.

---

## Why the log model matters

A traditional queue: read a message → it's gone.

Kafka's log: read an event → it stays. This means:
- Multiple independent consumers can read the same topic
- Consumers can **replay** — rewind their offset and re-process
- New consumers added later can read the full history
- Useful for: debugging, backfill jobs, audit trails, multiple microservices consuming the same stream

---

## Why it matters for work context

- **Decoupling** — services publish events; downstream services consume without coupling
- **Durability** — events survive service restarts and outages
- **Replay** — can reprocess historical events when a new service is added or a bug is fixed
- **Scale** — partitions allow horizontal parallelism; handles millions of events/sec

---

## What I don't need to know yet

- Kafka cluster setup, ZooKeeper vs KRaft
- Exactly-once semantics
- Kafka Streams / ksqlDB
- Replication factor and ISR internals
- Schema Registry

---

## Confidence: Low

I can explain what Kafka is, why it exists, and the log vs queue distinction. I don't yet have depth on partitioning strategy, consumer group rebalancing, or how our specific work project uses it.

---

## Sources

- [Confluent Apache Kafka 101 (2025), Video 1](https://www.youtube.com/watch?v=hyfX3_RB5cw&list=PLf38f5LhQtheK16nwnCYFqH23WUUvZfSb&index=1) — ft. Tim Berglund

---

*Back to [[../README]]*
