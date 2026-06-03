# SPEC-002-Event-Bus-Specification.md

## Document Metadata

| Field          | Value                               |
| -------------- | ----------------------------------- |
| Document       | SPEC-002                            |
| Name           | Event Bus Specification             |
| Version        | 4.0.0                               |
| Status         | APPROVED                            |
| Classification | Implementation Grade                |
| Authority      | Specification                       |
| Depends On     | DOC-001, DOC-002, DOC-007, SPEC-001 |

---

# 1. Purpose

The Event Bus is the nervous system of the Autonomous Alpha Factory.

All services communicate through the Event Bus.

No service-to-service business coupling is permitted outside approved contracts.

Objectives:

* Event Driven Architecture
* Loose Coupling
* Replayability
* Auditability
* Scalability
* Reliability
* Fault Isolation

---

# 2. Scope

Applies To:

* Exchange Services
* Market Data Platform
* Feature Platform
* AI Council
* Portfolio Engine
* Risk Engine
* Execution Engine
* Simulation Engine
* Research Platform
* Dashboard Platform

---

# 3. Event Bus Architecture

```text
Producer
   ↓

Redis Streams

   ↓

Consumer Groups

   ↓

Consumers
```

---

# 4. Core Principles

### Events Are Immutable

Published events cannot be modified.

### Replay Everything

All events must be replayable.

### Consumers Are Independent

Consumers do not compete.

### Schema First

All events require contracts.

### Canonical Only

Only canonical events may traverse the bus.

---

# 5. Technology Stack

Primary:

```text
Redis Streams
```

Future Compatible:

```text
Kafka
Redpanda
NATS
```

Business services remain transport agnostic.

---

# 6. Event Envelope

Every event must contain:

```json
{
  "event_id":"uuid-v7",
  "event_type":"market.trade.v1",
  "event_version":"1.0.0",
  "timestamp":"2026-01-01T00:00:00Z",
  "producer":"market-service",
  "correlation_id":"uuid-v7",
  "causation_id":"uuid-v7",
  "payload":{}
}
```

---

# 7. Event Domains

Authorized Domains:

```text
market
feature
signal
council
portfolio
risk
execution
learning
research
system
audit
```

---

# 8. Stream Naming Standard

Format:

```text
<domain>.<entity>.v<version>
```

Examples:

```text
market.trade.v1
market.orderbook.v1
feature.vector.v1
signal.generated.v1
execution.fill.v1
```

---

# 9. Event Ownership

Only owning services may publish:

```text
market.*      → Market Platform
feature.*     → Feature Platform
signal.*      → Strategy Services
council.*     → AI Council
risk.*        → Risk Engine
execution.*   → Execution Engine
```

---

# 10. Consumer Groups

Each service owns independent consumer groups.

Example:

```text
market.trade.v1

feature-platform
ai-council
simulation-engine
dashboard
research-engine
```

---

# 11. Stream Registry

Repository:

```text
contracts/events/
```

Every stream requires:

* Owner
* Version
* Schema
* Retention Policy

---

# 12. Event Schema Governance

Every event must have:

```text
JSON Schema
Version
Owner
Validation Rules
```

---

# 13. Event Validation Pipeline

Layers:

```text
Schema Validation
Type Validation
Business Validation
Relationship Validation
```

Invalid events rejected.

---

# 14. Correlation IDs

Used for end-to-end tracing.

Example:

```text
Trade
 ↓
Signal
 ↓
Decision
 ↓
Order
 ↓
Execution
```

All share the same correlation_id.

---

# 15. Causation IDs

Identify immediate parent event.

Example:

```text
Signal
 ↓
Decision
```

Decision contains:

```text
causation_id = signal.event_id
```

---

# 16. Event Routing

Routing based on:

```text
Event Type
Consumer Group
Subscriptions
```

---

# 17. Stream Retention

Hot Retention:

```text
7–30 Days
```

Configurable.

---

# 18. Replay Support

Replay Types:

```text
Market Replay
Decision Replay
Portfolio Replay
Organization Replay
```

---

# 19. Dead Letter Queues

Every stream requires:

```text
<stream>.dlq
```

Examples:

```text
market.trade.v1.dlq
execution.order.v1.dlq
```

---

