# CodeInquest Review Matrix

Apply only relevant categories, but actively determine relevance rather than waiting for obvious filenames.

## Authentication

Check credential verification, password hashing, reset-token entropy/expiry/one-time use, account enumeration, MFA/passkey recovery, session fixation/rotation/revocation, cookie flags, token expiry, JWT issuer/audience/signature/algorithm validation, refresh rotation, OAuth state/nonce/PKCE, redirect URIs, SAML/OIDC claims, API-key scope, brute-force protection, and login rate limits.

## Authorization and Tenancy

Check every privileged operation for server-side enforcement. Look for IDOR/BOLA, role or ownership bypass, cross-tenant access, object-level permission gaps, admin escalation, missing org/workspace/project scope, user-controlled tenant IDs, inconsistent policies, UI-only authorization, bulk bypasses, job permission drift, stale policy caches, and unsafe impersonation.

## Input Validation and Injection

Trace untrusted data into SQL/NoSQL, shell/commands, paths, HTML/DOM, templates, headers, redirects, XML/XPath, LDAP, regex, expression engines, serializers, dynamic imports/eval, GraphQL, interpreters, AI prompts, and tools.

Validate type, shape, length, range, enum membership, encoding, canonicalization, and semantic constraints.

## Web and API Security

Check CSRF, CORS/origin policy, SSRF, open redirects, host-header trust, cache poisoning/key confusion, content types, methods, mass assignment, excessive data exposure, pagination abuse, GraphQL depth/complexity, webhook signatures/replay, API-key leakage, error leakage, and unsafe debug endpoints.

## Browser Security

Check reflected/stored/DOM XSS, unsafe HTML, URL/script contexts, CSP assumptions, postMessage origins, secret storage, frontend authorization assumptions, prototype pollution, and DOM clobbering when relevant.

## Files, Uploads, Paths, and Parsers

Check path traversal, symlink attacks, arbitrary read/write, archive traversal, decompression bombs, content validation, executable uploads, filename trust, parser exposure, temp files, permissions, XXE, unsafe deserialization, and parser resource exhaustion.

## Secrets and Sensitive Data

Check committed secrets, environment handling, logs, analytics, traces, errors, backups, client bundles, URLs, caches, notifications, exports, test fixtures, and debug tools.

## Cryptography

Check custom crypto, weak hashes, insecure randomness, nonce/IV reuse, signature verification, timing-sensitive comparison, authenticated encryption, key handling, password storage, token entropy, downgrade behavior, and TLS validation.

## Payments and Billing

Treat client financial values as untrusted. Check price/currency trust, integer/decimal representation, rounding, negatives/overflow, quantity bounds, coupons, discounts, taxes, trials, proration, subscription transitions, duplicate charges/refunds, idempotency, payment-intent ownership, webhook authenticity/replay/order, chargebacks, payouts, reconciliation, entitlement timing, and stale product metadata.

## Accounting and Ledger Integrity

Check balanced postings/invariants, immutable historical amounts, currency consistency, decimal precision, atomic posting, deduplication, unique external references, reversals, audit trail, ordering, eventual consistency, reconciliation, balance derivation, stale caches, negative-balance rules, race conditions, adjustment authorization, and backfill/migration correctness.

## Business-Logic Abuse

Check invalid transitions, workflow skipping, replay, duplicate submission, quota/rate-limit bypass, referral/promo abuse, entitlement bypass, oversell, approval bypass, self-approval, ownership transfer, invite abuse, timing windows, expired-resource reuse, feature-flag trust, and client-controlled workflow state.

## Concurrency and Distributed Integrity

Check lost updates, double execution, TOCTOU, missing transactions, isolation, lock scope, optimistic versioning, duplicate jobs, out-of-order events, non-idempotent retries, retry storms, partial distributed writes, compensating actions, race-prone caches, and leader-election assumptions.

## Database Correctness

Check constraints, foreign keys, uniqueness, nullability, transactions, migration safety, destructive migrations, backfills, pagination, stable ordering, isolation assumptions, query authorization, raw SQL, mass assignment, and soft-delete leakage.

## Database Performance

Check N+1, query-in-loop, repeated counts, unbounded scans, missing pagination, index support, inefficient search, unnecessary joins/columns, lock-heavy transactions, batch size, pool behavior, and chatty ORM usage.

Do not recommend an index without considering write cost and actual query shape.

## Application Performance

Check asymptotic complexity, repeated computation, parsing/serialization, memory copies, allocations, blocking I/O, unnecessarily sequential independent I/O, unbounded parallelism, batching, connection reuse, expensive middleware, large payloads, redundant API requests, render loops, bundle weight, memory retention, and worker throughput.

## Abuse and Resource Exhaustion

Check login/reset, search, exports, uploads, AI requests, email/SMS, report generation, webhooks, expensive queries, password hashing, crypto, recursive input, and fan-out endpoints. Verify limiting identity/scope is not spoofable.

## Dependencies and Supply Chain

Check unnecessary dependencies, install scripts, pinning policy, lockfile integrity, suspicious/abandoned packages, dependency confusion, typosquatting, package privilege, update automation, and build-time network/code execution.

Use current advisory data only when network/tool access is authorized and available.

## CI/CD

Check untrusted PR data in shell, `pull_request_target`, secret exposure, artifact/cache poisoning, excessive token permissions, unsafe checkout with secrets, mutable actions, deployment authorization, environment protection, and release integrity.

## Containers and Infrastructure

Check privileged/root containers, host mounts, dangerous capabilities, writable root filesystems, exposed services, public storage, broad IAM/RBAC, missing network controls, secrets in manifests, metadata-service exposure, insecure cloud/IaC policy, and weak TLS/proxy config.

## AI, LLMs, Agents, and Tools

Check direct/indirect prompt injection, retrieved instructions, cross-user memory/context, secret leakage into prompts, trusted model output, tool authorization/validation, destructive actions, excessive scope, sandbox boundaries, unsafe tool servers, generated-code execution, poisoned content, and confirmation requirements.

## Correctness

Check boundaries, nullability, numeric overflow, timezone/DST, locale, encoding/Unicode, ordering, nondeterminism, stale state, defaults, partial failure, error propagation, retry semantics, cancellation, cleanup, lifecycle, and compatibility.

## Code Reduction

Search for dead/unreachable code, unused exports/imports/types, duplicate functions/branches, wrapper-only functions, repeated validation/mapping, unnecessary state, obsolete flags/compatibility, redundant fallbacks, duplicate queries, redundant dependencies, speculative abstractions, factories/services/adapters without value, and excessive indirection.

Never reduce code at the expense of safety, clarity, performance, testability, or compatibility.

## API and Architecture Quality

Check leaky abstractions, duplicated business rules, cycles, hidden side effects, unclear ownership, inconsistent errors/validation/auth, god modules, needless layering, duplicated schemas/types, unstable public APIs, and poor domain boundaries.

## Tests

Check whether high-risk behavior has meaningful denial, tenant-isolation, invalid-input, replay/idempotency, payment-duplicate, ledger-invariant, concurrency, security-regression, migration, and error-path tests.

Do not measure test quality only by coverage percentage.

## Observability

Check missing audit events, sensitive logging, security-event visibility, correlation, payment/reconciliation traceability, job failure visibility, swallowed exceptions, metrics, and alertable invariants.

## Documentation and Configuration Drift

Check whether code conflicts with API contracts, permission docs, environment examples, deployment docs, migrations, security assumptions, feature flags, or runbooks. Treat docs as evidence, not proof.
