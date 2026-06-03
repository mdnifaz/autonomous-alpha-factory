# DOC-002 Event Contract Constitution

Version: 2.0.0

Status: APPROVED

Classification: Constitutional

Authority Level: Organization-Wide

---

# 1. Purpose

The Event Contract Constitution defines how information flows through the Autonomous Alpha Factory.

All communication between services, agents, adapters, engines, storage systems, dashboards, simulators, and AI systems must occur through governed event contracts.

No business service may bypass this constitution.

---

# 2. Scope

Applies to:

* Exchange Adapters
* Market Services
* Feature Services
* AI Council
* Portfolio Services
* Risk Services
* Execution Services
* Research Services
* Learning Services
* Simulation Services
* Dashboard Services
* Audit Services

---

# 3. Core Principles

### Event First

All material state changes originate from events.

### Immutable Events

Published events are immutable.

### Replayability

All material events must be replayable.

### Traceability

Every event must be traceable through the organization.

### Versioned Evolution

Events evolve through explicit versioning.

---

# 4. Canonical Event Envelope

Every event must use:

```json
{
  "event_id": "uuid-v7",
  "event_type": "market.trade.v1",
  "event_version": "1.0.0",
  "timestamp": "2026-06-03T12:00:00Z",
  "producer": "market-service",
  "correlation_id": "uuid-v7",
  "causation_id": "uuid-v7",
  "payload": {}
}
```

No exceptions.

---

# 5. Event Identification

All events require:

* event_id
* event_type
* timestamp

Identifiers are immutable.

---

# 6. Correlation Rules

Every decision chain must be traceable.

Example:

```text
Trade Event
 ↓
Signal
 ↓
Vote
 ↓
Decision
 ↓
Allocation
 ↓
Order
 ↓
Execution
 ↓
PnL
```

All events in a chain share a correlation_id.

---

# 7. Causation Rules

causation_id identifies the direct parent event.

Example:

```text
Signal Generated
    ↓
Council Vote
```

Vote contains:

```text
causation_id = signal.event_id
```

---

# 8. Event Naming Standards

Format:

```text
domain.entity.version
```

Examples:

```text
market.trade.v1
signal.generated.v1
execution.order.v1
risk.alert.v1
```

---

# 9. Event Domains

Authorized domains:

```text
market
signal
council
portfolio
risk
execution
learning
system
audit
```

No custom domains allowed without constitutional approval.

---

# 10. Market Domain

Examples:

```text
market.trade.v1
market.kline.v1
market.orderbook.v1
market.funding.v1
market.open_interest.v1
market.liquidation.v1
market.regime.v1
```

Owner:

```text
Market Services
```

---

# 11. Signal Domain

Examples:

```text
signal.generated.v1
signal.validated.v1
signal.rejected.v1
```

Owner:

```text
Strategy Services
```

---

# 12. Council Domain

Examples:

```text
council.vote.v1
council.decision.v1
```

Owner:

```text
AI Council
```

---

# 13. Portfolio Domain

Examples:

```text
portfolio.allocation.v1
portfolio.rebalance.v1
portfolio.exposure.v1
```

Owner:

```text
Portfolio Services
```

---

# 14. Risk Domain

Examples:

```text
risk.alert.v1
risk.limit.v1
risk.kill_switch.v1
```

Owner:

```text
Risk Services
```

---

# 15. Execution Domain

Examples:

```text
execution.order.v1
execution.fill.v1
execution.cancel.v1
execution.position.v1
```

Owner:

```text
Execution Services
```

---

# 16. Learning Domain

Examples:

```text
learning.feedback.v1
experiment.result.v1
capability.promoted.v1
```

Owner:

```text
Research Services
```

---

# 17. Event Ownership

Only the owning service may publish a domain event.

Example:

```text
Risk Service
  → risk.*
```

Forbidden:

```text
Portfolio Service
  → risk.*
```

---

# 18. Event Immutability

After publication:

Forbidden:

* Modification
* Rewriting
* Deletion

Allowed:

* Replay
* Replication
* Archival

---

# 19. Event Versioning

Non-breaking:

```text
market.trade.v1.1
```

Breaking:

```text
market.trade.v2
```

Multiple versions may coexist.

---

# 20. Schema Governance

Every event must have:

* JSON Schema
* Version
* Owner
* Validation Rules

No undocumented event may enter production.

---

# 21. Validation Requirements

Every event passes:

### Layer 1

Schema Validation

### Layer 2

Type Validation

### Layer 3

Business Validation

### Layer 4

Relationship Validation

Failure causes rejection.

---

# 22. Event Priority Levels

Priority 1:

```text
risk.kill_switch.v1
risk.alert.v1
```

Priority 2:

```text
execution.*
```

Priority 3:

```text
portfolio.*
signal.*
```

Priority 4:

```text
learning.*
research.*
```

---

# 23. Event Retention

Hot:

```text
Redis Streams
7–30 Days
```

Warm:

```text
Operational Database
1–3 Years
```

Cold:

```text
Parquet Archive
Permanent
```

---

# 24. Replay Constitution

Replay must support:

* Stream Replay
* Market Replay
* Portfolio Replay
* Decision Replay
* Organization Replay

Replay cannot alter history.

---

# 25. Dead Letter Governance

Every stream requires:

```text
<stream>.dlq
```

Examples:

```text
market.trade.v1.dlq
execution.order.v1.dlq
```

Stores:

* Validation Failures
* Processing Failures
* Timeout Failures

---

# 26. Consumer Group Governance

Each service owns an independent consumer group.

Example:

```text
market.trade.v1

feature-service
ai-council-service
simulation-service
research-service
```

Consumers do not compete.

---

# 27. Event Security

Every event must support:

* Authentication
* Authorization
* Integrity Verification
* Audit Logging

---

# 28. Event Auditability

Every event must be:

* Traceable
* Replayable
* Attributable
* Recoverable

---

# 29. Event Compliance

Production events must:

* Use canonical envelope
* Use canonical naming
* Pass validation
* Maintain ownership rules

---

# 30. Constitutional Authority

Conflict resolution order:

```text
DOC-001 Canonical Domain Constitution

↓

DOC-002 Event Contract Constitution

↓

Other Constitutions

↓

Specifications

↓

Architecture Documents

↓

Implementation Code
```

No implementation may violate this constitution.
