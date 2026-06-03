# SPEC-010-Repository-Layout-Specification.md

## Document Metadata

| Field          | Value                                                |
| -------------- | ---------------------------------------------------- |
| Document       | SPEC-010                                             |
| Name           | Repository Layout Specification                      |
| Version        | 4.0.0                                                |
| Status         | APPROVED                                             |
| Classification | Implementation Grade                                 |
| Authority      | Specification                                        |
| Depends On     | DOC-001, DOC-002, DOC-007, SPEC-001 through SPEC-009 |

---

# 1. Purpose

This specification defines the canonical repository structure for the Autonomous Alpha Factory.

Objectives:

* Consistency
* Scalability
* Maintainability
* Discoverability
* Modularization
* Service Isolation
* Governance

No implementation may violate this layout without formal architectural approval.

---

# 2. Core Principles

### Domain Driven Structure

Repositories organized by business domains.

---

### No Hardcoded Dependencies

All dependencies flow through contracts.

---

### Contracts Before Code

Contracts are authoritative.

---

### Service Isolation

Services own their domains.

---

### Replay First

Replay support is mandatory.

---

# 3. Repository Root Layout

```text
autonomous-alpha-factory/

├── docs/
├── contracts/
├── schemas/
├── database/
├── infrastructure/
├── deployment/
├── tools/
├── tests/
├── src/
└── scripts/
```

---

# 4. Documentation Layer

```text
docs/

├── constitutional/
├── specifications/
├── architecture/
├── operations/
├── runbooks/
├── decisions/
```

---

# 5. Constitutional Documents

```text
docs/constitutional/

DOC-001.md
DOC-002.md
DOC-003.md
...
```

---

# 6. Specifications

```text
docs/specifications/

SPEC-001.md
SPEC-002.md
SPEC-003.md
...
```

---

# 7. Architecture Documents

```text
docs/architecture/

ARCH-001.md
ARCH-002.md
ARCH-003.md
...
```

---

# 8. Contracts Layer

```text
contracts/

events/
proto/
rest/
graphql/
```

---

# 9. Event Contracts

```text
contracts/events/

market/
portfolio/
execution/
risk/
council/
capability/
system/
```

---

# 10. Protobuf Contracts

```text
contracts/proto/

market/
portfolio/
execution/
risk/
council/
capability/
```

---

# 11. Schema Layer

```text
schemas/

market/
portfolio/
execution/
risk/
council/
capability/
```

---

# 12. Database Layer

```text
database/

ddl/
migrations/
seeds/
views/
```

---

# 13. DDL Structure

```text
database/ddl/

market/
portfolio/
execution/
risk/
audit/
```

---

# 14. Infrastructure Layer

```text
infrastructure/

terraform/
ansible/
monitoring/
observability/
```

---

# 15. Deployment Layer

```text
deployment/

docker/
kubernetes/
helm/
```

---

# 16. Tools Layer

```text
tools/

research/
migration/
certification/
generation/
```

---

# 17. Test Layer

```text
tests/

unit/
integration/
system/
performance/
certification/
```

---

# 18. Source Root

```text
src/
```

All production code resides here.

---

# 19. Source Domains

```text
src/

exchange/
event_bus/
storage/
council/
capability/
market/
execution/
risk/
portfolio/
```

---

# 20. Exchange Domain

```text
src/exchange/

gateway/
adapters/
models/
contracts/
certification/
```

---

# 21. Event Bus Domain

```text
src/event_bus/

publisher/
consumer/
routing/
replay/
monitoring/
```

---

# 22. Storage Domain

```text
src/storage/

postgres/
parquet/
vector/
backup/
recovery/
```

---

# 23. AI Council Domain

```text
src/council/

agents/
debate/
voting/
decision/
learning/
```

---

# 24. Capability Graph Domain

```text
src/capability/

registry/
graph/
ranking/
evolution/
```

---

# 25. Market Domain

```text
src/market/

ingestion/
normalization/
validation/
analytics/
replay/
```

---

# 26. Execution Domain

```text
src/execution/

router/
algorithms/
fills/
analytics/
replay/
```

---

# 27. Risk Domain

```text
src/risk/

limits/
stress/
exposure/
liquidity/
kill_switch/
```

---

# 28. Portfolio Domain

