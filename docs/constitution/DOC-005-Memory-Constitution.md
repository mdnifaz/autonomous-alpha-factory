# DOC-005 Memory Constitution

## Purpose
Defines how the Autonomous Alpha Factory remembers, forgets, learns and accumulates organizational knowledge.

## Core Principles
- Memory is hierarchical
- Knowledge compounds over time
- Retrieval is preferred over context stuffing
- Important knowledge is never lost
- Memory must be exchange and model agnostic

## Layer 1: Working Memory
Purpose:
Current decision making.

Storage:
Redis

Examples:
- Current market state
- Active signals
- Open positions
- Current risk state

Retention:
Minutes to hours

## Layer 2: Operational Memory
Purpose:
Recent operational context.

Storage:
SQLite/PostgreSQL abstraction

Examples:
- Active experiments
- Current allocations
- Recent performance
- Agent reputations

Retention:
Days to months

## Layer 3: Historical Memory
Purpose:
Long-term factual record.

Storage:
Parquet/Data Lake

Examples:
- Market data
- Orders
- Executions
- Trades
- Backtests
- Simulations

Retention:
Permanent

## Layer 4: Organizational Knowledge
Purpose:
Institutional learning.

Storage:
Knowledge Base + Vector Retrieval

Examples:
- Postmortems
- Research findings
- Alpha discoveries
- Regime observations
- Capability lessons

Retention:
Permanent

## Reflection System
The organization performs periodic reviews.

Review Sources:
- Live trading
- Paper trading
- Simulations
- Research experiments

Outputs:
- Lessons learned
- Improvement opportunities
- Updated knowledge entries

## Memory Importance Score
Each memory receives a dynamic importance score.

Factors:
- Profit impact
- Risk impact
- Novelty
- Frequency
- Longevity

## Forgetting Policy
Low-value operational memories may be summarized and archived.

Historical records are never deleted.

Audit records are immutable.

## Retrieval Rules
Agents retrieve memory using:
- Semantic search
- Metadata filtering
- Temporal relevance
- Regime relevance

## Constitutional Constraints
Memory systems may optimize storage and retrieval.

Memory systems may not:
- Delete audit records
- Alter historical trade records
- Modify constitutional documents