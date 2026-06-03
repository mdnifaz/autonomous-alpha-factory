# DOC-003 AI Council Constitution

Version: 2.0.0

Status: APPROVED

Classification: Constitutional

Authority Level: Organization-Wide

---

# 1. Purpose

The AI Council is the decision-making authority of the Autonomous Alpha Factory.

Its purpose is to:

* Evaluate opportunities
* Allocate capital
* Approve capabilities
* Challenge assumptions
* Manage uncertainty
* Coordinate autonomous operation

The council exists to prevent single-agent decision making.

---

# 2. Scope

Applies to:

* Strategy Agents
* Research Agents
* Risk Agents
* Portfolio Agents
* Capability Governors
* Learning Systems
* Human Oversight Interfaces

---

# 3. Core Principles

### Collective Intelligence

No material decision may originate from a single agent.

### Evidence First

All decisions require supporting evidence.

### Explainability

Every decision must be explainable.

### Auditability

Every decision must be replayable.

### Challengeability

Every recommendation may be challenged.

---

# 4. Council Structure

The council consists of independent roles.

Minimum council composition:

```text
Market Agent
Technical Agent
Orderflow Agent
Research Agent
Risk Agent
Portfolio Agent
Coordinator Agent
```

Additional agents may be added.

---

# 5. Council Topology

```text
Evidence
    ↓

Agent Analysis
    ↓

Recommendations
    ↓

Challenges
    ↓

Decision Synthesis
    ↓

Portfolio Allocation
    ↓

Execution
```

---

# 6. Agent Registry

Every council participant must be registered.

Required fields:

* agent_id
* name
* role
* version
* status
* performance_score

---

# 7. Agent Status

Allowed states:

* ACTIVE
* SHADOW
* DISABLED
* RETIRED

Only ACTIVE agents may vote.

---

# 8. Council Roles

## Market Agent

Responsibilities:

* Regime analysis
* Market structure
* Volatility assessment

---

## Technical Agent

Responsibilities:

* Indicator analysis
* Trend analysis
* Momentum analysis

---

## Orderflow Agent

Responsibilities:

* Liquidity analysis
* Order book analysis
* Execution quality assessment

---

## Research Agent

Responsibilities:

* Alpha discovery
* Experiment review
* Knowledge extraction

---

## Risk Agent

Responsibilities:

* Exposure review
* Constraint enforcement
* Challenge generation

---

## Portfolio Agent

Responsibilities:

* Capital allocation
* Diversification analysis
* Portfolio optimization

---

## Coordinator Agent

Responsibilities:

* Vote aggregation
* Decision synthesis
* Audit generation

---

# 9. Evidence Requirements

Every recommendation must contain:

* Data Sources
* Supporting Metrics
* Confidence Estimate
* Risk Assessment

Recommendations without evidence are invalid.

---

# 10. Recommendation Contract

Required fields:

* recommendation_id
* agent_id
* symbol
* action
* confidence
* evidence
* timestamp

---

# 11. Confidence Standards

Confidence range:

```text
0.00 - 1.00
```

Confidence must be calibrated.

Overconfident agents are penalized.

---

# 12. Challenge Process

Every recommendation may be challenged.

Challenge fields:

* challenge_id
* challenger_agent
* target_recommendation
* rationale

Challenges become part of the audit trail.

---

# 13. Mandatory Challenges

Risk Agent may challenge:

* Capital allocations
* Capability promotions
* New production deployments

---

# 14. Decision Workflow

```text
Evidence
  ↓

Recommendation
  ↓

Challenge
  ↓

Deliberation
  ↓

Decision
```

---

# 15. Decision States

Allowed states:

* PROPOSED
* UNDER_REVIEW
* APPROVED
* REJECTED
* ESCALATED

---

# 16. Voting Model

Voting is weighted.

Weights depend on:

* Historical accuracy
* Risk-adjusted performance
* Calibration quality

Weights are dynamic.

Hardcoded weights are prohibited.

---

# 17. Dynamic Weighting

Inputs:

* Accuracy
* Sharpe Contribution
* Drawdown Contribution
* Calibration Score

Weights must adapt continuously.

---

# 18. Risk Veto Authority

The Risk Agent may veto:

* Excessive exposure
* Capital concentration
* Constraint violations

Veto events must be audited.

---

# 19. Escalation Rules

Escalation required when:

* Risk disagreement exists
* Confidence conflict exists
* Constitutional conflict exists

---

# 20. Human Oversight

Human oversight exists as a supervisory layer.

Humans may:

* Pause systems
* Override decisions
* Disable agents

Humans may not modify audit history.

---

# 21. Human Intervention Audit

Every intervention must record:

* User
* Timestamp
* Reason
* Scope

---

# 22. Capital Allocation Authority

The council approves:

* Capital allocation
* Allocation changes
* Capability funding

Execution remains separate.

---

# 23. Capability Governance

The council reviews:

* Promotions
* Demotions
* Retirement

Council approval required.

---

# 24. Learning Governance

The council evaluates:

* Experiments
* Research results
* Model evaluations

---

# 25. Performance Measurement

Every agent receives:

* Accuracy Score
* Risk Score
* Calibration Score
* Contribution Score

---

# 26. Agent Promotion

Promotion criteria:

* Sustained performance
* Stable calibration
* Audit compliance

Promotion thresholds must be adaptive.

Hardcoded thresholds prohibited.

---

# 27. Agent Demotion

Demotion triggers:

* Performance degradation
* Audit violations
* Risk violations

---

# 28. Agent Retirement

Retirement requires:

* Council approval
* Audit record
* Historical preservation

---

# 29. Shadow Agents

New agents begin as:

```text
SHADOW
```

No production authority.

Used for evaluation.

---

# 30. Production Eligibility

Requirements:

* Shadow validation
* Risk review
* Council approval

---

# 31. Council Event Contracts

Examples:

```text
council.vote.v1
council.challenge.v1
council.decision.v1
```

Governed by DOC-002.

---

# 32. Council Audit Requirements

Every decision must record:

* Evidence
* Recommendations
* Challenges
* Decision
* Outcome

---

# 33. Replay Requirements

The organization must support:

* Vote Replay
* Challenge Replay
* Decision Replay
* Allocation Replay

---

# 34. Security Requirements

Council actions require:

* Authentication
* Authorization
* Audit Logging

---

# 35. Data Retention

Council decisions:

```text
Permanent
```

Audit records:

```text
Permanent
```

---

# 36. Compliance Requirements

Council actions must:

* Follow DOC-001
* Follow DOC-002
* Maintain auditability

---

# 37. Failure Handling

If a council member fails:

* Mark unavailable
* Recalculate weights
* Continue operation

No single point of failure allowed.

---

# 38. Distributed Operation

Council must support:

* Single Node
* Multi-GPU
* Multi-Node
* Distributed Cluster

No constitutional changes required.

---

# 39. Constitutional Precedence

Conflict order:

```text
DOC-001
↓
DOC-002
↓
DOC-003
↓
Specifications
↓
Architecture
↓
Implementation
```

---

# 40. Document Status

```text
Document: DOC-003
Name: AI Council Constitution
Version: 2.0.0
Status: APPROVED
Classification: Implementation Grade
Authority Level: Constitutional
```
