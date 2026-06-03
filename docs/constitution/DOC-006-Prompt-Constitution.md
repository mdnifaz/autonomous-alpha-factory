# DOC-006 Prompt Constitution

Version: 2.0.0

Status: APPROVED

Classification: Constitutional

Authority Level: Organization-Wide

---

# 1. Purpose

The Prompt Constitution governs all instruction systems used within the Autonomous Alpha Factory.

This includes:

* Agent Prompts
* System Prompts
* Council Prompts
* Research Prompts
* Evaluation Prompts
* Learning Prompts
* Simulation Prompts
* Oversight Prompts

The objective is to ensure consistency, auditability, reproducibility, and continuous improvement.

---

# 2. Scope

Applies to:

* AI Council
* Strategy Agents
* Research Agents
* Risk Agents
* Portfolio Agents
* Learning Systems
* Evaluation Systems
* Human Oversight Interfaces

---

# 3. Core Principles

### Prompts Are Code

Prompts are governed artifacts.

Prompt changes are treated as software changes.

---

### Version Everything

Every prompt must be versioned.

---

### Reproducibility

A historical decision must be reproducible using:

* Prompt Version
* Model Version
* Inputs
* Memory State

---

### Auditability

Prompt usage must be auditable.

---

### Continuous Improvement

Prompt evolution is encouraged.

Uncontrolled prompt drift is prohibited.

---

# 4. Prompt Definition

A prompt is any instruction set influencing model behavior.

Examples:

* System Prompt
* Agent Prompt
* Evaluation Prompt
* Reflection Prompt
* Research Prompt

---

# 5. Prompt Identity

Every prompt requires:

* prompt_id
* name
* version
* owner
* status
* created_at

Identifiers use UUIDv7.

---

# 6. Prompt Registry

All prompts must exist in a centralized registry.

Registry fields:

* prompt_id
* name
* version
* owner
* status
* checksum
* performance_score

Unregistered prompts may not run in production.

---

# 7. Prompt Categories

Supported categories:

```text
SYSTEM
AGENT
COUNCIL
RESEARCH
EVALUATION
REFLECTION
LEARNING
OVERSIGHT
```

---

# 8. Prompt Lifecycle

States:

```text
DRAFT
TESTING
SHADOW
APPROVED
PRODUCTION
DEPRECATED
RETIRED
```

---

# 9. Prompt Ownership

Every prompt has a designated owner.

Owners are responsible for:

* Maintenance
* Validation
* Compliance
* Retirement

---

# 10. Prompt Structure Standards

Every prompt should define:

* Role
* Objective
* Constraints
* Inputs
* Outputs
* Failure Conditions

---

# 11. Role Definition

Example:

```text
You are the Risk Agent.
```

Role ambiguity is prohibited.

---

# 12. Objective Definition

Every prompt must define a measurable objective.

Example:

```text
Identify portfolio risks.
```

---

# 13. Constraint Definition

Examples:

* Risk Limits
* Constitutional Rules
* Capital Limits
* Audit Requirements

Constraints are mandatory.

---

# 14. Input Contracts

Every prompt must define expected inputs.

Examples:

* Market Data
* Signals
* Portfolio State
* Risk State

---

# 15. Output Contracts

Every prompt must define expected outputs.

Examples:

* Recommendation
* Risk Assessment
* Allocation Proposal

Free-form production outputs are prohibited.

---

# 16. Prompt Versioning

Version format:

```text
MAJOR.MINOR.PATCH
```

---

# 17. Version Governance

Breaking changes:

```text
Major Version
```

Non-breaking changes:

```text
Minor Version
```

Fixes:

```text
Patch Version
```

---

# 18. Prompt Validation

Every prompt must pass:

* Syntax Validation
* Structural Validation
* Contract Validation
* Constitutional Validation

---

# 19. Constitutional Validation

Prompts must comply with:

* DOC-001
* DOC-002
* DOC-003
* DOC-004
* DOC-005

Violations are prohibited.

---

# 20. Prompt Testing

