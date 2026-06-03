# SPEC-009-Portfolio-Construction-Specification.md

## Document Metadata

| Field          | Value                                                   |
| -------------- | ------------------------------------------------------- |
| Document       | SPEC-009                                                |
| Name           | Portfolio Construction Specification                    |
| Version        | 4.0.0                                                   |
| Status         | APPROVED                                                |
| Classification | Implementation Grade                                    |
| Authority      | Specification                                           |
| Depends On     | DOC-001, DOC-002, DOC-003, SPEC-004, SPEC-006, SPEC-008 |

---

# 1. Purpose

The Portfolio Construction Engine converts approved AI Council decisions into risk-adjusted capital allocations.

Responsibilities:

* Capital Allocation
* Position Sizing
* Portfolio Optimization
* Diversification
* Rebalancing
* Exposure Management
* Portfolio Lifecycle Management

---

# 2. Core Principles

### Capital Is Scarce

Capital allocation must maximize risk-adjusted return.

---

### Risk Before Return

Risk constraints are mandatory.

---

### Diversification Required

No single decision may dominate the portfolio.

---

### Dynamic Allocation

Portfolio adapts to changing market conditions.

---

### Replayable

Portfolio decisions must be reproducible.

---

# 3. Portfolio Architecture

```text
AI Council Decisions
        │

Portfolio Construction
        │

Risk Validation
        │

Allocation Engine
        │

Execution Engine
```

---

# 4. Portfolio Layers

```text
Signal Layer
↓
Allocation Layer
↓
Optimization Layer
↓
Risk Layer
↓
Execution Layer
```

---

# 5. Portfolio Objectives

Primary:

```text
Maximize Risk Adjusted Return
```

Secondary:

```text
Minimize Drawdown

Control Volatility

Maintain Liquidity
```

---

# 6. Portfolio Types

Supported:

```text
LONG_ONLY
LONG_SHORT
MARKET_NEUTRAL
DIRECTIONAL
MULTI_STRATEGY
```

---

# 7. Portfolio States

```text
CREATED
ACTIVE
REBALANCING
PAUSED
DEGRADED
TERMINATED
```

---

# 8. Capital Model

Capital Types:

```text
Available Capital
Allocated Capital
Reserved Capital
Risk Capital
```

---

# 9. Allocation Inputs

Consumes:

```text
Council Decisions
Confidence Scores
Risk Scores
Market Conditions
Liquidity Metrics
```

---

# 10. Allocation Outputs

Produces:

```text
Target Positions
Target Weights
Execution Requests
```

---

# 11. Position Sizing Engine

Responsible for:

```text
Position Size
Exposure
Leverage
Risk Budget
```

---

# 12. Sizing Models

Supported:

```text
FIXED
RISK_BASED
VOLATILITY_BASED
KELLY
HYBRID
```

---

# 13. Fixed Sizing

Example:

```text
5% Capital Per Position
```

---

# 14. Risk Based Sizing

Based on:

```text
Risk Budget
Stop Distance
Volatility
```

---

# 15. Volatility Based Sizing

Position size decreases as volatility increases.

---

# 16. Kelly Sizing

Supported:

```text
Full Kelly
Half Kelly
Fractional Kelly
```

---

# 17. Hybrid Sizing

Combines:

```text
Kelly
Risk Budget
Volatility
Liquidity
```

---

# 18. Allocation Constraints

Required:

```text
Position Limits
Portfolio Limits
Risk Limits
Liquidity Limits
```

---

# 19. Portfolio Constraints

Examples:

```text
Max Position Weight

Max Sector Weight

Max Exchange Weight
```

---

# 20. Diversification Engine

Measures:

```text
Concentration
Correlation
Exposure
```

---

# 21. Correlation Engine

Calculates:

```text
Asset Correlation
Strategy Correlation
Portfolio Correlation
```

---

# 22. Concentration Engine

Measures:

```text
Single Asset Concentration
Exchange Concentration
Strategy Concentration
```

---

# 23. Optimization Engine

Goals:

```text
Maximize Return
Minimize Risk
Maintain Liquidity
```

---

# 24. Optimization Methods

Supported:

```text
Mean Variance
Risk Parity
Kelly
Hierarchical Risk Parity
Custom
```

---

# 25. Risk Parity

Allocates risk equally.

---

# 26. Hierarchical Risk Parity

Supported for large portfolios.

---

# 27. Liquidity Constraints

Inputs:

```text
Market Depth
Spread
Impact Cost
```

---

# 28. Liquidity Score

Range:

```text
0-100
```

---

# 29. Portfolio Risk Budget

Defined by:

```text
Maximum Drawdown

Volatility Budget

Exposure Budget
```

---

# 30. Allocation Confidence

Derived from:

```text
Council Confidence

Historical Accuracy

Market Conditions
```

---

# 31. Allocation Score

Range:

```text
0-100
```

---

# 32. Rebalancing Engine

Supports:

```text
Scheduled
Threshold
Risk Triggered
```

---

# 33. Scheduled Rebalancing

Examples:

```text
Daily
Weekly
Monthly
```

