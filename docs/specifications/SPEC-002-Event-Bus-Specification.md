# SPEC-002 Event Bus Specification

## Purpose
Defines the event-driven communication backbone.

## Event Categories
- market.*
- signal.*
- council.*
- portfolio.*
- risk.*
- execution.*
- learning.*

## Canonical Envelope
Includes event_id, event_type, timestamp, producer, correlation_id and payload.

## Delivery Model
At-least-once delivery with idempotent consumers.

## Replay
All events are replayable.

## Governance
Events are immutable after publication.