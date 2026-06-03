# DOC-001 Appendix — Implementation Grade Extensions

## 28. Canonical JSON Serialization Rules

### Encoding

All serialized payloads must use:

```text
UTF-8
```

### Timestamps

All timestamps must use:

```text
ISO-8601 UTC
```

Example:

```text
2026-06-03T12:45:21.123Z
```

### Numbers

Monetary values:

```text
Decimal
```

Never:

```text
float
```

for persisted financial records.

### UUID Format

All identifiers:

```text
UUIDv7
```

Example:

```text
019731d2-0fbb-7f0e-b5d4-cb6f4b3fd771
```

---

## 29. Field Naming Standards

All fields use:

```text
snake_case
```

Allowed:

```text
asset_id
order_id
created_at
updated_at
```

Forbidden:

```text
assetId
AssetID
createdAt
```

### Boolean Fields

Must begin with:

```text
is_
has_
can_
```

Examples:

```text
is_active
has_position
can_trade
```

---

## 30. Required vs Optional Fields

Every schema must explicitly define:

### Required

Field must exist.

Example:

```text
order_id
symbol
side
quantity
```

### Optional

Field may be null.

Example:

```text
client_order_id
metadata
comment
```

### Forbidden

Implicit optional fields are prohibited.

---

## 31. Cross-Entity Relationships

### Asset → Symbol

```text
Asset
  └── Symbol
```

### Symbol → Market

```text
Symbol
  └── Market
```

### Signal → Vote

```text
Signal
  └── Vote
```

### Vote → Decision

```text
Vote
  └── Decision
```

### Decision → Allocation

```text
Decision
  └── Allocation
```

### Allocation → Order

```text
Allocation
  └── Order
```

### Order → Execution

```text
Order
  └── Execution
```

### Execution → Trade

```text
Execution
  └── Trade
```

### Trade → Portfolio

```text
Trade
  └── Portfolio
```

---

## 32. State Transition Constraints

### Order State Machine

Allowed:

```text
PENDING
  ↓
OPEN
  ↓
PARTIALLY_FILLED
  ↓
FILLED
```

Allowed:

```text
OPEN
  ↓
CANCELLED
```

Allowed:

```text
OPEN
  ↓
REJECTED
```

Forbidden:

```text
FILLED → OPEN
FILLED → PENDING
CANCELLED → OPEN
REJECTED → OPEN
```

---

### Capability State Machine

Allowed:

```text
RESEARCH
  ↓
BACKTEST
  ↓
SIMULATION
  ↓
PAPER
  ↓
LIMITED
  ↓
PRODUCTION
```

Retirement:

```text
ANY STATE
  ↓
RETIRED
```

---

## 33. Backward Compatibility Rules

### Non-Breaking Changes

Allowed:

```text
Add optional fields
Add metadata
Add new event versions
```

### Breaking Changes

Require:

```text
New major version
```

Examples:

```text
order.v1
order.v2
```

Both versions may coexist.

---

## 34. Deprecation Rules

Deprecation process:

```text
Active
  ↓
Deprecated
  ↓
Retired
```

Requirements:

```text
Deprecation notice
Migration path
Compatibility window
```

Minimum compatibility window:

```text
90 days
```

---

## 35. Data Ownership Rules

### Market Domain

Owner:

```text
Market Service
```

### Signal Domain

Owner:

```text
Strategy Services
```

### Council Domain

Owner:

```text
AI Council Service
```

### Portfolio Domain

Owner:

```text
Portfolio Service
```

### Risk Domain

Owner:

```text
Risk Service
```

### Execution Domain

Owner:

```text
Execution Service
```

### Learning Domain

Owner:

```text
Research Service
```

Only the owning service may modify its authoritative records.

---

## 36. Event Ownership Rules

Only designated producers may publish events.

Examples:

```text
market.*       → Market Services
signal.*       → Strategy Services
council.*      → Council Services
portfolio.*    → Portfolio Services
risk.*         → Risk Services
execution.*    → Execution Services
learning.*     → Research Services
```

Publishing unauthorized events is prohibited.

---

## 37. Domain Validation Matrix

Every entity must pass four validation layers.

### Layer 1

Schema Validation

Checks:

```text
Required fields
Missing fields
Unknown fields
```

### Layer 2

Type Validation

Checks:

```text
Strings
Decimals
Booleans
Enums
UUIDs
```

### Layer 3

Business Validation

Checks:

```text
Positive quantity
Valid side
Valid status
Valid capability state
```

### Layer 4

Relationship Validation

Checks:

```text
Asset exists
Symbol exists
Order exists
Capability exists
Decision exists
```

Failure at any layer results in rejection.

---

## 38. Canonical Compliance Requirements

A service is considered compliant only if:

```text
Uses canonical identifiers
Uses canonical symbols
Uses canonical events
Uses canonical models
Passes validation rules
Produces auditable records
```

Non-compliant services may not participate in production workflows.

---

## 39. Constitutional Precedence

Conflict resolution order:

```text
DOC-001 Canonical Domain Constitution

↓
Other Constitutions

↓
Specifications

↓
Architecture Documents

↓
Implementation Code
```

Implementation must conform upward.

---

## 40. Document Status

```text
Document: DOC-001
Name: Canonical Domain Constitution
Status: APPROVED
Version: 2.0.0
Classification: Implementation Grade
Authority Level: Constitutional
```
