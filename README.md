# CodeInquest

An exhaustive multi-agent repository audit skill for security, auth, payments, accounting, correctness, performance, code reduction, and engineering quality.

CodeInquest turns an AI coding agent into a repository-wide review coordinator. It inventories the requested codebase, assigns independent review tracks, inspects every reviewable source and configuration file, validates important findings, reconciles coverage, and produces one evidence-driven audit instead of a shallow list of guesses.

## What CodeInquest reviews

CodeInquest covers, when applicable:

- security vulnerabilities and realistic attack paths;
- authentication, sessions, identity, authorization, permissions, ownership, and tenant isolation;
- payments, billing, subscriptions, refunds, credits, balances, accounting, and ledger integrity;
- business-logic abuse, race conditions, idempotency, distributed consistency, and data integrity;
- SQL/NoSQL, command, path, template, XSS, SSRF, deserialization, prompt, and other injection classes;
- secrets, cryptography, privacy, rate limiting, resource exhaustion, and abuse controls;
- database correctness, migrations, query efficiency, N+1 patterns, and index-sensitive hot paths;
- application performance, concurrency, memory, I/O, serialization, batching, and scalability;
- dead code, duplication, obsolete compatibility paths, unnecessary abstractions, dependencies, and removable complexity;
- CI/CD, GitHub Actions, containers, Kubernetes, infrastructure, IAM/RBAC, and supply-chain risk;
- AI/LLM/agent systems, tool authorization, prompt injection, retrieved-content trust, and cross-user context isolation;
- tests, observability, auditability, API contracts, and configuration drift.

## Core idea: accountable coverage

CodeInquest does not treat "I looked through the repository" as proof of a complete audit.

It builds a coverage ledger from the repository inventory. Every reviewable file must reach a terminal state such as reviewed, explicitly excluded, or blocked with a documented proof gap. High-risk surfaces should receive an independent second review when the runtime supports real subagents.

A repository audit may only be reported as complete when the ledger supports that claim.

## Multi-agent review

When the coding environment supports independent agents, CodeInquest coordinates specialized tracks such as:

- repository mapping and coverage;
- security and attack surface;
- identity, authentication, authorization, and tenancy;
- payments, billing, accounting, and financial integrity;
- business logic, concurrency, and data integrity;
- performance and scalability;
- code reduction, duplication, and maintainability;
- infrastructure, CI/CD, dependencies, and secrets;
- AI, agent, tool, and prompt-injection security.

High-risk code should not rely on one review perspective. When subagents are unavailable, CodeInquest performs separated sequential review passes and must disclose that limitation instead of claiming multi-agent coverage.

## Installation

### One command — recommended

Install CodeInquest globally for Claude Code, Codex, and GitHub Copilot:

```bash
npx skills add Quavon-dev/CodeInquest-skill --skill codeinquest -g -a claude-code -a codex -a github-copilot -y
```

Install for only one agent:

```bash
npx skills add Quavon-dev/CodeInquest-skill --skill codeinquest -g -a claude-code -y
npx skills add Quavon-dev/CodeInquest-skill --skill codeinquest -g -a codex -y
npx skills add Quavon-dev/CodeInquest-skill --skill codeinquest -g -a github-copilot -y
```

Interactive installation:

```bash
npx skills add Quavon-dev/CodeInquest-skill --skill codeinquest -g
```

Project-local installation:

```bash
npx skills add Quavon-dev/CodeInquest-skill --skill codeinquest -a claude-code -y
```

Verify a global installation:

```bash
npx skills ls -g -a claude-code -a codex -a github-copilot
```

### Ask your AI coding agent to install it

Paste this into a coding agent with terminal access:

```text
Install CodeInquest globally from https://github.com/Quavon-dev/CodeInquest-skill as an Agent Skill for the coding agents available in this environment.

Use the standard Agent Skills CLI. Install only the `codeinquest` skill and explicitly target only agents that support global skill installation. Do not use an unrestricted global auto-install that includes project-only agents. If the CLI is unavailable, use the active coding agent's documented global skill directory instead. Do not execute untrusted remote shell scripts.

After installation, verify that SKILL.md and its references directory exist, that the YAML frontmatter is valid, and that the active agent can discover the `codeinquest` skill. Do not modify unrelated files. Tell me the exact installation path and verification result when finished.
```

### Manual installation

Claude Code:

```bash
git clone --depth 1 https://github.com/Quavon-dev/CodeInquest-skill.git ~/.claude/skills/codeinquest
```

Agents using the shared `.agents` skill directory:

```bash
git clone --depth 1 https://github.com/Quavon-dev/CodeInquest-skill.git ~/.agents/skills/codeinquest
```

## Run a full audit

A simple invocation is enough when the skill is discoverable:

```text
Use CodeInquest to perform a complete repository-wide audit. Review the entire repository scope, use independent agents where available, validate important findings, reconcile the coverage ledger, and report security, auth, payments/accounting, correctness, performance, code-reduction, infrastructure, dependency, AI-agent, testing, and observability findings. Do not modify code unless I explicitly ask for fixes.
```

For a stricter audit:

```text
Run CodeInquest against this entire repository. I want accountable full-repository coverage, not sampling. Inventory all tracked files, review every reviewable source/config file, independently double-review high-risk surfaces where subagents are available, use specialized installed security/testing/framework/database/infrastructure skills when relevant, validate material security findings, trace realistic attack paths, inspect auth/authorization/tenant boundaries, payments/accounting/ledger invariants, concurrency and business logic, database and application performance, dead/duplicate/unnecessary code, dependencies, CI/CD and infrastructure, AI/tool security, tests, observability, and documentation drift. Keep the audit read-only. Do not claim complete coverage unless the coverage ledger proves it. Produce a prioritized final report with exact file/line evidence and explicit proof gaps.
```

## Files

```text
CodeInquest-skill/
├── SKILL.md
└── references/
    ├── agent-roles.md
    ├── review-matrix.md
    ├── coverage-ledger.md
    └── finding-format.md
```

The main workflow is defined in [`SKILL.md`](./SKILL.md). Detailed review criteria and output contracts live in [`references/`](./references/).

## Relationship to CodeCanon

CodeInquest and [CodeCanon](https://github.com/Quavon-dev/CodeCanon-skill) solve different problems:

- **CodeInquest** audits existing repositories and finds evidence-backed weaknesses and improvement opportunities.
- **CodeCanon** governs how coding agents should implement production changes: secure, minimal, performant, and maintainable.

When CodeInquest enters Fix Mode, it should load CodeCanon when available.

## Audit philosophy

CodeInquest is intentionally skeptical. A dangerous-looking pattern is a candidate, not automatically a vulnerability. Material findings should be validated or backed by a complete static trace with explicit reachability, controls, counterevidence, and proof gaps.

Likewise, shorter code is not automatically better and unusual code is not automatically slow. Recommendations must preserve or improve correctness, security, performance, readability, compatibility, and maintainability.

## Contributing

Focused improvements are welcome. Please read [`CONTRIBUTING.md`](./CONTRIBUTING.md) before opening a pull request.

Security issues concerning CodeInquest itself should be reported according to [`SECURITY.md`](./SECURITY.md), not through a public issue.

## License

CodeInquest is available under the [MIT License](./LICENSE).

## Maintainer

**rgxdev**  
hello@d-aaron.dev