# 20. DLQ Triggers

```text
Validation Failure
Processing Failure
Timeout Failure
Unknown Exception
```

---

# 21. Replay Engine

Repository:

```text
src/event_bus/replay/
```

Interfaces:

```python
async def replay_stream()

async def replay_range()

async def replay_correlation()
```

---

# 22. Idempotency

Consumers must support:

```text
Exactly Once Processing Semantics
```

Implementation:

```text
Idempotency Keys
Processed Event Store
```

---

# 23. Event Ordering

Required for:

```text
Orders
Executions
Positions
```

Best effort for:

```text
Trades
Market Data
```

---

# 24. Partitioning Strategy

Logical Partitions:

```text
market
feature
execution
risk
portfolio
```

Future Kafka compatibility.

---

# 25. Backpressure Management

Required:

```text
Queue Monitoring
Consumer Lag Monitoring
Flow Control
```

---

# 26. Consumer Lag Monitoring

Metrics:

```text
Pending Events
Processing Delay
Backlog Growth
```

---

# 27. Retry Strategy

Retries:

```text
Exponential Backoff
```

Levels:

```text
Immediate
Short
Medium
Long
DLQ
```

---

# 28. Event Security

Required:

```text
Authentication
Authorization
Encryption
Audit Logging
```

---

# 29. Event Integrity

Verify:

```text
Schema
Checksums
Timestamps
```

---

# 30. Audit Events

Examples:

```text
audit.event_received.v1
audit.event_replayed.v1
audit.event_failed.v1
```

---

# 31. Redis Stream Design

Required Streams:

```text
market.*
feature.*
signal.*
council.*
portfolio.*
risk.*
execution.*
learning.*
audit.*
```

---

# 32. Redis Consumer Groups

Pattern:

```text
<service-name>-consumer-group
```

---

# 33. Event Bus Health Engine

Health Inputs:

```text
Latency
Lag
Error Rate
DLQ Growth
```

Output:

```text
0-100 Health Score
```

---

# 34. Event Bus Monitoring

Required Metrics:

```text
Events Per Second
Consumer Lag
Retry Rate
DLQ Count
```

---

# 35. Performance Targets

Publish:

```text
< 5ms
```

Consume:

```text
< 10ms
```

Internal Routing:

```text
< 20ms
```

---

# 36. Scalability Targets

Support:

```text
100k+ events/sec
100+ streams
100+ consumer groups
```

---

# 37. Event Contracts Repository

```text
contracts/events/
```

Required:

```text
market.trade.v1.json
signal.generated.v1.json
execution.order.v1.json
```

---

# 38. JSON Event Schema Example

```json
{
  "event_type":"signal.generated.v1",
  "payload":{
    "symbol":"BTC-USDT-PERP",
    "direction":"LONG",
    "confidence":0.81
  }
}
```

---

# 39. Protobuf Contracts

Repository:

```text
contracts/proto/events/
```

Required:

```text
Trade.proto
Signal.proto
Decision.proto
Order.proto
Execution.proto
```

---

# 40. Certification Framework

Required Tests:

```text
Publish
Consume
Replay
Recovery
Failover
Latency
Scaling
```

---

# 41. Replay Certification

Validate:

```text
Ordering
Integrity
Completeness
```

---

# 42. Recovery Certification

Validate:

```text
Consumer Restart
Redis Restart
Network Failure
```

---

# 43. Security Certification

Validate:

```text
Authentication
Authorization
Audit Logging
```

---

# 44. Repository Structure

```text
src/

 event_bus/

    publisher/
    consumer/
    replay/
    routing/
    monitoring/
    security/

contracts/

 events/
 proto/
```

---

# 45. Definition Of Done

Event Bus complete only if:

✓ Canonical Event Compliant

✓ Replay Compatible

✓ DLQ Enabled

✓ Auditable

✓ Certified

✓ Scalable

✓ Secure

✓ Distributed Ready

---

# 46. Architectural Authority

All platform communication must traverse the Event Bus.

No service may bypass this specification.

---

# 47. Document Status

```text
Document:
SPEC-002

Name:
Event Bus Specification

Version:
4.0.0

Status:
APPROVED

Classification:
Implementation Grade

Authority:
Specification
```
