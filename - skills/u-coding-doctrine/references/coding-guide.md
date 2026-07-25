# AI Coding Agent Code Quality, Security, and Maintainability Guide

Version: 2.1  
Audience: AI coding agents such as Codex, Claude Code, Copilot coding agent, and similar tools.  
Purpose: produce code that is correct, secure, polished, easy to change, and aligned with the current product intention rather than the accidental history of the repository.

This guide is an operating standard. It values a small, complete, well-owned solution over both bare happy-path patches and overbuilt architecture. Use what the platform, language, framework, installed stack, and repository already provide before inventing new concepts.

## How to use this guide

This is the bundled long-form reference for the u-coding-doctrine skill. Apply the skill's working contract whenever it is active and use this guide for the rationale, examples, and deeper requirements behind structural, risky, or durable decisions. Treat this bundled file as the skill's authoritative guide; do not search for or prefer external project copies.

Agents should apply the operating contract for all code work and consult the full guide before architecture, security, refactor, dependency, migration, data-model, folder-structure, deletion, cleanup, or large feature decisions.

Using this guide does not itself authorize editing repository instruction files, broadening the task, changing production state, or performing external actions. Repository owners may separately mirror selected principles into always-loaded instructions when they explicitly choose to do so.

## Contents

- [Agent Operating Contract](#agent-operating-contract)
- [1. Good code means truthful code](#1-good-code-means-truthful-code)
- [2. Minimal complete solutions](#2-minimal-complete-solutions)
- [3. Change discipline, architecture, and ownership](#3-change-discipline-architecture-and-ownership)
- [4. Code-level design](#4-code-level-design)
- [5. Security baseline](#5-security-baseline)
- [6. Testing and verification](#6-testing-and-verification)
- [7. Product polish, performance, data, and operations](#7-product-polish-performance-data-and-operations)
- [8. Refactoring, deletion, dependencies, and docs](#8-refactoring-deletion-dependencies-and-docs)
- [9. Agent guardrails, review, and reporting](#9-agent-guardrails-review-and-reporting)
- [10. Stack notes](#10-stack-notes)
- [11. Compact checklists](#11-compact-checklists)
- [Standards to consult](#standards-to-consult)
- [Final principle](#final-principle)

## Agent Operating Contract

### Mission

Build and maintain software that is correct, secure, understandable, testable, polished, and aligned with the current product goal inside the authorized task scope. Do not preserve obsolete ideas, duplicate implementations, abandoned features, stale names, or misleading folder structures when the requested change directly makes them obsolete and safe removal is supported by evidence.

### Authority, scope, and repository state

The user's request and higher-level instructions define the authorized outcome, action mode, and scope. This guide governs how authorized work is performed; it does not broaden permission. Review, assessment, diagnosis, explanation, and status requests remain read-only unless changes are requested. Implementation may include directly affected tests, docs, types, config, migrations, generated artifacts, and cleanup needed for correctness, but it does not authorize unrelated redesign, repository-wide cleanup, deployment, production-data writes or deletion, external messages, history-rewriting or destructive version-control commands, or out-of-scope filesystem removal. Ordinary task-owned edits and evidence-backed deletion inside the change envelope remain governed by the rules below.

Establish a change envelope before editing: the requested behavior, the files and systems that own it, and the adjacent changes genuinely required for correctness. Report useful out-of-scope improvements separately instead of silently absorbing them into the task.

Use repository evidence to resolve implementation details, not to invent broader product direction. When signals conflict, use this hierarchy:

1. Governing instructions and the current user request.
2. Explicit accepted specifications, ADRs, current product decisions, and public or data contracts.
3. Active runtime wiring and behavior tests.
4. Recent repository documentation and current product naming.
5. Historical implementation and residue.

Lower-ranked evidence must not silently override higher-ranked direction. Tests can preserve a defect, documentation can be stale, and absence of an internal reference does not prove absence of an external consumer. If a conflict affects security, persisted data, compatibility, public behavior, or irreversible product direction, ask the minimum blocking question or choose the smallest reversible step and state the assumption.

Treat the working tree as user-owned. Inspect relevant status and existing diffs before editing. Preserve unrelated and pre-existing changes, avoid broad formatting when a focused edit is sufficient, use generators for generated artifacts when available, and do not change lockfiles unless dependency resolution is intentionally in scope. Never revert, overwrite, stage, commit, or include unrelated work merely because it is present.

### Non-negotiable rules

1. **Current intent beats historical residue, within authorized scope.** Infer desired behavior from the request and the evidence hierarchy above. If old code conflicts with current intent, realign or remove it when that work belongs to the requested change; do not use nearby residue as permission for unrelated cleanup.
2. **Smallest complete solution wins.** “Small” means the fewest long-term concepts, files, branches, dependencies, duplicate paths, and maintenance obligations inside the change envelope, not the shortest local diff. Complete means tests, security, docs, types, config, names, migrations, generated artifacts, and user states are handled when they are part of correctness.
3. **Use existing capability first.** Before adding custom code, ask whether the need can be removed, solved by the standard library, browser, OS, database, framework, platform, repository-owned system, or an appropriate, healthy already-installed dependency.
4. **No duplicate systems.** Search before adding services, utilities, schemas, components, hooks, routes, jobs, migrations, config, UI primitives, upload flows, permission checks, pagination, empty states, or status vocabularies. Extend or repair the right existing abstraction when it should own the behavior. Share code only when semantics, ownership, lifecycle, security boundary, and reason to change align.
5. **No zombie code.** When replacing behavior, remove or clearly deprecate the old path in the same change when evidence supports deletion and compatibility permits it. Update directly affected tests, docs, routes, config, types, names, analytics, logs, generated artifacts, and folder structure so the repository tells one current story.
6. **Domain ownership over dumping grounds.** Keep code near the feature or domain that owns it. Avoid `utils`, `helpers`, `common`, and `shared` unless the code is truly stable and shared by multiple active domains.
7. **Security is correctness.** Validate untrusted input at affected boundaries. Enforce authorization server-side and object-by-object. Use safe query and shell APIs. Protect secrets. Redact sensitive logs. Assess abuse controls when changing exposed sensitive or expensive paths. Deny authorization by default.
8. **Tests prove behavior.** Add or update the smallest meaningful tests for risk, bugs, security boundaries, shared primitives, and user-visible behavior at the cheapest stable layer that exercises the real risk. Bug fixes should leave regression evidence that would have failed before the fix when practical and proportional.
9. **Run verification.** Derive commands from repository docs, package files, CI, Makefiles, task runners, and checked-in tool configuration. When verification is undocumented, use a conservative tool-native command directly supported by that configuration and state what was run. Do not guess nonexistent scripts or silently weaken checks. If checks cannot run, state why and what remains unverified.
10. **Preserve product polish.** User-facing work must handle the loading, empty, error, success, permission, edge, accessibility, keyboard, responsive, and recovery states relevant to the changed surface.
11. **Report proportionally.** Every final report should state the outcome, verification performed, and meaningful remaining risk. For larger feature, cleanup, refactor, migration, deletion, security, or UI work, also report important reuse, removals, net footprint, visible verification, and follow-ups. Do not pad tiny changes with ritual categories.

### Default workflow

1. Inspect repository status and relevant existing diffs before editing. Treat pre-existing changes as user-owned, preserve unrelated work, and identify the files and hunks that belong to the task.
2. Inspect relevant files, tests, docs, routes, config, runtime wiring, generated-file provenance, and current patterns before editing.
3. Define done and the change envelope: expected behavior, affected users, edge cases, security implications, compatibility or data implications, adjacent artifacts required for correctness, and verification commands.
4. Plan briefly for multi-file, security-sensitive, data-model, migration, architectural, deletion, dependency, public-contract, generated-code, or risky refactor work. Skip ceremony for tiny obvious edits.
5. Implement authorized changes using local patterns, clear names, focused functions, existing systems, and no speculative abstractions. Avoid broad formatting and unrelated cleanup.
6. Realign names, docs, tests, types, routes, config, generated artifacts, and old paths made inaccurate by the change. Do not hand-edit generated output when the repository provides a generator.
7. Verify targeted checks capable of falsifying the changed behavior first, then broader checks when risk justifies them.
8. Self-review the task-owned diff as a maintainer for correctness, security, complexity, duplication, dead code, stale docs, broken tests, product polish, accidental generated or lockfile churn, unrelated edits, and net code health.

### Completion questions

Before finishing, answer internally: Did I stay inside the authorized action mode and change envelope? Did I preserve unrelated and pre-existing work? Did this solve the current intent? Did I apply the evidence hierarchy? Did I search existing patterns? Did I avoid duplicate systems? Is each deletion supported by affirmative evidence? Did I remove or update artifacts directly made obsolete by the change? Are validation, authorization, secrets, logging, and dependency risks safe? Are tests meaningful and deterministic? Did I run the right checks without weakening them merely to get green? Would a future maintainer understand this without digging through accidental history?

## 1. Good code means truthful code

Good code does more than run. It makes the intended product easier to understand, safer to operate, and cheaper to change. It is correct, secure, cohesive, maintainable, observable, reversible where possible, and minimal without being unfinished.

Avoid two opposite failures. Barely functional code passes the happy path while ignoring tests, security, errors, accessibility, operations, and edge states. Bloated “future-proof” code adds layers, flags, files, dependencies, and generic systems for requirements that do not exist. Build the well-fitted tool: boring, owned, secure, and easy to change.

Repositories contain fossils: old names, abandoned flows, duplicate services, feature flags that never retire, and tests for behavior nobody wants. Agents are prone to preserving fossils because old code looks authoritative. Treat code as evidence of current behavior, not proof of product truth.

When signals conflict, apply the operating contract's evidence hierarchy. Tests can faithfully preserve a defect, documentation can be stale, names can describe an abandoned product era, and an empty internal reference search does not prove that no external consumer exists. If a conflict affects security, persisted data, compatibility, public behavior, or irreversible product direction, ask the minimum blocking question or choose the smallest reversible step and record the assumption. Use current intent to resolve work inside the authorized change envelope, not to claim authority over adjacent product direction.

When touching an area with old or conflicting artifacts inside the change envelope, classify each related piece as **keep**, **change**, **delete**, or **quarantine**. Quarantine only when deletion is genuinely risky and a temporary compatibility or investigation boundary is necessary. Mark the reason, isolate it from the active path, and add an owner or measurable removal condition. Do not use quarantine as a hiding place for uncertainty or as a permanent inactive system.

When purpose changes, update names and contracts at all layers: files, folders, classes, functions, components, routes, endpoints, jobs, tables, columns, enums, UI copy, docs, comments, tests, fixtures, mock data, config, env vars, feature flags, analytics, metrics, logs, alerts, API contracts, and migration notes. A stale name silently teaches the next agent the wrong story.

## 2. Minimal complete solutions

Minimalism here means fewer total obligations, not fewer lines today. A patch is not small if it bypasses validation, duplicates a shared component, invents a second vocabulary, leaves old paths alive, or creates tomorrow's audit finding.

Use this decision ladder before adding custom code:

1. Does this need to exist at all?
2. Can the language standard library solve it?
3. Can the browser, OS, database, framework, cloud platform, or runtime solve it?
4. Does the repository already have a shared system, component, service, selector, contract, schema, permission layer, UI primitive, copy pattern, or workflow?
5. Does an appropriate, healthy already-installed dependency solve it cleanly?
6. Can a few clear local lines express it without creating a new concept?
7. Only then add new custom code, and make it the minimum complete version.

This ladder should be reflexive, not a research project. It must include the repository's own shared systems. Do not reinvent shared platform behavior because the same need appears on another page, route, app, template, component, or workflow. If the existing system is close but incomplete, improve it. If it is wrong, refactor or realign it. If it is genuinely domain-specific, keep the new code domain-owned and make the separation clear.

Share code when it represents the same knowledge and its semantics, ownership, lifecycle, security boundary, and reason to change align. Similar-looking code is not automatically duplication. Two small domain-owned implementations can be safer than one shared abstraction when their policies or evolution can diverge.

Minimal code avoids semantically empty abstractions: interfaces introduced only to mirror one concrete type, factories that only select one product, config nobody sets, feature flags without a real rollout or operational purpose, wrappers that delegate without owning policy or a boundary, helper files that merely move code elsewhere, new dependencies for platform-covered behavior, boilerplate for later, compatibility layers without active compatibility needs, duplicate systems, and dead code preserved out of fear.

A one-implementation interface or thin wrapper can still be correct at an external SDK or I/O seam, authorization, transaction, telemetry, clock or randomness boundary, consumer-owned test seam, stable public contract, or temporary migration adapter. The question is whether the abstraction owns a real boundary or current axis of change, not merely how many implementations it has today.

Minimal code does not remove required tests, authorization, input validation, privacy or visibility gates, data-loss-preventing error handling, security logging, secret redaction, accessibility basics, keyboard support, loading and error states, rate limits on sensitive paths, transaction safety, migration safety, retention guarantees, explicit user requirements, or real-world knobs for hardware, timing, external services, and operational variance. If less code loses one of these, it is not simpler.

Prefer standard and platform-native features when they fit: browser form controls and APIs, CSS layout and media features, database constraints and transactions, Python `pathlib` and `dataclasses`, Node `fs`, `path`, `crypto`, streams, arrays, maps, and built-in JSON, and similar mature capabilities. This is not dogma. A dependency earns its place when native support is insufficient, accessibility or security would be worse, runtime support is missing, edge cases are hard, or the library is already the project standard.

Use appropriate, maintained, compatible, healthy already-installed dependencies before adding another package or hand-rolling a competitor. Installed does not automatically mean suitable: do not deepen reliance on a deprecated, vulnerable, unmaintained, license-incompatible, redundant, or poorly fitting package merely because it is present. Do not add a second date library, query parser, validation layer, modal system, uploader, markdown parser, permission layer, editor primitive, or design component pattern without a strong reason. Existing dependencies are part of the platform only while they remain healthy and appropriate. New dependencies are new obligations.

When making an intentional bounded simplification, use the repository's existing ADR, issue, TODO, or comment convention when available. Leave a local marker only if future maintainers genuinely need it, and include both the known safe ceiling and the upgrade trigger:

```text
doctrine: bounded simplification; ceiling: [known safe limit]; upgrade when [trigger].
```

A simplification marker without a ceiling and trigger is likely rot. Do not add doctrine-specific comments merely to demonstrate compliance. Audit useful markers by listing file, line, ceiling, and trigger.

Useful internal review lenses for simplification work: `delete` for dead code or stale flexibility, `stdlib` for custom code the language already handles, `native` for package or custom code the platform already handles, `existing-system` for reinvention of repository primitives, `yagni` for future-proofing without a current need, `shrink` for fewer concepts or branches, `consolidate` for duplicate implementations that need one owner, and `retire` for old paths that should leave after replacement. These are not mandatory source tags.

## 3. Change discipline, architecture, and ownership

Make the smallest complete change that solves the real problem inside the authorized change envelope. A change is incomplete if it leaves directly affected tests broken, obsolete code active, misleading names, duplicate paths, unhandled security implications, half-implemented relevant user states, or docs that describe the changed behavior incorrectly. A change is too large if it mixes unrelated features, broad formatting, incidental dependency upgrades, architecture experiments, or unrelated bug fixes. Split when possible and report adjacent debt separately.

Protect the working tree. Do not revert, overwrite, stage, commit, or reformat unrelated user changes. Change generated artifacts through their source or generator when available, and do not alter lockfiles unless dependency resolution is intentionally part of the task. If requested work overlaps a dirty file, edit narrowly, review the combined diff carefully, and report the overlap. History-rewriting or destructive version-control commands and out-of-scope filesystem removal require explicit authority. This does not prohibit ordinary task-owned edits or evidence-backed removal inside the change envelope.

Refactor only with a reason: the current shape blocks the requested change, misleads relative to current intent, causes security or correctness risk, prevents meaningful tests, creates demonstrated duplication risk, or needs a clear public/data contract boundary. Do not refactor because a different style is prettier, a new library is interesting, or an abstraction might help someday.

Architecture should be just large enough to protect expected change. Keep clear boundaries between UI and business rules, business rules and persistence, internal models and external payloads, trusted and untrusted data, synchronous user paths and background work, and product logic and generic infrastructure. Dependencies should flow toward stable concepts. Avoid domain logic importing UI, deep cross-feature imports, circular dependencies, shared modules importing feature-specific code, and low-level utilities depending on product state. A small adapter, interface, or wrapper is justified when it makes one of these boundaries explicit and enforceable; it is not justified merely to create layers.

Follow the repository's structure unless it is actively causing harm. A common shape is `features/<feature>`, `shared/ui`, `shared/lib`, `infrastructure`, and framework-specific `app` or `routes`, but frameworks differ. If structure changes, update imports, tests, docs, and agent instructions.

`shared`, `common`, `utils`, and `helpers` are danger caves. Add to them only when code is used by multiple active domains now, has a stable domain-neutral purpose, and has a specific name. Avoid `helpers.ts`, `misc.ts`, `manager.ts`, and similar fog. Prefer names like `invoiceTotals.ts`, `authSessionCookies.ts`, `emailAddress.ts`, or `retryPolicy.ts`. Use the fewest files compatible with clear ownership and reuse. Do not split code into tiny files to look architected, and do not jam unrelated behavior together to keep file count low.

For public APIs, exported modules, SDKs, shared libraries, event schemas, CLI contracts, and database contracts, keep surfaces narrow. Document inputs, outputs, errors, compatibility expectations, and breaking changes. Avoid leaking implementation details. Add tests that protect contract behavior. Treat external consumers, persisted data, and rolling deployment version skew as real dependencies even when repository search cannot see them.

## 4. Code-level design

Names are compression. Good names reveal domain meaning, data unit, side effect, lifecycle, and whether data is nullable, optional, derived, cached, persisted, or user-provided. Avoid vague names, stale product-era names, and storage-shaped names when a domain concept exists. Booleans should read clearly: `isArchived`, `canEdit`, `hasValidSession`, not inverted double negatives.

Functions should do one coherent thing at one level of abstraction. Prefer explicit inputs and outputs, limited hidden state, separated calculation and side effects, typed results or documented exceptions, and testability without full application boot. Avoid unexpected mutation, long primitive parameter lists, flag parameters for unrelated behavior, swallowed errors, and functions that mix parsing, validation, authorization, persistence, rendering, and transport.

Use types to make invalid states hard to represent. Validate untrusted input at process, network, storage, file, queue, CLI, environment, and user boundaries. Convert validated data into internal types. Keep external DTOs separate from internal domain models when they evolve differently. Prefer discriminated unions or explicit enums for state. Avoid `any`, unchecked casts, raw maps, and stringly typed state unless the project has no better mechanism.

Errors are part of the product contract. Preserve enough detail for debugging without leaking secrets, private data, stack traces, or internal topology to users. Distinguish validation, permission, user, dependency, and internal failures. Fail closed for security. Avoid catch-all success, silent fallback that hides data loss or privilege errors, blind retries of non-idempotent operations, and vague API errors that force clients to guess.

Code should explain what. Comments should usually explain why. Good comments capture non-obvious business rules, security decisions, compatibility constraints, and why a simpler-looking option is wrong. Temporary comments need owner, date, reason, and removal condition. Delete stale comments when code changes.

Make side effects visible. Name side-effecting functions with verbs. Keep reads and writes separate where possible. Avoid hidden network, storage, clock, random, or environment access inside pure-looking functions. Inject time, randomness, and external clients when tests need determinism. Use transactions around multi-step writes that must stay consistent.

## 5. Security baseline

Security is not a later pass. When authorized changes touch user data, permissions, payments, authentication, files, integrations, infrastructure, or background jobs, think through assets, actors, entry points, trust boundaries, abuse cases, and failure modes. Map high-risk web work to OWASP-style risks and verification requirements. Preserve existing security properties outside the changed surface and report broader architectural risks rather than silently expanding the task unless immediate correction is necessary for the requested behavior to be safe.

Validate all untrusted input at boundaries: request bodies, query params, headers, cookies, path params, webhooks and signatures, uploads and metadata, queue messages, CLI args, environment variables, third-party API data, and database records when integrity is not guaranteed. Check shape, type, length, range, format, allowed values, and cross-field rules. Reject unknown or dangerous fields when appropriate. Frontend validation is user experience, not server security.

Use sink-specific protection for injection risks. Use parameterized SQL or safe query builders. Escape HTML by context. Avoid raw data in executable JavaScript. Avoid shell invocation; if unavoidable, pass arguments safely and never concatenate untrusted input. Use safe APIs for LDAP, XML, templates, regexes, and paths. Sanitization is not a magic rinse.

Use proven authentication libraries or platform services. Do not implement password hashing, token signing, OAuth, or session handling from scratch unless the project is a security library. Use secure session cookies where cookies are used: `HttpOnly`, `Secure`, appropriate `SameSite`, path/domain scope, and rotation on privilege changes. Avoid exposing whether an account exists unless the product accepts that risk.

Enforce authorization server-side, not only in UI. Deny by default. Check every object, not just every route. Do not trust client-provided IDs, roles, tenant IDs, prices, scopes, or ownership flags. Test horizontal and vertical privilege boundaries. Recheck authorization in background jobs when payloads can be forged, delayed, or stale.

Never hardcode secrets, credentials, API keys, tokens, private keys, passwords, database URLs, signing keys, encryption keys, or recovery codes. Use secret managers, environment injection, or platform-secure config. Validate required environment variables at startup. Keep secrets out of logs, errors, metrics, analytics, screenshots, test output, generated docs, and `.env.example` values. Rotate exposed secrets immediately; Git history remembers.

Do not invent cryptography. Use mature libraries, secure randomness, authenticated encryption where applicable, separated keys and data, and documented key rotation assumptions. Do not use outdated hashes or ciphers for security decisions.

Minimize sensitive data collection and retention. Treat logs as data stores. Redact structured logs. Avoid sending sensitive data to analytics or third parties without explicit product and legal intent. Protect backups, exports, support tools, and admin interfaces.

For uploads, enforce size limits, validate content beyond client filename or MIME type when risk justifies it, generate server-side storage names, block path traversal, store files outside executable or public paths unless meant to be public, strip risky metadata where needed, and consider malware scanning for high-risk contexts.

For SSRF, webhooks, and outbound requests, allowlist user-influenced destinations where possible, block internal ranges and metadata services unless explicitly required and protected, set timeouts and response limits, verify webhook signatures, and add replay protection.

When creating or materially changing expensive, sensitive, or anonymous endpoints, assess appropriate abuse controls: login, reset, signup, invites, OTP, token refresh, search, exports, report generation, AI calls, email sending, payments, uploads, and webhooks. Use controls that fit the deployment architecture; an in-process limiter is not a distributed limit. Rate limiting is not authorization.

Log security events safely: login outcomes, credential changes, MFA changes, permission changes, admin actions, token lifecycle, sensitive exports or deletions, suspicious validation failures, and rate-limit triggers. Include correlation IDs, actor or tenant IDs when safe, action, outcome, and reason. Avoid raw payloads.

Add dependencies only when they solve a real problem better than local or platform code. Prefer maintained packages with clear ownership, acceptable license, active releases, and modest transitive load. Use lockfiles. Remove unused dependencies. Enable dependency, secret, static analysis, type, lint, test, IaC, container, and provenance checks where appropriate. A noisy gate becomes a scarecrow, so tune it.

## 6. Testing and verification

Tests are executable memory. Keep them accurate, focused, and alive. Test at the cheapest stable layer that exercises the real risk. Use many fast focused tests, fewer integration tests, and a small number of high-value end-to-end tests, but do not mock away the database, framework, authorization, serialization, migration, transaction, or concurrency behavior being verified. Do not rely on slow brittle UI journeys for everything.

Test behavior that matters: core user flows, boundaries, permission matrices, validation, error and empty states, data migrations, concurrency and idempotency, public API compatibility, and security-sensitive branches. Avoid excessive tests for framework internals, mock choreography, private helpers already covered through public behavior, and snapshots that churn without catching regressions.

Good tests fail when behavior breaks, are deterministic, have scenario-shaped names, arrange data through readable factories or fixtures, assert outcomes instead of internal choreography, avoid sleeps and shared mutable state, clean up after themselves, and keep their own logic simple. Non-trivial logic should leave the smallest runnable check that would fail if it broke. Do not add elaborate scaffolding for trivial one-liners or per-helper suites when a public path covers the behavior better.

Bug fix protocol: reproduce with a failing test or clear manual verification, identify root cause, fix the smallest responsible area, add regression evidence that would have failed before the fix when practical and proportional, verify related edge cases, and remove diagnostic code. When automated coverage is genuinely infeasible, preserve a reproducible manual check and state the remaining test gap.

Run the most relevant actual commands. Derive them from repository docs, CI config, `package.json`, Makefiles, task runners, build files, and checked-in tool configuration; do not assume script names. When no project command is documented but configuration unambiguously supports a safe tool-native check, use it and state the basis. Typical examples include `npm test`, `npm run typecheck`, `npm run lint`, `npm run build`, `pytest`, `ruff check .`, `pyright`, `mypy .`, `go test ./...`, `cargo test`, `cargo clippy`, `mvn test`, or `gradle test`, but the project's configured commands win.

Never obtain a green result by weakening or deleting meaningful tests, assertions, types, lint rules, security checks, ignore boundaries, or timeouts unless the changed expectation is supported by intended behavior. Distinguish failures introduced by the task from pre-existing, unrelated, or environment-limited failures. Do not silently expand scope to repair unrelated failures; continue with scoped verification when they do not invalidate attribution, and stop when they make the claimed result misleading.

For UI work, visible browser verification is part of done when available. If unavailable, say the UI remains visually unverified. Passing checks are evidence, not completion; they do not prove architecture, stale-code cleanup, security boundaries, or user behavior are finished.

## 7. Product polish, performance, data, and operations

Correctness includes user experience. User-facing work should preserve or add the initial and slow loading, empty and partial data, success, validation errors, permission denied, dependency failure, retry or recovery, offline or reconnect states, and destructive action safeguards relevant to the changed surface. Do not broaden a tiny visual or copy change into unrelated state-system work; report missing adjacent product states when they are outside scope.

For web or app UI, use semantic structure, working keyboard navigation, visible focus, labels, accessible names, sufficient contrast, safe focus behavior, announcements for important dynamic changes, non-color-only meaning, usable touch targets, reduced motion where needed, and responsive layout. Target WCAG 2.2 AA unless the project says otherwise. Match existing spacing, typography, copy tone, component patterns, navigation, scroll, and focus expectations. Avoid flicker, layout shift, and new design languages unless requested.

For APIs, use consistent status codes and error shapes, actionable validation errors, pagination for unbounded lists, request size limits, idempotency keys for risky repeats, documented breaking changes, and minimal purposeful response data.

Do not prematurely optimize, but do not ship obvious waste on active paths. Avoid unbounded queries, loops, payloads, recursion, and in-memory accumulation. Watch for N+1 queries. Use pagination, filtering, indexes, timeouts, background jobs for long operations, and bounded retries. Cache only with a freshness and invalidation strategy. For web apps, consider loading performance, interaction responsiveness, visual stability, unnecessary client JavaScript, image optimization, main-thread work, and duplicate fetching.

Data changes require special caution. Name tables, columns, events, and enums after current domain concepts. Use constraints for invariants, indexes for real query patterns, transactions for multi-step consistency, and locking where concurrent writes can conflict. Transactions alone do not prevent every lost update, duplicate side effect, or race. Use database constraints, conditional updates, appropriate isolation, row or advisory locks, idempotency keys, deduplication, or optimistic concurrency according to the invariant being protected. Verify truly concurrent behavior at an integration boundary when races are part of the risk; sequential unit tests are not equivalent evidence. Avoid fields with multiple meanings, premature denormalization, and unnecessary sensitive data.

Production migrations should usually remain compatible with rolling deploys and mixed application versions. Prefer expand-and-contract: expand the schema, deploy compatible code, backfill, switch reads, stop old writes, verify, and only then remove old structures after retention and rollback review. Use dual writes only when necessary because they create their own consistency failure modes; keep one authoritative source when possible and define reconciliation when not. Make backfills idempotent, resumable, observable, bounded, and safe under retries. Account for lock duration, online versus blocking DDL, transaction boundaries, replication lag, deploy ordering, version skew, and realistic data volume. Provide a tested rollback or forward-fix strategy; a down migration alone does not make a destructive change safe.

For background jobs and integrations, design explicitly for timeouts, cancellation, resource cleanup, idempotency, duplicate delivery, ordering, partial failure, and retry safety. Avoid claiming exactly-once behavior unless the system actually enforces it across the relevant boundaries.

Configuration belongs in environment-specific mechanisms, not hardcoded constants. Validate required config at startup and fail fast on missing critical values. Keep secrets separate, document placeholders, remove obsolete keys, and keep development, test, staging, and production similar enough that behavior does not mutate mysteriously.

Feature flags need purpose, owner, creation date, expected removal condition or date, default state by environment, and test coverage for active states. Remove flags after rollout. Permanent flags are product configuration and should be named accordingly.

Software must be diagnosable where users suffer. Use structured logs with operation, correlation/request ID, safe actor or tenant identifiers, outcome, error category, and relevant non-sensitive dimensions. Track request count, latency, error rate, queue depth, external dependency failures, user journey completion where useful, and security event counts. For distributed systems, traces should connect services, jobs, and external calls without sensitive attributes. Critical features need runbooks for detection, mitigation, rollback or disablement, inspection points, and edge cases.

## 8. Refactoring, deletion, dependencies, and docs

Before refactoring, identify behavior that must not change, add characterization tests if under-tested, define the desired boundary or name, keep behavior changes separate when practical, and plan deletion of old paths. Move before changing behavior when possible. Rename with tool support. Keep public contracts stable unless intentionally changing them. Afterward, delete old files and exports, remove obsolete tests and fixtures, update docs and imports, and verify no duplicate implementations remain.

For risky replacement, use a strangler pattern: define target behavior and boundary, add a thin adapter only if needed, route a safe slice, verify behavior and telemetry, move remaining slices, delete the old implementation, then delete the adapter if it no longer has purpose. Do not leave both systems alive indefinitely.

Deletion is a positive outcome when evidence supports it and it belongs to the requested change. Search references through text, types, route maps, config, tests, docs, generated clients, CI, runtime wiring, dynamic registration, reflection, plugins, and framework conventions. Check public contracts, persisted data, migrations, telemetry, external consumers, rolling-deploy version skew, and rollback needs. Absence of an in-repository reference is not proof that external consumers do not exist.

Remove active code and the tests, docs, config, flags, analytics, fixtures, mocks, generated artifacts, and dependencies tied only to the removed behavior. Keep compatibility shims only for a concrete consumer, rollout, or rollback requirement, with an owner and measurable removal trigger. Run targeted checks and search again. Do not delete unrelated legacy code merely because it is nearby, and do not delete solely because text search is empty.

Delete tests when they assert obsolete behavior. Add or update tests for current behavior instead of preserving old expectations because they look impressive.

Dependencies are rented code. Before adding or deepening reliance on one, ask whether the problem is core enough, whether the package is healthy, maintained, compatible with the supported runtime, and licensed acceptably, how many transitive dependencies it adds, whether it increases bundle size or attack surface, whether the project already has an equivalent, whether local code is safer, and whether it constrains future architecture. Prefer official SDKs for complex external services and proven security libraries for cryptography, authentication, and protocol handling. Do not ignore vulnerability alerts without documented risk acceptance.

Respect framework idioms. Do not bypass framework security features, fight routing or rendering patterns, mix incompatible paradigms without a migration plan, or bury product rules in framework entry points when testable domain code is possible.

Documentation should describe current truth. Update docs when setup commands, test commands, environment variables, public APIs, data models, security assumptions, user behavior, operational procedures, architecture boundaries, feature flags, or migration steps change. Use short ADRs for decisions future maintainers will wonder about: context, decision, alternatives, consequences, date, and status. Delete or update docs when features go away. Stale documentation is a bug with nice typography.

## 9. Agent guardrails, review, and reporting

AI agents fail predictably: patch tunnel vision, scope creep, duplicate creation, zombie preservation, overconfident deletion, plausible invention, over-abstraction, under-verification, security amnesia, context flooding, dirty-working-tree clobbering, unowned shared code, and silent failure. Counter these by confirming action mode and scope, inspecting repository state first, searching for patterns by name, route, type, UI copy, and behavior, deriving exact project commands, keeping an evidence-backed deletion list for replaced behavior, running targeted verification, reading the task-owned final diff, preferring explicit assumptions over hidden guesses, and choosing the smallest reversible implementation when uncertain.

Ask the minimum blocking questions when ambiguity could cause materially wrong behavior, security issues, data loss, compatibility breakage, public-contract changes, or irreversible product direction. Batch closely related blocking questions when useful. Do not ask when the repository clearly shows the pattern, the decision is low-risk and reversible, the user already answered, or a safe default can be implemented and stated.

Stop and report before deleting production data, changing unclear authorization behavior for sensitive data, applying irreversible migrations, breaking an unclear public or data contract, accepting dependency or security risk without explicit approval, or proceeding when failures prevent reliable attribution and would make the result misleading. Unrelated failures that do not invalidate scoped evidence should be reported, not silently adopted as new work.

Review PRs and final diffs for authorized scope, design fit, behavior, user impact, security boundaries, complexity, tests, naming, docs, dead code, folder structure, performance on hot paths, accessibility, product polish, unrelated changes, and net code health. For cleanup and refactor work, track added, removed, renamed, realigned, duplicate paths collapsed, and zombie code deleted. Treat net code growth as a signal to investigate, not a quality score or automatic failure. Growth can be justified when it unlocks safety, tests, clearer boundaries, or later deletion, but it should not be process scaffolding pretending to be cleanup.

Scale the final report to the work and risk. A tiny change usually needs the outcome, checks run, and any remaining uncertainty. Larger work should also cover obsolete pieces removed or realigned, existing systems or platform primitives reused, migration or compatibility status, UI/browser verification when relevant, net footprint for cleanup or refactor work, known risks, and useful follow-ups. Include screenshots or before/after evidence only when they materially improve verification.

## 10. Stack notes

These are examples, not mandates. Use the repository's configured tools first.

TypeScript and JavaScript: prefer strict TypeScript, runtime schemas for external data, focused React components, domain logic outside rendering, no unnecessary derived client state, no unsafe `dangerouslySetInnerHTML`, and configured ESLint, Prettier, type checks, unit tests, and Playwright or equivalent for critical UI flows.

Python: use explicit types for public functions and complex structures, project-approved validation models, `pytest` patterns already present, `ruff`, `pyright`, or `mypy` when configured, safe ORM or parameterized database access, and business logic outside framework views when possible.

Go: use `gofmt`, `go test`, cohesive packages, small interfaces introduced at the consumer boundary when useful, explicit errors with helpful context, and little global mutable state.

Rust: use the type system for invariants, avoid production `unwrap` or `expect` unless justified, keep error types useful, prefer safe Rust, and run configured `cargo test`, `cargo fmt`, and `cargo clippy`.

Java and JVM: keep controllers thin, put business rules in clear services or domain classes, validate at boundaries, avoid deep inheritance, use dependency injection consistently, and run configured tests, formatters, and static analysis.

## 11. Compact checklists

Pre-change: confirm action mode and authorized scope; inspect repository status and existing diffs; understand current intent; find relevant code paths, generated-file provenance, active tests, and docs; search for similar systems; know trust boundaries and verification commands; and create a short plan for larger work.

Implementation: follow existing patterns, use current domain names, avoid duplicate systems, preserve unrelated work, remove or intentionally preserve old behavior with evidence, use generators for generated artifacts, change dependencies and lockfiles only intentionally, validate inputs, enforce authorization, protect secrets, handle errors honestly, cover meaningful behavior, and update directly affected docs and config.

Completion: run relevant tests and checks without weakening them to get green, distinguish introduced from pre-existing failures, review security-sensitive paths, self-review the task-owned diff, remove directly obsolete code and stale docs/tests/config, verify relevant user-facing states, state remaining risks, and make the repository more truthful.

Security: trusted auth, object-level authorization, boundary validation, safe injection sinks, secrets out of code/logs/docs/tests, sensitive data minimized and redacted, necessary dependencies only, non-leaky errors, abuse controls where needed, and safe security logging.

Deletion: confirm the behavior is inside scope and affirmatively obsolete; check runtime and dynamic wiring, public contracts, external consumers, persisted data, version skew, and rollback needs; remove references, tests, docs, config, flags, env vars, analytics, metrics, dependencies, and stale generated artifacts; handle data cleanup safely; then build, test, and search again.

## Standards to consult

For detailed requirements, consult current versions of NIST SSDF, OWASP Secure Coding Practices, OWASP ASVS, OWASP Top 10, CISA Secure by Design, MITRE CWE Top 25, SLSA, OpenSSF Scorecard, GitHub code/secret/dependency scanning docs, Google engineering review practices, Google testing guidance, W3C WCAG, Web Vitals, Twelve-Factor App, Semantic Versioning, Conventional Commits, and official agent-instruction guidance for Codex, Claude Code, and GitHub Copilot.

## Final principle

Every change should make the repository more truthful. Truthful code has names that match purpose, tests that match desired behavior, docs that match reality, folders that reveal ownership, and security assumptions enforced by code instead of hope.
