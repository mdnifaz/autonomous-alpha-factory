# DOC-002 Event Contract Constitution

## Purpose
Defines the event-driven nervous system of the Autonomous Alpha Factory.

## Principles
- Canonical events only
- Exchange-normalized payloads
- Versioned schemas
- Replayable events
- Immutable audit trail
- Loose coupling between services

## Event Naming
<domain>.<entity>.<version>

Examples:
- market.trade.v1
- market.orderbook.v1
- signal.generated.v1
- council.vote.v1
- risk.alert.v1
- execution.order.v1

## Core Streams
### Market Domain
- market.trade.v1
- market.kline.v1
- market.orderbook.v1
- market.funding.v1
- market.open_interest.v1
- market.liquidation.v1
- market.regime.v1

### AI Domain
- signal.generated.v1
- council.vote.v1
- council.decision.v1
- model.inference.v1

### Trading Domain
- strategy.signal.v1
- portfolio.allocation.v1
- capability.update.v1

### Risk Domain
- risk.alert.v1
- risk.limit.v1
- risk.kill_switch.v1

### Execution Domain
- execution.order.v1
- execution.fill.v1
- execution.cancel.v1
- execution.position.v1

### Learning Domain
- learning.feedback.v1
- experiment.result.v1
- model.promoted.v1

## Base Event Envelope
{
  "event_id": "uuid",
  "event_type": "market.trade.v1",
  "timestamp": "ISO8601",
  "source": "service_name",
  "payload": {}
}

## Replay Rules
All events must be persisted.
Replay engine must reconstruct full system state using only event history.

## Versioning Rules
Breaking changes require new major version.
Example:
market.trade.v1 -> market.trade.v2

## Governance
Services may only communicate through approved event contracts.
Direct service-to-service business logic coupling is prohibited.