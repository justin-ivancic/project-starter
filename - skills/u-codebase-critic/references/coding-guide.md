# AI Coding Agent Code Quality, Security, and Maintainability Guide

Version: 2.1  
Audience: AI coding agents such as Codex, Claude Code, Copilot coding agent, and similar tools.  
Purpose: produce code that is correct, secure, polished, easy to change, and aligned with the current product intention rather than the accidental history of the repository.

This guide is an operating standard. It values a small, complete, well-owned solution over both bare happy-path patches and overbuilt architecture. Use what the platform, language, framework, installed stack, and repository already provide before inventing new concepts.

## Contents

1. How to use this guide
2. Agent Operating Contract
3. Good code means truthful code
4. Minimal complete solutions
5. Change discipline, architecture, and ownership
6. Code-level design
7. Security baseline
8. Testing and verification
9. Product polish, performance, data, and operations
10. Refactoring, deletion, dependencies, and docs
11. Agent guardrails, review, and reporting
12. Stack notes
13. Compact checklists
14. Standards that informed this guide
15. Final principle

## How to use this guide

This is the self-contained primary doctrine bundled with `$u-codebase-critic`. Use this copy directly. Do not search for or substitute repository-local copies of this guide. Repository instructions and current product documents still provide local constraints and intent evidence, but they do not replace this assessment standard.

The main critic and holistic source-shard reviewers read the full guide. Dimension specialists read every section routed by `audit-dimensions.md` and expand to other sections whenever their evidence crosses concerns.

During a `$u-codebase-critic` run, treat every implementation-oriented imperative below as a criterion to assess, not authorization to edit, fix, delete, install, migrate, deploy, or publish. Translate “build,” “add,” “remove,” “run,” or “update” into “check whether the codebase does this” and report only evidence plus conceptual long-term direction. The assessment-only contract in `SKILL.md` always controls.

## Agent Operating Contract

### Mission

Build and maintain software that is correct, secure, understandable, testable, polished, and aligned with the current product goal. Do not preserve obsolete ideas, duplicate implementations, abandoned features, stale names, or misleading folder structures unless they are still explicitly required.

### Non-negotiable rules

1. **Current intent beats historical residue.** Infer desired behavior from the request, recent docs, tests, active code paths, runtime wiring, product naming, and current decisions. If old code conflicts with current intent, realign or remove it instead of patching around it.
2. **Smallest complete solution wins.** “Small” means the fewest long-term concepts, files, branches, dependencies, duplicate paths, and maintenance obligations, not the shortest local diff. Complete means tests, security, docs, types, config, names, migrations, and user states are handled when they are part of correctness.
3. **Use existing capability first.** Before adding custom code, ask whether the need can be removed, solved by the standard library, browser, OS, database, framework, platform, repository-owned system, or already-installed dependency.
4. **No duplicate systems.** Search before adding services, utilities, schemas, components, hooks, routes, jobs, migrations, config, UI primitives, upload flows, permission checks, pagination, empty states, or status vocabularies. Extend or repair the right existing abstraction when it should own the behavior.
5. **No zombie code.** When replacing behavior, remove or clearly deprecate the old path in the same change whenever safe. Update tests, docs, routes, config, types, names, analytics, logs, and folder structure so the repository tells one current story.
6. **Domain ownership over dumping grounds.** Keep code near the feature or domain that owns it. Avoid `utils`, `helpers`, `common`, and `shared` unless the code is truly stable and shared by multiple active domains.
7. **Security is correctness.** Validate untrusted input at boundaries. Enforce authorization server-side and object-by-object. Use safe query and shell APIs. Protect secrets. Redact sensitive logs. Deny by default.
8. **Tests prove behavior.** Add or update the smallest meaningful tests for risk, bugs, security boundaries, shared primitives, and user-visible behavior. Bug fixes need regression coverage that would have failed before the fix.
9. **Run verification.** Use commands from the repository's docs, package files, CI, Makefiles, or task runners. Do not invent commands. If checks cannot run, state why and what remains unverified.
10. **Preserve product polish.** User-facing work must handle loading, empty, error, success, permission, edge, accessibility, keyboard, responsive, and recovery states as appropriate.
11. **Explain only what matters.** Final reports should state what changed, what existing system or platform primitive was reused, what was removed or avoided, what was verified, and any remaining risk or deliberate simplification ceiling.

