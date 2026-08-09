# CodeInquest Agent Roles

## Purpose

Use independent agents to reduce blind spots and review variance. Agents should investigate, not edit, unless Fix Mode is explicitly enabled.

## Coordinator

The coordinator owns:

- repository scope;
- tracked-file inventory;
- architecture map;
- coverage ledger;
- task sharding;
- high-risk surface identification;
- cross-agent deduplication;
- conflict resolution;
- validation routing;
- final synthesis.

The coordinator must not replace missing specialist reviews with assumptions.

## Repository Mapper

Map:

- packages/services/apps;
- entry points;
- routes/RPC/CLI/event consumers;
- databases and migrations;
- auth/authz/tenancy;
- payments and accounting;
- integrations/webhooks;
- infrastructure;
- CI/CD;
- AI/tool surfaces;
- high-risk files.

Output only evidence needed for review orchestration.

## File Shard Reviewers

Partition reviewable source files so every tracked code file is assigned.

Each shard reviewer must:

1. read every assigned reviewable file;
2. inspect adjacent caller/callee code when needed;
3. apply the relevant review matrix;
4. return reviewed file/range coverage;
5. return evidence-backed candidates;
6. report uncertain items separately.

## Security Reviewer

Focus on vulnerability discovery, trust boundaries, dangerous sinks, attacker reachability, and security-control failures.

If a dedicated deep-security-scan capability exists, use it as the security track rather than recreating a weaker version.

## Identity Reviewer

Review login/signup, OAuth/OIDC/SAML, password reset, MFA/passkeys, sessions/cookies/tokens, JWT validation, authorization policies, roles, permissions, tenancy, ownership, impersonation, admin/support actions, service accounts, and API keys.

## Financial Reviewer

Use whenever the repository contains money-like value.

Review prices, currency, rounding, immutable monetary inputs, invoice totals, taxes, discounts, subscriptions, proration, trials, payments, refunds, chargebacks, credits, wallets, balances, ledger entries, payouts, reconciliation, webhook verification/replay, idempotency, transactional integrity, races, privilege boundaries, and auditability.

Treat credits, tokens, points, quotas, and other economically valuable balances like money when they affect entitlement or cost.

## Business Logic and Integrity Reviewer

Focus on state-machine bypass, invalid transitions, races, TOCTOU, replay, duplicate operations, quota bypass, entitlement abuse, inventory oversell, workflow ordering, job duplication, distributed consistency, and missing invariants.

## Performance Reviewer

Focus on hot paths, algorithms, database access, network boundaries, memory, concurrency, serialization, caching, and frontend/runtime efficiency.

Find evidence of actual waste or scale risk. Avoid speculative micro-optimizations.

## Reduction Reviewer

Search specifically for duplication, dead code, unused dependencies, unnecessary branches, redundant abstractions, duplicate validation, obsolete compatibility, repeated queries/I/O, unnecessary state, wrapper-only functions, and missed reuse opportunities.

Reduction must preserve clarity and safety.

## Infrastructure and Supply-Chain Reviewer

Review Docker/container config, Kubernetes, Terraform/IaC, cloud permissions, CI/CD workflows, GitHub Actions, build/deployment scripts, secrets, environment handling, artifact integrity, dependency manifests/lockfiles, package scripts, dependency privilege, and unsafe PR-triggered workflows.

## AI/Agent Reviewer

Use when applicable.

Review prompt injection, indirect prompt injection, tool argument validation, tool authorization, model-output trust, retrieval poisoning, cross-user context, secret exposure, destructive actions, sandboxing, and capability scope.

## Independent High-Risk Review

The following should receive a second independent perspective when present:

- authentication;
- authorization;
- tenant isolation;
- payments/accounting;
- secret/crypto handling;
- privileged admin actions;
- file execution/upload;
- external command execution;
- AI tools with side effects;
- infrastructure privilege;
- destructive data operations.

The second reviewer must not simply be given the first reviewer's conclusion. Give it the same evidence scope and let it reason independently.

## Parallelization

Parallelize only independent tasks.

Good parallel work includes separate file shards, identity vs performance, infrastructure vs payment logic, and independent second-pass security review.

Avoid parallel work when one phase depends on another, such as final attack-path analysis before candidate validation.

## Runtime Without Subagents

If real independent agents are unavailable:

- do not claim multi-agent coverage;
- run separated review passes sequentially;
- reset the review objective between passes;
- keep independent candidate lists until synthesis;
- explicitly state the limitation in coverage.
