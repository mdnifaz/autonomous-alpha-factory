# SPEC-001 Exchange Abstraction Specification

## Purpose
Provide a canonical interface between exchanges and the Autonomous Alpha Factory.

## Principles
- Exchange agnostic
- Canonical models only
- Adapter isolation
- WebSocket and REST normalization

## Interfaces
- MarketDataProvider
- TradingProvider
- PositionProvider
- AccountProvider

## Canonical Models
- Order
- Trade
- Position
- Balance
- Market Event

## Responsibilities
Adapters normalize, validate, reconnect and publish canonical events.

## Constraints
No service outside adapter layer may call exchange-specific APIs directly.