### Default workflow

1. Inspect relevant files, tests, docs, routes, config, and current patterns before editing.
2. Define done: expected behavior, affected users, edge cases, security implications, and verification commands.
3. Plan briefly for multi-file, security-sensitive, data-model, migration, architectural, deletion, or risky refactor work. Skip ceremony for tiny obvious edits.
4. Implement using local patterns, clear names, focused functions, existing systems, and no speculative abstractions.
5. Realign stale names, docs, tests, types, routes, config, and old paths made inaccurate by the change.
6. Verify targeted checks first, broader checks when risk justifies them.
7. Self-review the diff as a maintainer for correctness, security, complexity, duplication, dead code, stale docs, broken tests, product polish, and net code health.

### Completion questions

Before finishing, answer internally: Did this solve the current intent? Did I search existing patterns? Did I avoid duplicate systems? Did I remove or update obsolete artifacts? Are validation, authorization, secrets, logging, and dependency risks safe? Are tests meaningful and deterministic? Did I run the right checks? Did I avoid mistaking green checks for full completion? Would a future maintainer understand this without digging through accidental history?

## 1. Good code means truthful code

Good code does more than run. It makes the intended product easier to understand, safer to operate, and cheaper to change. It is correct, secure, cohesive, maintainable, observable, reversible where possible, and minimal without being unfinished.

Avoid two opposite failures. Barely functional code passes the happy path while ignoring tests, security, errors, accessibility, operations, and edge states. Bloated “future-proof” code adds layers, flags, files, dependencies, and generic systems for requirements that do not exist. Build the well-fitted tool: boring, owned, secure, and easy to change.

Repositories contain fossils: old names, abandoned flows, duplicate services, feature flags that never retire, and tests for behavior nobody wants. Agents are prone to preserving fossils because old code looks authoritative. Treat code as evidence of current behavior, not proof of product truth. When signals conflict, prefer explicit recent instructions, current docs, active tests for user-visible behavior, runtime wiring, and settled decisions. If deleting or changing behavior could remove an important feature, ask one concise question or choose the smallest reversible step and record the assumption.

When touching an area with old or conflicting artifacts, classify each related piece as **keep**, **change**, **delete**, or **quarantine**. Quarantine only when deletion is genuinely risky. Mark the reason, isolate it from the active path, and add an owner or removal condition. Do not use quarantine as a default hiding place for timidity.

When purpose changes, update names and contracts at all layers: files, folders, classes, functions, components, routes, endpoints, jobs, tables, columns, enums, UI copy, docs, comments, tests, fixtures, mock data, config, env vars, feature flags, analytics, metrics, logs, alerts, API contracts, and migration notes. A stale name silently teaches the next agent the wrong story.

## 2. Minimal complete solutions

Minimalism here means fewer total obligations, not fewer lines today. A patch is not small if it bypasses validation, duplicates a shared component, invents a second vocabulary, leaves old paths alive, or creates tomorrow's audit finding.

Use this decision ladder before adding custom code:

1. Does this need to exist at all?
2. Can the language standard library solve it?
3. Can the browser, OS, database, framework, cloud platform, or runtime solve it?
4. Does the repository already have a shared system, component, service, selector, contract, schema, permission layer, UI primitive, copy pattern, or workflow?
5. Does an already-installed dependency solve it cleanly?
6. Can a few clear local lines express it without creating a new concept?
7. Only then add new custom code, and make it the minimum complete version.

This ladder should be reflexive, not a research project. It must include the repository's own shared systems. Do not reinvent shared platform behavior because the same need appears on another page, route, app, template, component, or workflow. If the existing system is close but incomplete, improve it. If it is wrong, refactor or realign it. If it is genuinely domain-specific, keep the new code domain-owned and make the separation clear.

Minimal code avoids speculative abstractions, interfaces with one implementation, factories with one product, config nobody sets, feature flags for behavior that should simply be public and functional, wrappers that only delegate, helper files that merely move code elsewhere, new dependencies for platform-covered behavior, boilerplate for later, compatibility layers without active compatibility needs, duplicate systems, and dead code preserved out of fear.

