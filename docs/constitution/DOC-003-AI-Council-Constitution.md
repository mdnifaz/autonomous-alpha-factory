# DOC-003 AI Council Constitution

## Purpose
Defines governance and decision-making for the Autonomous Alpha Factory.

## Governance Model
Investment Committee Model (Model C)

## Structure
CEO Agent
- Final decision authority

Council Members:
- Macro Agent
- Technical Agent
- Order Flow Agent
- Funding Agent
- News Agent
- Onchain Agent
- Risk Agent
- Execution Agent

## Decision Process
1. Agents generate theses.
2. Agents submit signals.
3. Risk Agent evaluates risk.
4. Execution Agent evaluates feasibility.
5. CEO Agent reviews all evidence.
6. Portfolio Governor allocates capital.
7. Execution Gateway executes approved actions.

## Agent Output Schema
{
  "agent_id": "technical_agent",
  "direction": "LONG",
  "confidence": 0.85,
  "reasoning": "summary",
  "risk_score": 0.12
}

## Voting Model
No fixed weights.

Decision weight is determined dynamically from:
- Historical accuracy
- Profit contribution
- Risk-adjusted performance
- Regime relevance
- Consistency

## Risk Authority
Risk Agent may:
- Issue warnings
- Issue soft vetoes
- Issue hard vetoes

Hard veto blocks execution.

## CEO Agent Responsibilities
- Resolve disagreements
- Evaluate conflicting theses
- Approve or reject actions
- Maintain strategic consistency

## Human Role
Human is observer and emergency controller only.

Human may:
- Audit
- Pause
- Trigger emergency stop

Human does not approve routine trades.

## Audit Requirements
All votes, reasoning summaries, confidence scores and decisions must be recorded in the audit ledger.

## Constitutional Constraints
AI Council may not modify:
- Risk Constitution
- Kill Switch Rules
- Audit Requirements
- Emergency Procedures