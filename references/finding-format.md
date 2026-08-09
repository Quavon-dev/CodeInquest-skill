# CodeInquest Finding Format

## Finding Classes

Use one of:

`security`, `auth`, `authorization`, `tenancy`, `payments`, `accounting`, `business-logic`, `data-integrity`, `correctness`, `performance`, `code-reduction`, `maintainability`, `dependency`, `infra-cicd`, `ai-agent`, `testing`, `observability`.

## Severity and Value

For vulnerabilities and integrity/correctness failures:

- `critical`
- `high`
- `medium`
- `low`

For non-defect engineering opportunities:

- `high-value`
- `medium-value`
- `low-value`

Do not call style preferences vulnerabilities.

## Confidence

Use `confirmed`, `high`, `medium`, or `low`.

Low-confidence suspicions normally belong in proof gaps rather than the primary findings list.

## Required Finding Shape

```markdown
## CI-XXX — Title

Class:
Severity/Value:
Confidence:
Status:
Affected:
Root cause:

### Evidence
Concrete repository evidence with file and line references.

### Path
For security/integrity issues: source/entry point → controls → sink/effect.

### Impact
Realistic consequence.

### Preconditions
Required role, state, deployment condition, attacker capability, or scale.

### Counterevidence
Strongest evidence that could disprove or mitigate the finding and why it does or does not close it.

### Recommendation
Smallest robust root-cause fix.

### Validation
What was actually tested/traced and the result.

### Engineering effect
Expected security/correctness/performance/code-size/maintenance effect.

### Related locations
All sibling instances sharing the root cause.
```

Omit non-applicable sections only for simple engineering opportunities. Never omit evidence.

## Security Status

Use:

- `validated`
- `reportable-static`
- `deferred`
- `suppressed`

`reportable-static` requires a strong source/control/sink/reachability argument even without runtime reproduction.

## Performance Findings

Include the hot path, current complexity/query/I/O behavior, trigger/scale condition, evidence, proposed change, expected effect, and benchmark/profile status.

Never invent percentage speedups.

## Code-Reduction Findings

Include exact duplicated/dead/unnecessary locations, reusable existing primitives, safe consolidation/removal plan, compatibility risk, and approximate removable lines only when reasonably measurable.

## Deduplication

Merge findings that share one root cause while preserving every affected location.

Do not merge distinct authorization failures merely because both involve permissions.

## Executive Priority

Rank remediation by:

1. exploitability/data-loss/financial-loss risk;
2. privilege and blast radius;
3. correctness and integrity impact;
4. performance/scalability impact;
5. reduction and maintenance value;
6. implementation risk/cost.

A one-line authorization bug can outrank a thousand-line cleanup.

## Positive Controls

Record important controls worth preserving when they materially reduce risk, such as centralized authorization, strong ledger invariants, idempotent payment processing, verified webhooks, safe query APIs, defensive rate limits, and critical-boundary tests.