Minimal code does not remove required tests, authorization, input validation, privacy or visibility gates, data-loss-preventing error handling, security logging, secret redaction, accessibility basics, keyboard support, loading and error states, rate limits on sensitive paths, transaction safety, migration safety, retention guarantees, explicit user requirements, or real-world knobs for hardware, timing, external services, and operational variance. If less code loses one of these, it is not simpler.

Prefer standard and platform-native features when they fit: browser form controls and APIs, CSS layout and media features, database constraints and transactions, Python `pathlib` and `dataclasses`, Node `fs`, `path`, `crypto`, streams, arrays, maps, and built-in JSON, and similar mature capabilities. This is not dogma. A dependency earns its place when native support is insufficient, accessibility or security would be worse, runtime support is missing, edge cases are hard, or the library is already the project standard.

Use already-installed stable dependencies before adding another package or hand-rolling a competitor. Do not add a second date library, query parser, validation layer, modal system, uploader, markdown parser, permission layer, editor primitive, or design component pattern without a strong reason. Existing dependencies are part of the platform. New dependencies are new obligations.

When making an intentional bounded simplification, leave a useful marker only if future maintainers need it:

```text
doctrine: bounded simplification; ceiling: [known safe limit]; upgrade when [trigger].
```

A simplification marker without a ceiling and trigger is likely rot. Audit such markers by listing file, line, ceiling, and trigger.

Useful review tags for simplification work: `delete` for dead code or stale flexibility, `stdlib` for custom code the language already handles, `native` for package or custom code the platform already handles, `existing-system` for reinvention of repository primitives, `yagni` for future-proofing without a current need, `shrink` for fewer concepts or branches, `consolidate` for duplicate implementations that need one owner, and `retire` for old paths that should leave after replacement.

## 3. Change discipline, architecture, and ownership

Make the smallest complete change that solves the real problem. A change is incomplete if it leaves broken tests, dead code, misleading names, duplicate paths, unhandled security implications, half-implemented user states, or docs that describe old behavior. A change is too large if it mixes unrelated features, broad formatting, dependency upgrades, architecture experiments, or multiple bug fixes. Split when possible.

Refactor only with a reason: the current shape blocks the requested change, misleads relative to current intent, causes security or correctness risk, prevents meaningful tests, creates demonstrated duplication risk, or needs a clear public/data contract boundary. Do not refactor because a different style is prettier, a new library is interesting, or an abstraction might help someday.

Architecture should be just large enough to protect expected change. Keep clear boundaries between UI and business rules, business rules and persistence, internal models and external payloads, trusted and untrusted data, synchronous user paths and background work, and product logic and generic infrastructure. Dependencies should flow toward stable concepts. Avoid domain logic importing UI, deep cross-feature imports, circular dependencies, shared modules importing feature-specific code, and low-level utilities depending on product state.

Follow the repository's structure unless it is actively causing harm. A common shape is `features/<feature>`, `shared/ui`, `shared/lib`, `infrastructure`, and framework-specific `app` or `routes`, but frameworks differ. If structure changes, update imports, tests, docs, and agent instructions.

`shared`, `common`, `utils`, and `helpers` are danger caves. Add to them only when code is used by multiple active domains now, has a stable domain-neutral purpose, and has a specific name. Avoid `helpers.ts`, `misc.ts`, `manager.ts`, and similar fog. Prefer names like `invoiceTotals.ts`, `authSessionCookies.ts`, `emailAddress.ts`, or `retryPolicy.ts`. Use the fewest files compatible with clear ownership and reuse. Do not split code into tiny files to look architected, and do not jam unrelated behavior together to keep file count low.

For public APIs, exported modules, SDKs, shared libraries, and database contracts, keep surfaces narrow. Document inputs, outputs, errors, compatibility expectations, and breaking changes. Avoid leaking implementation details. Add tests that protect contract behavior.

## 4. Code-level design

Names are compression. Good names reveal domain meaning, data unit, side effect, lifecycle, and whether data is nullable, optional, derived, cached, persisted, or user-provided. Avoid vague names, stale product-era names, and storage-shaped names when a domain concept exists. Booleans should read clearly: `isArchived`, `canEdit`, `hasValidSession`, not inverted double negatives.

