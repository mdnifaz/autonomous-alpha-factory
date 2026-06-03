# SPEC-003 Storage Specification

## Purpose
Defines storage architecture.

## Layers
- Redis (hot operational state)
- SQLite/PostgreSQL abstraction (operational records)
- Parquet Data Lake (historical data)
- Vector Store (knowledge retrieval)

## Principles
- Storage abstraction
- Immutable audit trail
- Event sourced recovery

## Data Categories
Market Data
Trading Data
Risk Data
Knowledge Data
Audit Data

## Retention
Hot: days
Warm: months
Cold: permanent