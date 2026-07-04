---
type: concept-note
topic: Kafka Events — Structure and Anatomy
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
  - events
  - messages
---

# Kafka Events — Structure and Anatomy

> What lives inside a Kafka topic? The actual structure of events.

---

## One-sentence summary

A Kafka **event** (or message) is a structured record with a **key**, **value**, **timestamp**, and **headers** — the producer decides what goes in, Kafka manages the rest.

---

## The anatomy of a Kafka event

When you write an event to a Kafka topic, here's what gets stored:

```
┌─────────────────────────────────────┐
│ Kafka Event (Message)               │
├─────────────────────────────────────┤
│ Partition ID (which shard)          │
│ Offset (position in log)            │
│ Key       (optional, for grouping)  │
│ Value     (the actual data)         │
│ Timestamp (when it happened)        │
│ Headers   (metadata, optional)      │
└─────────────────────────────────────┘
```

### **Value** — The actual data you care about

The **value** is the main payload — the thing you're sending.

Examples:
- `{"user_id": 123, "action": "login", "ip": "192.168.1.1"}` (JSON)
- `User clicked button at 3:45pm` (string)
- Binary data (protobuf, Avro)

**Format:** Usually JSON or binary. You decide. Kafka doesn't care — it just stores bytes.

### **Key** — Optional, but powerful

The **key** is used for **routing and grouping**.

```
┌────────────────────────────────────┐
│ Topic: orders                      │
│                                    │
│ Event 1: key="user_123", value=... │
│ Event 2: key="user_456", value=... │
│ Event 3: key="user_123", value=... │
│                                    │
│ → Events with same key → same      │
│   partition → same consumer        │
└────────────────────────────────────┘
```

**Why it matters:**
- All events with the **same key go to the same partition**
- This guarantees **order** for that key (important for state machines: user's orders must be processed in sequence)
- Enables **compacted topics** (keeping only the latest event per key)

Examples of keys:
- `user_123` (keep all user events together)
- `order_456` (keep order lifecycle events in order)
- `null` (no grouping — distributed round-robin)

### **Timestamp** — When did it happen?

Kafka adds a timestamp automatically. Two options:

| Type | What it is | Set by |
|---|---|---|
| **Create Time** | When the producer sent it | Producer |
| **Log Append Time** | When Kafka broker stored it | Broker |

Usually you want **create time** (what the user saw) not log append time (internal broker timing).

---

## **Headers** — Metadata about the event

Headers are optional key-value pairs attached to the event. Useful for:

```
Headers:
  "traceId": "abc-123-def"
  "userId": "user_456"
  "service": "payment-service"
  "priority": "high"
```

**Why use headers vs putting in the value?**
- Headers are **filtered and routed** without parsing the value
- You can read headers to make routing decisions without deserialization
- Keeps the value focused on business data

---

## Real example: An order event

```json
{
  "key": "order_12345",
  "value": {
    "order_id": "order_12345",
    "user_id": "user_456",
    "items": [
      {"sku": "SHOE-001", "qty": 2, "price": 99.99}
    ],
    "total": 199.98,
    "status": "placed"
  },
  "timestamp": 1717993234567,
  "headers": {
    "traceId": "xyz-789-abc",
    "userId": "user_456"
  }
}
```

What each part does:
- **key** = `order_12345` → ensures all events for this order go to the same partition, stay in order
- **value** = the actual order data (your business logic reads this)
- **timestamp** = 1717993234567 (milliseconds since epoch) → when the order was placed
- **headers** = tracing + routing metadata

---

## Key vs Value — Quick mental model

| Aspect | Key | Value |
|---|---|---|
| Required? | No | Yes |
| What goes here | Identifier, grouping field | Actual data |
| Used for | Partitioning, ordering | Business logic |
| Format | Usually simple string/ID | Usually JSON/binary |
| Example | `user_123` | `{"action": "login", "ip": "..."}` |

---

## Retention and Compaction — Two ways to manage event lifecycle

### Log Retention (Time-based)

How long do events stay in a topic? By default:
- **Default:** 7 days
- **Configurable:** 1 hour, 24 hours, 30 days, forever — your choice
- **Policy:** Once retention window expires → **oldest events deleted**

This is why consumers can replay: events live on disk durably for the retention window.

**Use case:** Most topics. Events are immutable records of what happened. Keep them for a while, then discard.

### Log Compaction (Keyed cleanup)

For topics with **keys**, you can enable **log compaction** instead of time-based deletion.

Compaction keeps **only the latest event per key**:

```
Before compaction:
key=user_123, value={status: "active"}    (offset 0)
key=user_456, value={status: "new"}       (offset 1)
key=user_123, value={status: "inactive"}  (offset 2) ← latest for key_123
key=user_789, value={status: "active"}    (offset 3)

After compaction:
key=user_456, value={status: "new"}       (offset 1)
key=user_123, value={status: "inactive"}  (offset 2) ← kept as latest
key=user_789, value={status: "active"}    (offset 3)
```

**Why?**
- Topic becomes a **state snapshot** — each key has its current value
- Useful for: user profiles, settings, configuration, counters
- New consumers can replay and get the current state without processing history

**How it works:**
- Old events with the same key are deleted
- Latest event per key is kept forever (or until deleted manually)
- Requires **non-null keys** to work

| Retention | Compaction |
|---|---|
| Time-based (7 days default) | Key-based (keep latest per key) |
| Deletes oldest events after window | Deletes old events for same key |
| All events preserved in window | Only latest per key preserved |
| Use case: event streams, audit logs | Use case: state stores, KV stores |

---

## What I don't need to know yet

- Serialization/deserialization formats (Avro, Protobuf, JSON Schema)
- Compression (gzip, snappy, lz4)
- Batch writes and performance tuning
- Exactly-once semantics with idempotent keys

---

## Confidence: Low → building

I understand what a Kafka event contains and why each field matters. I haven't designed schemas or dealt with serialization yet.

---

## Sources

- [Confluent Apache Kafka 101 (2025)](https://www.youtube.com/watch?v=hyfX3_RB5cw&list=PLf38f5LhQtheK16nwnCYFqH23WUUvZfSb&index=1) — ft. Tim Berglund

---

*Back to [[../README]]*