Functions should do one coherent thing at one level of abstraction. Prefer explicit inputs and outputs, limited hidden state, separated calculation and side effects, typed results or documented exceptions, and testability without full application boot. Avoid unexpected mutation, long primitive parameter lists, flag parameters for unrelated behavior, swallowed errors, and functions that mix parsing, validation, authorization, persistence, rendering, and transport.

Use types to make invalid states hard to represent. Validate untrusted input at process, network, storage, file, queue, CLI, environment, and user boundaries. Convert validated data into internal types. Keep external DTOs separate from internal domain models when they evolve differently. Prefer discriminated unions or explicit enums for state. Avoid `any`, unchecked casts, raw maps, and stringly typed state unless the project has no better mechanism.

Errors are part of the product contract. Preserve enough detail for debugging without leaking secrets, private data, stack traces, or internal topology to users. Distinguish validation, permission, user, dependency, and internal failures. Fail closed for security. Avoid catch-all success, silent fallback that hides data loss or privilege errors, blind retries of non-idempotent operations, and vague API errors that force clients to guess.

Code should explain what. Comments should usually explain why. Good comments capture non-obvious business rules, security decisions, compatibility constraints, and why a simpler-looking option is wrong. Temporary comments need owner, date, reason, and removal condition. Delete stale comments when code changes.

Make side effects visible. Name side-effecting functions with verbs. Keep reads and writes separate where possible. Avoid hidden network, storage, clock, random, or environment access inside pure-looking functions. Inject time, randomness, and external clients when tests need determinism. Use transactions around multi-step writes that must stay consistent.

## 5. Security baseline

Security is not a later pass. For features touching user data, permissions, payments, authentication, files, integrations, infrastructure, or background jobs, think through assets, actors, entry points, trust boundaries, abuse cases, and failure mode. Map high-risk web work to OWASP-style risks and verification requirements.

Validate all untrusted input at boundaries: request bodies, query params, headers, cookies, path params, webhooks and signatures, uploads and metadata, queue messages, CLI args, environment variables, third-party API data, and database records when integrity is not guaranteed. Check shape, type, length, range, format, allowed values, and cross-field rules. Reject unknown or dangerous fields when appropriate. Frontend validation is user experience, not server security.

Use sink-specific protection for injection risks. Use parameterized SQL or safe query builders. Escape HTML by context. Avoid raw data in executable JavaScript. Avoid shell invocation; if unavoidable, pass arguments safely and never concatenate untrusted input. Use safe APIs for LDAP, XML, templates, regexes, and paths. Sanitization is not a magic rinse.

Use proven authentication libraries or platform services. Do not implement password hashing, token signing, OAuth, or session handling from scratch unless the project is a security library. Use secure session cookies where cookies are used: `HttpOnly`, `Secure`, appropriate `SameSite`, path/domain scope, and rotation on privilege changes. Avoid exposing whether an account exists unless the product accepts that risk.

Enforce authorization server-side, not only in UI. Deny by default. Check every object, not just every route. Do not trust client-provided IDs, roles, tenant IDs, prices, scopes, or ownership flags. Test horizontal and vertical privilege boundaries. Recheck authorization in background jobs when payloads can be forged, delayed, or stale.

Never hardcode secrets, credentials, API keys, tokens, private keys, passwords, database URLs, signing keys, encryption keys, or recovery codes. Use secret managers, environment injection, or platform-secure config. Validate required environment variables at startup. Keep secrets out of logs, errors, metrics, analytics, screenshots, test output, generated docs, and `.env.example` values. Rotate exposed secrets immediately; Git history remembers.

Do not invent cryptography. Use mature libraries, secure randomness, authenticated encryption where applicable, separated keys and data, and documented key rotation assumptions. Do not use outdated hashes or ciphers for security decisions.

Minimize sensitive data collection and retention. Treat logs as data stores. Redact structured logs. Avoid sending sensitive data to analytics or third parties without explicit product and legal intent. Protect backups, exports, support tools, and admin interfaces.

