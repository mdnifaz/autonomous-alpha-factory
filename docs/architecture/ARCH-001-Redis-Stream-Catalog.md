# ARCH-001 Redis Stream Catalog

Implementation-grade event backbone specification.

Defines event naming, envelopes, stream ownership, consumer groups, retention, replay, DLQ handling, priorities and governance.

Core domains:
- market
- signal
- council
- portfolio
- risk
- execution
- learning

All services communicate through canonical streams only.