---

# 34. Threshold Rebalancing

Triggered when:

```text
Weight Drift Exceeds Threshold
```

---

# 35. Risk Rebalancing

Triggered by:

```text
Risk Breach
Drawdown
Exposure Breach
```

---

# 36. Portfolio Health Engine

Measures:

```text
Performance
Risk
Diversification
Liquidity
```

---

# 37. Health Score

Range:

```text
0-100
```

---

# 38. Portfolio Events

```text
portfolio.created.v1
portfolio.rebalanced.v1
portfolio.allocation.updated.v1
portfolio.closed.v1
```

---

# 39. Event Streams

Published To:

```text
portfolio.*
```

---

# 40. Allocation Object

```json
{
  "symbol":"BTC-USDT-PERP",
  "target_weight":0.05,
  "allocation":5000
}
```

---

# 41. Portfolio Object

```json
{
  "portfolio_id":"uuid",
  "capital":100000,
  "risk_budget":0.02
}
```

---

# 42. Portfolio Models

Repository:

```text
src/portfolio/models/
```

Required:

```text
Portfolio
Allocation
PositionTarget
RiskBudget
RebalancePlan
```

---

# 43. Pydantic Portfolio Model

```python
class Portfolio(BaseModel):

    portfolio_id: UUID

    capital: Decimal

    risk_budget: Decimal
```

---

# 44. Allocation Model

```python
class Allocation(BaseModel):

    symbol: str

    target_weight: Decimal

    capital: Decimal
```

---

# 45. Rebalance Plan Model

```python
class RebalancePlan(BaseModel):

    plan_id: UUID

    actions: list
```

---

# 46. Event Contracts

Repository:

```text
contracts/events/portfolio/
```

Required:

```text
portfolio_created.json
allocation_updated.json
rebalance_completed.json
```

---

# 47. Protobuf Contracts

Repository:

```text
contracts/proto/portfolio/
```

Required:

```text
Portfolio.proto
Allocation.proto
PositionTarget.proto
```

---

# 48. Portfolio Analytics

Measures:

```text
Return
Volatility
Sharpe
Sortino
Calmar
```

---

# 49. Exposure Analytics

Measures:

```text
Gross Exposure
Net Exposure
Exchange Exposure
Sector Exposure
```

---

# 50. Drawdown Analytics

Measures:

```text
Current Drawdown
Maximum Drawdown
Recovery Time
```

---

# 51. Scenario Analysis

Supported:

```text
Crash
Rally
Liquidity Shock
Exchange Failure
```

---

# 52. Stress Testing Integration

Consumes Risk Engine stress scenarios.

---

# 53. Risk Integration

All allocations require:

```text
Risk Approval
```

Mandatory.

---

# 54. AI Council Integration

Consumes:

```text
Council Decisions
Confidence Scores
```

---

# 55. Market Data Integration

Consumes:

```text
Volatility
Liquidity
Funding
Open Interest
```

---

# 56. Execution Integration

Produces:

```text
Execution Requests
```

---

# 57. Replay Support

Must replay:

```text
Allocations
Rebalances
Portfolio States
```

---

# 58. Replay Fidelity

Must preserve:

```text
Inputs
Constraints
Weights
Outputs
```

---

# 59. Certification Framework

Required Tests:

```text
Allocation
Optimization
Rebalancing
Replay
Stress
Recovery
```

---

# 60. Allocation Certification

Verify:

```text
Sizing Accuracy
Constraint Enforcement
```

---

# 61. Optimization Certification

Verify:

```text
Risk Compliance
Diversification
```

---

# 62. Rebalancing Certification

Verify:

```text
Drift Detection
Execution Plan Generation
```

---

# 63. Security Controls

Required:

```text
Authentication
Authorization
Audit Logging
```

---

# 64. Audit Controls

Record:

```text
Allocations
Rebalances
Overrides
Risk Decisions
```

---

# 65. Human Override

Authorized users may:

```text
Pause
Resume
Override
```

All actions audited.

---

# 66. Scalability

Support:

```text
Single GPU
Multi GPU
Distributed Cluster
```

---

# 67. Multi Portfolio Support

Supported:

```text
Research Portfolios
Paper Portfolios
Production Portfolios
```

---

# 68. Repository Structure

```text
src/

 portfolio/

    allocation/
    sizing/
    optimization/
    diversification/
    rebalancing/
    analytics/
    replay/
    certification/

contracts/

 portfolio/
```

---

# 69. Definition Of Done

Portfolio Construction Engine complete only if:

✓ Position Sizing Implemented

✓ Optimization Implemented

✓ Rebalancing Implemented

✓ Risk Integrated

✓ Replay Compatible

✓ Certified

✓ Audited

✓ Distributed Ready

---

# 70. Architectural Authority

All capital allocation decisions must traverse the Portfolio Construction Engine.

No component may bypass portfolio governance.

---

# 71. Document Status

```text
Document:
SPEC-009

Name:
Portfolio Construction Specification

Version:
4.0.0

Status:
APPROVED

Classification:
Implementation Grade

Authority:
Specification
```