For uploads, enforce size limits, validate content beyond client filename or MIME type when risk justifies it, generate server-side storage names, block path traversal, store files outside executable or public paths unless meant to be public, strip risky metadata where needed, and consider malware scanning for high-risk contexts.

For SSRF, webhooks, and outbound requests, allowlist user-influenced destinations where possible, block internal ranges and metadata services unless explicitly required and protected, set timeouts and response limits, verify webhook signatures, and add replay protection.

Add abuse controls to expensive, sensitive, or anonymous endpoints: login, reset, signup, invites, OTP, token refresh, search, exports, report generation, AI calls, email sending, payments, uploads, and webhooks. Rate limiting is not authorization.

Log security events safely: login outcomes, credential changes, MFA changes, permission changes, admin actions, token lifecycle, sensitive exports or deletions, suspicious validation failures, and rate-limit triggers. Include correlation IDs, actor or tenant IDs when safe, action, outcome, and reason. Avoid raw payloads.

Add dependencies only when they solve a real problem better than local or platform code. Prefer maintained packages with clear ownership, acceptable license, active releases, and modest transitive load. Use lockfiles. Remove unused dependencies. Enable dependency, secret, static analysis, type, lint, test, IaC, container, and provenance checks where appropriate. A noisy gate becomes a scarecrow, so tune it.

## 6. Testing and verification

Tests are executable memory. Keep them accurate, focused, and alive. Use many fast focused tests, fewer integration tests, and a small number of high-value end-to-end tests. Do not rely on slow brittle UI journeys for everything.

Test behavior that matters: core user flows, boundaries, permission matrices, validation, error and empty states, data migrations, concurrency and idempotency, public API compatibility, and security-sensitive branches. Avoid excessive tests for framework internals, mock choreography, private helpers already covered through public behavior, and snapshots that churn without catching regressions.

Good tests fail when behavior breaks, are deterministic, have scenario-shaped names, arrange data through readable factories or fixtures, assert outcomes instead of internal choreography, avoid sleeps and shared mutable state, clean up after themselves, and keep their own logic simple. Non-trivial logic should leave the smallest runnable check that would fail if it broke. Do not add elaborate scaffolding for trivial one-liners or per-helper suites when a public path covers the behavior better.

Bug fix protocol: reproduce with a failing test or clear manual verification, identify root cause, fix the smallest responsible area, add regression coverage, verify related edge cases, and remove diagnostic code.

Run the most relevant actual commands. Read repository docs, CI config, `package.json`, Makefiles, task runners, or build files. Typical examples include `npm test`, `npm run typecheck`, `npm run lint`, `npm run build`, `pytest`, `ruff check .`, `pyright`, `mypy .`, `go test ./...`, `cargo test`, `cargo clippy`, `mvn test`, or `gradle test`, but the project's commands win.

For UI work, visible browser verification is part of done when available. If unavailable, say the UI remains visually unverified. Passing checks are evidence, not completion; they do not prove architecture, stale-code cleanup, security boundaries, or user behavior are finished.

## 7. Product polish, performance, data, and operations

Correctness includes user experience. User-facing work should handle initial and slow loading, empty and partial data, success, validation errors, permission denied, dependency failure, retry or recovery, offline or reconnect states when relevant, and destructive action safeguards.

For web or app UI, use semantic structure, working keyboard navigation, visible focus, labels, accessible names, sufficient contrast, safe focus behavior, announcements for important dynamic changes, non-color-only meaning, usable touch targets, reduced motion where needed, and responsive layout. Target WCAG 2.2 AA unless the project says otherwise. Match existing spacing, typography, copy tone, component patterns, navigation, scroll, and focus expectations. Avoid flicker, layout shift, and new design languages unless requested.

For APIs, use consistent status codes and error shapes, actionable validation errors, pagination for unbounded lists, request size limits, idempotency keys for risky repeats, documented breaking changes, and minimal purposeful response data.

Do not prematurely optimize, but do not ship obvious waste on active paths. Avoid unbounded queries, loops, payloads, recursion, and in-memory accumulation. Watch for N+1 queries. Use pagination, filtering, indexes, timeouts, background jobs for long operations, and bounded retries. Cache only with a freshness and invalidation strategy. For web apps, consider loading performance, interaction responsiveness, visual stability, unnecessary client JavaScript, image optimization, main-thread work, and duplicate fetching.

