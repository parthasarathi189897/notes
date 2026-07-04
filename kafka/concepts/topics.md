---
type: concept-note
topic: Kafka Topics
context: work-project
week_learned: ~
confidence: L
related_sources:
  - "Confluent Apache Kafka 101 (2025) ft. Tim Berglund"
created: 2026-06-09
updated: 2026-06-09
tags:
  - study
  - kafka
  - concept
  - topics
---

# Kafka Topics

> Simple explanation, no prior knowledge needed.

---

## One-sentence summary

A **topic** is just a named folder where Kafka stores a stream of events — like a running diary that keeps everything in order and never deletes entries.

---

## The everyday analogy

Think of a topic like a **WhatsApp group chat**:

- Anyone can send a message to the group (producer)
- Everyone in the group can read the messages (consumers)
- Messages stay in the chat — they don't disappear after someone reads them
- New members who join later can scroll up and read old messages too

In Kafka:
- The "group chat" = the **topic**
- "Sending a message" = **producing an event**
- "Reading messages" = **consuming events**

---

## What a topic actually is

![[diagrams/kafka-topic-log.excalidraw]]

A topic is an **append-only log** — imagine a long scroll of paper:

```
[event 1] → [event 2] → [event 3] → [event 4] → [event 5] → ...
  offset 0     offset 1    offset 2    offset 3    offset 4
```

- New events are always added to the **end** (append-only)
- Events are never edited or deleted (immutable)
- Each event has a number called an **offset** — its position in the log
- You can have as many topics as you need, each with a different name

---

## Topics are not queues

This is the most important thing to understand:

| Queue (old way) | Kafka Topic (new way) |
|---|---|
| Message read → message gone | Event read → event stays |
| Only one consumer gets each message | Many consumers can read the same event |
| Can't go back in time | Consumers can replay from any point |

**Why this matters:** If a new service joins your system next month, it can read all the events that happened before it existed. Nothing is lost.

---

## Topics are durable

Events in a topic are saved to **disk** (not just memory). This means:
- If Kafka restarts, the events are still there
- You configure how long to keep events: 7 days, 30 days, forever — your choice
- Default retention: **7 days**

---

## You can have many topics

Different topics for different purposes:

```
topic: orders          → order_placed, order_cancelled events
topic: payments        → payment_success, payment_failed events
topic: user-activity   → user_login, user_click events
```

Each topic is independent. Producers write to a specific topic. Consumers read from a specific topic.

---

## What I don't need to know yet

- How topics are split into partitions (next concept)
- How Kafka decides which broker stores which topic
- Topic compaction (a special mode that keeps only the latest value per key)

---

## Confidence: Low → building

I understand what a topic is and why it's different from a queue. I don't yet understand how topics scale (partitions) or how retention policies are configured.

---

## Sources

- [Confluent Apache Kafka 101 (2025)](https://www.youtube.com/watch?v=hyfX3_RB5cw&list=PLf38f5LhQtheK16nwnCYFqH23WUUvZfSb&index=1) — ft. Tim Berglund

---

*Back to [[../README]]*