```text
src/portfolio/

allocation/
optimization/
rebalancing/
analytics/
```

---

# 29. Shared Domain

```text
src/shared/
```

Purpose:

Only generic reusable code.

---

# 30. Shared Modules

Allowed:

```text
logging
config
security
utilities
serialization
```

---

# 31. Prohibited Shared Modules

Not allowed:

```text
business_logic
strategy_logic
portfolio_logic
```

---

# 32. Service Boundaries

Services communicate through:

```text
Events
Contracts
APIs
```

Never direct internal coupling.

---

# 33. Package Structure

Every package requires:

```text
__init__.py

models/
services/
contracts/
tests/
```

---

# 34. Configuration Layer

```text
config/

development/
staging/
production/
```

---

# 35. Environment Configuration

Required:

```text
.env.example
```

Never commit secrets.

---

# 36. Secrets Management

Required:

```text
Vault
Secret Manager
KMS
```

Forbidden:

```text
Hardcoded Credentials
```

---

# 37. Logging Structure

```text
src/shared/logging/
```

Centralized.

---

# 38. Monitoring Structure

```text
src/shared/monitoring/
```

---

# 39. Security Structure

```text
src/shared/security/
```

---

# 40. Replay Structure

Every domain must contain:

```text
replay/
```

module.

---

# 41. Certification Structure

Every domain must contain:

```text
certification/
```

module.

---

# 42. Event Structure

Every domain must define:

```text
events/
```

contracts.

---

# 43. Model Structure

Every domain must define:

```text
models/
```

---

# 44. Service Structure

Every domain must define:

```text
services/
```

---

# 45. Interface Structure

Every domain must define:

```text
interfaces/
```

---

# 46. Adapter Structure

External integrations belong in:

```text
adapters/
```

---

# 47. Test Organization

```text
unit/
integration/
system/
performance/
```

Mandatory.

---

# 48. Unit Tests

Purpose:

```text
Component Validation
```

---

# 49. Integration Tests

Purpose:

```text
Service Interaction Validation
```

---

# 50. System Tests

Purpose:

```text
End-to-End Validation
```

---

# 51. Performance Tests

Purpose:

```text
Latency
Throughput
Scalability
```

---

# 52. Certification Tests

Purpose:

```text
Specification Compliance
```

---

# 53. Documentation Standards

Every service requires:

```text
README.md
ARCHITECTURE.md
RUNBOOK.md
```

---

# 54. Naming Standards

Directories:

```text
snake_case
```

Files:

```text
snake_case
```

Classes:

```text
PascalCase
```

---

# 55. Versioning Standards

Format:

```text
MAJOR.MINOR.PATCH
```

---

# 56. Migration Standards

All schema changes require:

```text
Migration
Rollback
Verification
```

---

# 57. Branch Strategy

```text
main
develop
feature/*
hotfix/*
```

---

# 58. Commit Standards

Format:

```text
feat:
fix:
refactor:
docs:
test:
```

---

# 59. Code Ownership

Every domain requires:

```text
Owner
Reviewer
Approver
```

---

# 60. Architectural Governance

Changes to:

```text
contracts
schemas
architecture
```

require review.

---

# 61. Monorepo Governance

Repository is a monorepo.

Benefits:

```text
Shared Contracts
Unified Governance
Consistent Standards
```

---

# 62. Future Expansion

Supports:

```text
Multi GPU
Distributed Systems
Multiple Exchanges
Additional Services
```

without repository redesign.

---

# 63. Repository Health Metrics

Track:

```text
Test Coverage
Documentation Coverage
Dependency Health
Build Health
```

---

# 64. Build Standards

Every component requires:

```text
Lint
Type Check
Tests
Certification
```

---

# 65. CI/CD Standards

Pipeline Stages:

```text
Build
Test
Certification
Security Scan
Deploy
```

---

# 66. Definition Of Done

Repository compliant only if:

✓ Structure Compliant

✓ Contract Compliant

✓ Replay Support Present

✓ Certification Present

✓ Documentation Present

✓ Tests Present

---

# 67. Architectural Authority

This specification governs repository organization.

All implementations must follow this structure.

---

# 68. Document Status

```text
Document:
SPEC-010

Name:
Repository Layout Specification

Version:
4.0.0

Status:
APPROVED

Classification:
Implementation Grade

Authority:
Specification
```