Required tests:

* Unit Evaluation
* Scenario Evaluation
* Stress Evaluation
* Adversarial Evaluation

---

# 21. Shadow Deployment

New prompts begin in:

```text
SHADOW
```

No production authority.

Used for comparison.

---

# 22. Prompt Promotion

Promotion requires:

* Test Results
* Audit Review
* Council Approval

---

# 23. Prompt Demotion

Triggers:

* Performance Degradation
* Audit Violations
* Risk Violations

---

# 24. Prompt Retirement

Requires:

* Historical Preservation
* Audit Record
* Registry Update

---

# 25. Prompt Performance

Metrics:

* Accuracy
* Consistency
* Calibration
* Compliance
* Utility

---

# 26. Prompt Evaluation

Evaluation must use:

* Historical Scenarios
* Simulation
* Paper Evaluation
* Production Observation

---

# 27. Prompt Benchmarking

Every production prompt must have benchmarks.

Examples:

* Baseline Prompt
* Previous Version
* Control Group

---

# 28. Prompt Comparison

Comparisons require:

* Same Inputs
* Same Context
* Same Evaluation Criteria

---

# 29. Reflection Prompts

Reflection prompts analyze:

* Decisions
* Failures
* Opportunities

Purpose:

Continuous improvement.

---

# 30. Learning Prompts

Learning prompts generate:

* Insights
* Knowledge
* Research Findings

Outputs become memory objects.

---

# 31. Council Prompt Governance

Council prompts govern:

* Voting
* Deliberation
* Challenge Generation
* Decision Synthesis

---

# 32. Risk Prompt Governance

Risk prompts may:

* Challenge recommendations
* Veto allocations
* Escalate concerns

---

# 33. Prompt Security

Prompts require:

* Authentication
* Authorization
* Audit Logging

Unauthorized modifications prohibited.

---

# 34. Prompt Integrity

Every prompt stores:

* Checksum
* Version
* Owner

Tampering detection required.

---

# 35. Prompt Audit Requirements

Every execution records:

* Prompt Version
* Model Version
* Inputs
* Outputs
* Timestamp

---

# 36. Prompt Memory Integration

Prompts may consume:

* Working Memory
* Historical Memory
* Organizational Knowledge

Governed by DOC-005.

---

# 37. Prompt Event Contracts

Examples:

```text
prompt.created.v1
prompt.updated.v1
prompt.promoted.v1
prompt.retired.v1
```

Governed by DOC-002.

---

# 38. Multi-Model Compatibility

Prompts must support:

* Local Models
* Hosted Models
* Future Models

Prompts must not depend on a single provider.

---

# 39. Model Independence

Prompts may not contain:

* Provider-specific assumptions
* Vendor-specific dependencies

Portability required.

---

# 40. Context Management

Prompts must define:

* Context Sources
* Context Limits
* Context Priorities

---

# 41. Prompt Composition

Complex prompts may be composed of:

* System Layer
* Constitutional Layer
* Role Layer
* Task Layer

---

# 42. Prompt Governance Council

Prompt governance decisions require:

* Evaluation Evidence
* Audit Compliance
* Approval Process

---

# 43. Distributed Operation

Prompt infrastructure must support:

* Single GPU
* Multi GPU
* Multi Node
* Distributed Cluster

---

# 44. Failure Handling

Prompt failures must record:

* Inputs
* Outputs
* Error State
* Recovery Actions

---

# 45. Continuous Optimization

Prompt systems should improve through:

* Evaluation
* Learning
* Feedback
* Research

---

# 46. Constitutional Precedence

Conflict order:

```text
DOC-001
↓
DOC-002
↓
DOC-003
↓
DOC-004
↓
DOC-005
↓
DOC-006
↓
Specifications
↓
Architecture
↓
Implementation
```

---

# 47. Document Status

```text
Document: DOC-006
Name: Prompt Constitution
Version: 2.0.0
Status: APPROVED
Classification: Implementation Grade
Authority Level: Constitutional
```