Data changes require special caution. Name tables, columns, events, and enums after current domain concepts. Use constraints for invariants, indexes for real query patterns, transactions for multi-step consistency, and locking where concurrent writes can conflict. Avoid fields with multiple meanings, premature denormalization, and unnecessary sensitive data.

Production migrations should usually be backward-compatible: expand schema, deploy code that writes both if needed, backfill, read new, stop writing old, then remove old after verification and retention review. Make backfills resumable and observable. Avoid long locks. Provide rollback or forward-fix strategy. Test against realistic data shape when possible.

Configuration belongs in environment-specific mechanisms, not hardcoded constants. Validate required config at startup and fail fast on missing critical values. Keep secrets separate, document placeholders, remove obsolete keys, and keep development, test, staging, and production similar enough that behavior does not mutate mysteriously.

Feature flags need purpose, owner, creation date, expected removal condition or date, default state by environment, and test coverage for active states. Remove flags after rollout. Permanent flags are product configuration and should be named accordingly.

Software must be diagnosable where users suffer. Use structured logs with operation, correlation/request ID, safe actor or tenant identifiers, outcome, error category, and relevant non-sensitive dimensions. Track request count, latency, error rate, queue depth, external dependency failures, user journey completion where useful, and security event counts. For distributed systems, traces should connect services, jobs, and external calls without sensitive attributes. Critical features need runbooks for detection, mitigation, rollback or disablement, inspection points, and edge cases.

## 8. Refactoring, deletion, dependencies, and docs

Before refactoring, identify behavior that must not change, add characterization tests if under-tested, define the desired boundary or name, keep behavior changes separate when practical, and plan deletion of old paths. Move before changing behavior when possible. Rename with tool support. Keep public contracts stable unless intentionally changing them. Afterward, delete old files and exports, remove obsolete tests and fixtures, update docs and imports, and verify no duplicate implementations remain.

For risky replacement, use a strangler pattern: define target behavior and boundary, add a thin adapter only if needed, route a safe slice, verify behavior and telemetry, move remaining slices, delete the old implementation, then delete the adapter if it no longer has purpose. Do not leave both systems alive indefinitely.

Deletion is a positive outcome. Search references through text, types, route maps, config, tests, docs, generated clients, CI, and runtime wiring. Identify public contracts, migrations, telemetry, and external clients. Remove active code, tests, docs, config, flags, analytics, fixtures, mocks, and dependencies tied only to removed behavior. Keep compatibility shims only when required, with expiration. Run checks and search again. Do not delete solely because text search is empty in systems with reflection, dynamic imports, generated code, external routes, or plugins.

Delete tests when they assert obsolete behavior. Add or update tests for current behavior instead of preserving old expectations because they look impressive.

Dependencies are rented code. Before adding one, ask whether the problem is core enough, whether the package is maintained and licensed acceptably, how many transitive dependencies it adds, whether it increases bundle size or attack surface, whether the project already has an equivalent, whether local code is safer, and whether it constrains future architecture. Prefer official SDKs for complex external services. Do not ignore vulnerability alerts without documented risk acceptance.

Respect framework idioms. Do not bypass framework security features, fight routing or rendering patterns, mix incompatible paradigms without a migration plan, or bury product rules in framework entry points when testable domain code is possible.

Documentation should describe current truth. Update docs when setup commands, test commands, environment variables, public APIs, data models, security assumptions, user behavior, operational procedures, architecture boundaries, feature flags, or migration steps change. Use short ADRs for decisions future maintainers will wonder about: context, decision, alternatives, consequences, date, and status. Delete or update docs when features go away. Stale documentation is a bug with nice typography.

## 9. Agent guardrails, review, and reporting

AI agents fail predictably: patch tunnel vision, duplicate creation, zombie preservation, plausible invention, over-abstraction, under-verification, security amnesia, context flooding, unowned shared code, and silent failure. During assessment, counter these by inspecting source first, searching for patterns by name, route, type, UI copy, and behavior, using exact project commands, tracing replaced behavior, checking relevant history or diffs when useful, preferring explicit assumptions over hidden guesses, and keeping conclusions proportional to direct evidence.

