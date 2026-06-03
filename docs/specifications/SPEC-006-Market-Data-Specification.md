# SPEC-006 Market Data Specification

## Purpose
Defines acquisition, normalization and distribution of market data.

## Sources
- Trades
- Order Books
- OHLCV
- Funding
- Open Interest
- Liquidations

## Storage
1m OHLCV as canonical base timeframe.
Higher timeframes derived on demand.

## Transport
WebSocket first.
REST for recovery and backfill.

## Governance
All market data must be normalized into canonical events.