# SPEC-004-AI-Council-Specification.md

## Document Metadata

| Field          | Value                                                  |
| -------------- | ------------------------------------------------------ |
| Document       | SPEC-004                                               |
| Name           | AI Council Specification                               |
| Version        | 4.0.0                                                  |
| Status         | APPROVED                                               |
| Classification | Implementation Grade                                   |
| Authority      | Specification                                          |
| Depends On     | DOC-001, DOC-002, DOC-003, DOC-005, SPEC-002, SPEC-006 |

---

# 1. Purpose

The AI Council is the autonomous decision-making body of the organization.

Responsibilities:

* Market Analysis
* Signal Evaluation
* Debate
* Challenge Generation
* Risk Review
* Decision Making
* Capital Allocation Recommendations
* Strategy Governance

The AI Council is the only entity authorized to generate portfolio recommendations.

---

# 2. Core Principles

### No Single Model Authority

No individual model may control capital.

---

### Adversarial Deliberation

Recommendations must be challenged.

---

### Evidence First

Claims require supporting evidence.

---

### Decisions Are Auditable

All votes, debates, and outcomes are stored.

---

### Human Override Always Available

Autonomy exists within constitutional limits.

---

# 3. Council Architecture

```text
Market Data
     │

Features
     │

Research
     │

┌────────────────────┐
│     AI Council     │
└────────────────────┘

Bull Agents
Bear Agents
Risk Agents
Research Agents

     │

Debate Engine

     │

Voting Engine

     │

Decision Engine

     │

Portfolio Engine
```

---

# 4. Council Layers

```text
Observation Layer
↓

Analysis Layer
↓

Debate Layer
↓

Voting Layer
↓

Decision Layer
↓

Audit Layer
```

---

# 5. Agent Categories

Required Agent Types:

```text
Bull Agent
Bear Agent
Risk Agent
Research Agent
Macro Agent
Execution Agent
Portfolio Agent
```

---

# 6. Bull Agent

Responsibilities:

```text
Identify Long Opportunities
Identify Momentum
Identify Positive Catalysts
```

---

# 7. Bear Agent

Responsibilities:

```text
Identify Shorts
Identify Weakness
Identify Downside Risks
```

---

# 8. Risk Agent

Responsibilities:

```text
Challenge All Recommendations
Identify Risk Exposure
Recommend Constraints
```

Risk Agent may veto.

---

# 9. Research Agent

Responsibilities:

```text
Historical Analysis
Pattern Discovery
Hypothesis Testing
```

---

# 10. Macro Agent

Responsibilities:

```text
Macro Trends
Funding Environment
Cross Asset Analysis
```

---

# 11. Execution Agent

Responsibilities:

```text
Execution Feasibility
Liquidity Analysis
Slippage Risk
```

---

# 12. Portfolio Agent

Responsibilities:

```text
Capital Allocation
Diversification
Exposure Analysis
```

---

# 13. Agent Identity

Every agent requires:

```text
agent_id
name
version
owner
status
```

---

# 14. Agent Lifecycle

States:

```text
DRAFT
TESTING
SHADOW
ACTIVE
DEPRECATED
RETIRED
```

---

# 15. Observation Phase

Inputs:

```text
Market Data
Features
Research
Portfolio State
Risk State
```

Output:

```text
Observations
```

---

# 16. Analysis Phase

Agents generate:

```text
Hypotheses
Predictions
Risk Assessments
```

---

# 17. Debate Phase

Agents challenge:

```text
Evidence
Assumptions
Confidence
Risk
```

---

# 18. Debate Rules

Every proposal requires:

```text
Supporting Evidence

Counter Arguments

Risk Review
```

---

# 19. Challenge Engine

Automatically generates:

```text
Contrarian Views

Failure Scenarios

Risk Scenarios
```

---

# 20. Voting Phase

Agents vote:

```text
APPROVE

REJECT

ABSTAIN
```

---

# 21. Voting Weight

Dynamic.

Inputs:

```text
Historical Accuracy

Calibration

Domain Expertise

Recent Performance
```

---

# 22. Weight Range

```text
0.0 - 1.0
```

---

# 23. Decision Threshold

Configurable.

Example:

```text
Approval ≥ 70%
```

---

# 24. Decision Types

```text
LONG
SHORT
REDUCE
EXIT
HOLD
RESEARCH
```

---

# 25. Decision Object

```json
{
  "decision_id":"uuid",
  "symbol":"BTC-USDT-PERP",
  "decision":"LONG",
  "confidence":0.81
}
```

---

# 26. Decision Confidence

Range:

```text
0.0 - 1.0
```

---

# 27. Evidence Requirements

Every decision requires:

```text
Market Evidence
Feature Evidence
Risk Review
```

---

# 28. Decision Audit Trail

Store:

```text
Votes
Challenges
Evidence
Outcome
```

---

# 29. Decision Events

```text
council.debate.started.v1
council.vote.completed.v1
council.decision.created.v1
```

---

# 30. Event Publishing

Published To:

```text
council.*
```

streams.

---

# 31. Council Memory Integration

Consumes:

```text
Research Memory
Decision Memory
Failure Memory
```

Governed by DOC-005.

---

# 32. Learning Integration

Council learns from:

```text
Trade Outcomes
Research Outcomes
Decision Outcomes
```

---

# 33. Performance Metrics

Track:

```text
Accuracy
Calibration
PnL Contribution
Sharpe Contribution
```

---

# 34. Calibration Engine

Measures:

```text
Predicted Confidence

vs

Actual Outcome
```

---

# 35. Agent Score

Range:

```text
0-100
```

Inputs:

```text
Accuracy
Consistency
Calibration
```

---

# 36. Dynamic Weight Adjustment

Weights automatically adjusted based on performance.

---

# 37. Promotion Rules

Promotion requires:

```text
Performance Threshold
Audit Review
Certification
```

---

# 38. Demotion Rules

Triggered by:

```text
Poor Performance
Risk Violations
Audit Violations
```

---

# 39. Retirement Rules

Requires:

```text
Audit Record
Performance Review
```

---

# 40. Shadow Agents

Allowed.

Purpose:

```text
Evaluate New Ideas
```

No decision authority.

---

# 41. Multi-Model Support

Supported:

```text
Open Models
Commercial Models
Hybrid Models
```

---

# 42. Model Independence

Council logic may not depend on a single provider.

---

# 43. Prompt Governance

Prompts governed by DOC-006.

---

# 44. Memory Governance

Memories governed by DOC-005.

---

# 45. Risk Governance

All decisions reviewed by Risk Engine.

---

# 46. Veto Authority

Risk Agent may veto.

Human oversight may veto.

---

# 47. Human Oversight

Humans may:

```text
Pause
Override
Review
```

All actions audited.

---

# 48. Council Replay

Must support:

```text
Debate Replay
Vote Replay
Decision Replay
```

---

# 49. Replay Source

```text
Parquet
Event Store
```

---

# 50. Replay Fidelity

Must reproduce:

```text
Inputs
Prompts
Votes
Decisions
```

---

# 51. Pydantic Models

Repository:

```text
src/council/models/
```

Required:

```text
Observation
Hypothesis
Vote
Decision
Challenge
```

---

# 52. Vote Model

```python
class Vote(BaseModel):

    vote_id: UUID

    agent_id: UUID

    decision: str

    confidence: float
```

---

# 53. Decision Model

```python
class Decision(BaseModel):

    decision_id: UUID

    symbol: str

    decision: str

    confidence: float
```

---

# 54. Event Contracts

Repository:

```text
contracts/events/council/
```

Required:

```text
debate_started.json
vote_completed.json
decision_created.json
```

---

# 55. Protobuf Contracts

Repository:

```text
contracts/proto/council/
```

Required:

```text
Vote.proto
Decision.proto
Challenge.proto
```

---

# 56. Debate Engine

Responsibilities:

```text
Aggregate Arguments

Generate Challenges

Evaluate Evidence
```

---

# 57. Challenge Generation

Required challenge types:

```text
Risk

Contrarian

Historical

Execution
```

---

# 58. Consensus Engine

Methods:

```text
Weighted Voting

Majority Voting

Unanimous Approval
```

Configurable.

---

# 59. Confidence Aggregation

Inputs:

```text
Votes
Weights
Evidence
```

Output:

```text
Council Confidence
```

---

# 60. Decision Ranking

Rank by:

```text
Confidence

Expected Return

Risk

Liquidity
```

---

# 61. Portfolio Recommendation Contract

Output:

```json
{
  "symbol":"BTC-USDT-PERP",
  "allocation":0.05,
  "confidence":0.82
}
```

---

# 62. Certification Framework

Required Tests:

```text
Debate
Voting
Replay
Learning
Calibration
Performance
```

---

# 63. Replay Certification

Verify:

```text
Decision Reproduction

Vote Reproduction

Audit Integrity
```

---

# 64. Calibration Certification

Verify:

```text
Confidence Accuracy
```

---

# 65. Performance Certification

Measure:

```text
Accuracy
Risk Adjusted Return
Consistency
```

---

# 66. Security Controls

Required:

```text
Authentication

Authorization

Audit Logging
```

---

# 67. Audit Controls

Record:

```text
Prompts

Votes

Decisions

Overrides
```

---

# 68. Scalability

Support:

```text
Single GPU

Multi GPU

Distributed Cluster
```

---

# 69. Repository Structure

```text
src/

 council/

   agents/
   debate/
   voting/
   decision/
   calibration/
   replay/
   learning/

contracts/

 council/
```

---

# 70. Definition Of Done

AI Council complete only if:

✓ Debate Engine Implemented

✓ Voting Engine Implemented

✓ Replay Compatible

✓ Learning Enabled

✓ Audited

✓ Certified

✓ Risk Integrated

✓ Human Override Enabled

---

# 71. Architectural Authority

All autonomous recommendations must originate from the AI Council.

No service may bypass Council governance.

---

# 72. Document Status

```text
Document:
SPEC-004

Name:
AI Council Specification

Version:
4.0.0

Status:
APPROVED

Classification:
Implementation Grade

Authority:
Specification
```
