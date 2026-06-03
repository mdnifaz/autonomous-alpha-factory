# ARCH-002 Canonical Database Schema

Defines canonical persistence architecture.

Core domains:
- Assets
- Exchanges
- Symbols
- Orders
- Executions
- Trades
- Positions
- Balances
- Allocations
- Signals
- Votes
- Decisions
- Capabilities
- Experiments
- Knowledge
- Memory
- Audit

Storage layers:
- Redis
- SQLite/PostgreSQL abstraction
- Parquet Data Lake
- Vector Knowledge Store

Supports event-sourced recovery and immutable audit trails.