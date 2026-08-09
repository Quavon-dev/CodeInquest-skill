# CodeInquest Coverage Ledger

## Goal

Make repository-wide coverage auditable. A review is not complete because agents say they "looked through the repo."

## Canonical Inventory

Prefer the version-control tracked-file inventory. For Git repositories, the equivalent of `git ls-files` is the normal starting point.

Do not treat `.git`, dependency caches, build caches, IDE caches, or runtime temp directories as source scope.

## File Classification

Every inventory entry receives one primary classification:

- `source`
- `test`
- `schema-migration`
- `config-security`
- `infra-cicd`
- `dependency`
- `operational-doc`
- `generated-vendor`
- `binary-asset`
- `excluded`

## Ledger Fields

Track at least:

| Field | Meaning |
|---|---|
| path | Repository-relative path |
| classification | Primary file class |
| language/type | Detected language or format |
| risk | critical/high/medium/normal |
| assigned_review | Reviewer/shard |
| review_passes | Completed independent passes |
| security_review | yes/no/not-applicable |
| correctness_review | yes/no/not-applicable |
| performance_review | yes/no/not-applicable |
| reduction_review | yes/no/not-applicable |
| status | pending/reviewed/excluded/blocked |
| findings | Finding IDs |
| exclusion_reason | Required when excluded |
| proof_gap | Required when blocked |

## High-Risk Classification

Mark at least high risk when a file directly controls authentication, authorization, sessions/tokens, tenant isolation, payments/billing, balances/ledger/accounting, secrets/crypto, admin/impersonation, uploads/execution, process execution, unsafe parsing, public API entry points, webhooks, invariant-sensitive migrations, AI tools with effects, privileged infrastructure, CI/CD secrets/deployment, or destructive data operations.

High-risk files should receive two independent relevant review passes when real multi-agent execution is available.

## Line-by-Line Meaning

For reviewable source/config files, "line-by-line" means the reviewer reads the complete file and reasons about executable declarations, control flow, data flow, security boundaries, configuration, and meaningful context.

It does not mean generating commentary for every line.

Whitespace, generated formatting, vendored code, binary data, and non-semantic boilerplate do not require artificial per-line commentary.

## Exclusions

Allowed exclusions include binaries that cannot be semantically reviewed as source, vendored third-party code when supply-chain review is appropriate, generated artifacts whose source/generator is reviewed, build output, lockfile bodies from semantic code review while dependency integrity is still assessed, and assets with no executable/security role.

Each exclusion requires a reason. Security-relevant generated output may still require targeted review.

## Coverage Reconciliation

Before completion:

1. count inventory files;
2. count reviewed files;
3. count excluded files;
4. count blocked files;
5. verify `reviewed + excluded + blocked == inventory`;
6. verify no reviewable row remains pending;
7. verify high-risk independent-pass requirements;
8. verify findings reference existing ledger paths;
9. state blocked proof.

## Coverage Labels

Use:

- `complete`: all required rows closed and high-risk pass requirements met;
- `partial`: at least one required review or proof step is blocked/deferred;
- `failed`: inventory or review execution is too incomplete to support a responsible result.

Never convert `partial` to `complete` because remaining files appear low risk.