Ask one concise question only when ambiguity could cause materially wrong behavior, security issues, data loss, or irreversible product direction. Do not ask when the repository clearly shows the pattern, the decision is low-risk and reversible, the user already answered, or a safe default can be implemented and stated.

Never use an assessment to delete production data, change authorization, apply migrations, accept dependency/security risk, or fix broader breakage. Record the evidence, risk, and conceptual long-term direction only.

Review active code, runtime paths, tests, docs, and relevant history for design fit, behavior, user impact, security boundaries, complexity, naming, dead code, folder structure, performance on hot paths, accessibility, product polish, and net code health. For cleanup and refactor history, inspect what was added, removed, renamed, realigned, consolidated, or left alive. Treat unexplained net growth as a signal to investigate, not automatic guilt.

A good assessment report includes canonical findings with exact source evidence, observed behavior, why it matters, conceptual long-term direction, contributing dimensions, confidence, independent validation for consequential claims, tests and checks run, UI/browser verification when relevant, refuted hotspots, known uncertainty, and exact file coverage. It never claims behavior changed during an assessment.

## 10. Stack notes

These are examples, not mandates. Use the repository's configured tools first.

TypeScript and JavaScript: prefer strict TypeScript, runtime schemas for external data, focused React components, domain logic outside rendering, no unnecessary derived client state, no unsafe `dangerouslySetInnerHTML`, and configured ESLint, Prettier, type checks, unit tests, and Playwright or equivalent for critical UI flows.

Python: use explicit types for public functions and complex structures, project-approved validation models, `pytest` patterns already present, `ruff`, `pyright`, or `mypy` when configured, safe ORM or parameterized database access, and business logic outside framework views when possible.

Go: use `gofmt`, `go test`, cohesive packages, small interfaces introduced at the consumer boundary when useful, explicit errors with helpful context, and little global mutable state.

Rust: use the type system for invariants, avoid production `unwrap` or `expect` unless justified, keep error types useful, prefer safe Rust, and run configured `cargo test`, `cargo fmt`, and `cargo clippy`.

Java and JVM: keep controllers thin, put business rules in clear services or domain classes, validate at boundaries, avoid deep inheritance, use dependency injection consistently, and run configured tests, formatters, and static analysis.

## 11. Compact checklists

Intent and map: understand current intent, find relevant code paths, identify active tests and docs, search for similar systems, map trust boundaries, and identify configured verification commands.

Implementation evidence: check whether code follows existing patterns, uses current domain names, avoids duplicate systems, treats old behavior intentionally, validates inputs, enforces authorization, protects secrets, handles errors honestly, covers meaningful behavior, and keeps docs/config truthful.

Verification evidence: run only safe relevant checks, review security-sensitive paths, inspect current code and useful diffs, identify dead code and stale docs/tests/config, verify user-facing states when possible, and state remaining risk.

Security: trusted auth, object-level authorization, boundary validation, safe injection sinks, secrets out of code/logs/docs/tests, sensitive data minimized and redacted, necessary dependencies only, non-leaky errors, abuse controls where needed, and safe security logging.

Deletion recommendation: before recommending deletion, verify runtime references, tests, docs, config, flags, env vars, analytics, metrics, dependencies, generated artifacts, dynamic use, data implications, and the checks that would prove a safe removal.

## Standards that informed this guide

This bundled doctrine was informed by NIST SSDF, OWASP Secure Coding Practices, OWASP ASVS, OWASP Top 10, CISA Secure by Design, MITRE CWE Top 25, SLSA, OpenSSF Scorecard, GitHub code/secret/dependency scanning guidance, Google engineering review and testing guidance, W3C WCAG, Web Vitals, Twelve-Factor App, Semantic Versioning, Conventional Commits, and official coding-agent instruction guidance. The bundled guide is sufficient for a normal audit. Consult an external current standard only when the user explicitly requests it or a claim requires authoritative current verification, and record that external evidence separately.

## Final principle

Every change should make the repository more truthful. Truthful code has names that match purpose, tests that match desired behavior, docs that match reality, folders that reveal ownership, and security assumptions enforced by code instead of hope.
