---
name: u-coding-doctrine
description: >-
  Guide repository code work across implementation, bug fixing, refactoring,
  cleanup, architecture, security-sensitive changes, review, tests,
  verification, deletion, simplification, duplicate systems, zombie code,
  domain boundaries, and maintainability. Load the bundled guide for
  architecture, security, dependencies, migrations, data models, folder
  structure, deletion, review, or large feature work.
---

# Coding Doctrine

## Purpose

Use this skill to leave the repository more truthful, secure, understandable, testable, polished, smaller in total maintenance burden, and aligned with current product intent. Prefer the smallest complete solution that belongs in the existing system: fewer concepts, files, branches, dependencies, duplicate paths, wrappers, and long-term obligations, without dropping correctness, security, accessibility, tests, operational safety, or user polish.

This file carries the working contract. The bundled guide carries the detailed rationale and standards for structural, risky, or durable decisions.

## Required Reference

- Bundled full guide: `references/coding-guide.md`

The bundled guide is the authoritative source copy for this skill. Do not look for or prefer a repository-specific, project-specific, or external source copy.

Read `references/coding-guide.md` completely before architecture, security, refactoring, dependency, data-model, migration, folder-structure, deletion, cleanup, review, or large feature work. For small edits, apply the contract below and open the guide if the change touches risk, ambiguity, public behavior, persisted data, or durable structure.

Resolve the reference path relative to this `SKILL.md`, not relative to the repository being edited. After reading the guide fully, these searches can help revisit relevant sections; run them from the skill directory or substitute the resolved absolute path:

```bash
rg -n "^#|^##|^###" references/coding-guide.md
rg -n "authority|scope|minimal|existing-system|security|authorization|validation|migration|deletion|duplicate|zombie|verification|self-review" references/coding-guide.md
```

## Authority, Scope, and Repository State

The user's request and higher-level instructions define the authorized outcome, action mode, and scope. This doctrine governs how authorized work is performed; it does not broaden permission. Review, assessment, diagnosis, explanation, and status requests remain read-only unless changes are requested. Local implementation requests do not silently authorize deployment, production-data writes or deletion, external messages, history-rewriting or destructive version-control commands, out-of-scope filesystem removal, or unrelated cleanup. Ordinary task-owned edits and evidence-backed deletion inside the change envelope remain governed by the rules below.

Establish a change envelope before editing: the requested behavior, the files and systems that own it, and the adjacent changes genuinely required for correctness. Tests, types, docs, config, migrations, generated artifacts, and obsolete paths may belong in that envelope when the requested change makes them necessary. Do not mix in unrelated improvements merely because they are worthwhile; report them separately.

Use repository evidence to determine how to implement the requested outcome, not to invent broader product direction. Apply this evidence hierarchy:

1. Governing instructions and the current user request.
2. Explicit accepted specifications, ADRs, current product decisions, and public or data contracts.
3. Active runtime wiring and behavior tests.
4. Recent documentation and current product naming.
5. Historical implementation and residue.

Lower-ranked evidence must not silently override higher-ranked direction. When evidence conflicts around security, persisted data, compatibility, public behavior, or irreversible product direction, ask the minimum blocking question or take the smallest reversible step and state the assumption. Absence of a text reference is not by itself proof that an externally consumed or dynamically wired artifact is unused.

Treat the existing working tree as user-owned. Inspect relevant status and diffs before editing. Preserve unrelated and pre-existing changes; do not overwrite, revert, format, stage, or commit them as part of the task.

## Operating Contract

1. Infer current product intent using the authority and evidence hierarchy above. Current intent beats historical residue, but inference does not broaden the authorized change envelope.
2. Make the smallest complete change that solves the real problem within that envelope, including tests, docs, types, config, names, migrations, generated artifacts, and structure when correctness requires them.
3. Use existing capability before inventing code: remove the need if possible, then prefer the standard library, browser, OS, database, framework, platform, repository systems, healthy and appropriate already-installed dependencies, clear local code, and only then new custom code.
4. Search before adding services, utilities, schemas, components, hooks, routes, jobs, migrations, config, UI primitives, permission checks, pagination, upload flows, empty states, or status vocabularies.
5. Improve, extend, consolidate, or realign the correct existing abstraction before creating a parallel system. Share only when semantics, ownership, lifecycle, security boundary, and reason to change align. If separate code is genuinely needed, keep it domain-owned and explain the boundary.
6. Remove or clearly deprecate paths directly made obsolete by the requested change when safe. Do not leave zombie code, stale tests, stale docs, misleading names, unused flags, duplicate systems, or dead compatibility layers inside the affected system.
7. Keep code near the domain that owns it. Avoid `utils`, `helpers`, `common`, and `shared` unless the code is genuinely shared by multiple active domains and has a stable, specific purpose.
8. Avoid speculative or semantically empty scaffolding: no one-product factories, config nobody sets, wrappers that only delegate without enforcing a meaningful boundary, helper files that merely move code, or flags for behavior that should simply work. A single implementation may still justify an interface or adapter when it protects an external boundary, authorization, telemetry, transactions, time or I/O test seams, platform compatibility, or a stable public contract.
9. Treat security as correctness: validate affected boundaries, enforce server-side and object-level authorization, use safe query and shell APIs, protect secrets, redact logs, minimize sensitive data, assess abuse controls on exposed sensitive or expensive paths, and deny authorization by default.
10. Preserve user polish where relevant to the changed surface: loading, empty, error, success, permission, accessibility, keyboard, responsive, recovery, and edge states.
11. Add or update the smallest meaningful tests for behavior that matters, at the cheapest stable layer that exercises the real risk. Tests support production-code quality; they are not a substitute for real simplification, and they must not be weakened merely to make checks pass.
12. Derive verification from repository docs, package files, CI, Makefiles, task runners, and configured tools. When documentation is silent but configuration unambiguously supports a safe check, use it and report it. Do not fabricate scripts or alter configuration merely to create a verification command. If checks cannot run, state why and what remains unverified.
13. Do not obtain a green result by weakening meaningful tests, assertions, types, lint rules, security checks, ignore boundaries, or timeouts unless the changed expectation is supported by intended behavior.
14. Finish with a proportional report: outcome, verification performed, and meaningful remaining risk. Include reuse, removals, net footprint, visible verification, and simplification ceilings when relevant to larger feature, cleanup, refactor, migration, deletion, security, or UI work; do not force ceremony onto tiny edits.

## Workflow

1. Inspect repository status and relevant existing diffs. Identify pre-existing or unrelated user changes that must remain untouched.
2. Inspect relevant files, tests, docs, routes, config, runtime wiring, generated-file provenance, and local patterns before editing.
3. Define done and the change envelope: expected behavior, users affected, edge cases, security implications, compatibility or data implications, adjacent artifacts required for correctness, and verification commands.
4. Plan briefly for multi-file, security-sensitive, data-model, migration, deletion, refactor, architecture, dependency, public-contract, or generated-code work. Skip ceremony for tiny obvious edits.
5. Implement with local patterns, boring clear code, focused functions, existing systems, and the fewest files compatible with ownership and reuse. Avoid broad formatting and unrelated cleanup.
6. Realign artifacts made stale by the change by renaming, moving, deleting, consolidating, regenerating, or updating them. Do not hand-edit generated output when the repository provides a generator. Do not change lockfiles incidentally; intentional dependency changes must keep manifests and lockfiles consistent.
7. Verify targeted checks first, then broader checks when risk justifies them. Run checks capable of falsifying the changed behavior. For UI work, use visible browser verification when available; otherwise leave that risk open.
8. Self-review the task-owned diff for correctness, security, complexity, duplication, dead code, stale docs, broken tests, product polish, accidental generated or lockfile churn, unrelated edits, and net code health.

## Decision Rules

- Prefer deletion over addition for behavior that is obsolete, duplicated, unreachable, or misleading and is inside the authorized change envelope.
- Prefer consolidation over local one-offs when multiple active surfaces need the same behavior and their semantics, ownership, lifecycle, security boundary, and reason to change align. Similar-looking code is not automatically the same system.
- Prefer repository-owned systems over copied page-specific logic, without dumping domain-specific code into shared folders.
- Prefer platform, framework, database, browser, standard-library, and healthy already-installed dependency primitives when they fit.
- Prefer boring direct code over clever generic systems, magic registration, deep indirection, and abstractions without a meaningful boundary.
- Prefer characterization tests before risky refactors and regression evidence before bug fixes when practical and proportional.
- Delete only artifacts directly made obsolete by the requested change or explicitly included in cleanup scope. Check text and type references, runtime wiring, dynamic or reflective registration, generated consumers, public contracts, persisted data, external clients, deployment version skew, and rollback requirements as relevant. An empty text search is not sufficient in systems with dynamic behavior or external consumers.
- Keep compatibility adapters only when an active compatibility, rollout, or version-skew requirement exists. Give temporary adapters a documented removal condition; do not leave two permanent systems alive by default.
- Treat passing checks as evidence, not completion. Green tests do not prove cleanup, security boundaries, architecture, UI behavior, or product intent.
- Treat failing checks as findings, not automatic scope. Fixing the nearest red check is useful only when the requested intent remains covered or the unrelated failure is explicitly left open.
- Do not weaken assertions, delete meaningful coverage, loosen types or lint rules, add broad ignores, increase timeouts, or suppress errors merely to make verification pass.
- For cleanup and refactor work, track added, removed, renamed or realigned, duplicate paths collapsed, and zombie code deleted. Use `git diff --stat` or `git diff --shortstat` when available.
- Treat net code growth in cleanup work as a prompt to investigate, not a quality score or automatic failure. Explain what safety, deletion, simplification, clearer boundary, or verification the growth unlocks.
- Do not let tests, CI, reports, wrappers, compatibility layers, or process scaffolding substitute for production-code simplification.
- Update test expectations only after confirming the new behavior is intended from higher-ranked evidence: the request, accepted decisions or contracts, active runtime paths, current docs, or user confirmation.
- Preserve unrelated user changes. Never use destructive version-control resets, broad or out-of-scope filesystem removal, broad formatting, incidental dependency upgrades, or generated-file rewrites to make the task easier. This does not prohibit evidence-backed deletion that belongs to the requested change.
- When specialist security, frontend, database, framework, or platform instructions apply, use them for their domain-specific workflow. This doctrine continues to govern scope, system fit, duplication, cleanup, and completion quality.
- Ask the minimum blocking questions when ambiguity could cause materially wrong implementation, security risk, data loss, compatibility breakage, or irreversible product direction. Batch closely related blocking questions when useful.
- Stop and report risk before deleting production data, changing unclear authorization behavior, applying irreversible migrations, breaking an unclear public or data contract, or accepting dependency or security risk without explicit approval.

## Minimalism Guardrails

Minimalism must never remove boundary validation, server-side authorization, object-level permissions, privacy or visibility gates, data-loss-preventing error handling, needed security logging, secret redaction, accessibility basics, keyboard support, loading, empty, error, success, or permission states where relevant, rate limits on sensitive paths, transaction safety, migration safety, file cleanup and retention, explicit user requirements, necessary compatibility, or real-world calibration knobs for hardware, timing, external services, and operational variance.

Minimalism also does not forbid a small abstraction with one implementation when it enforces a real boundary or invariant. Remove semantically empty abstraction, not useful seams merely because they currently have one consumer.

For intentional simplifications that may need later review, use an existing repository convention when available and include both the known safe ceiling and the upgrade trigger. If no convention exists and a local marker will genuinely help future maintainers, use:

```text
doctrine: bounded simplification; ceiling: [known safe limit]; upgrade when [trigger].
```

Do not add doctrine-specific comments merely to demonstrate compliance. Use these as internal review lenses rather than mandatory source tags: `delete`, `stdlib`, `native`, `existing-system`, `yagni`, `shrink`, `consolidate`, `retire`.

## Completion Review

Before finalizing, answer internally:

- Did this remain within the authorized action mode and change envelope?
- Did this solve current intent rather than merely produce a superficial literal patch?
- Did you apply the evidence hierarchy instead of treating historical code as authority?
- Did you inspect and preserve unrelated or pre-existing user changes?
- Did you search existing patterns, platform primitives, healthy installed dependencies, and shared systems before adding code?
- Did you avoid duplicate systems, local one-offs, speculative scaffolding, and unnecessary dependencies?
- Did you share code only where semantics, ownership, lifecycle, security boundary, and reason to change align?
- Did you remove or update artifacts directly made obsolete by the change without deleting on text-search evidence alone?
- Are necessary compatibility paths justified by an active requirement and a removal condition where temporary?
- Are validation, authorization, secrets, logs, sensitive data, dependency risk, and abuse controls safe?
- Are tests meaningful, deterministic, proportional, and free of changes made only to get green?
- Did you run the right checks or clearly explain why not?
- Were generated files and lockfiles changed only intentionally through repository-supported workflows?
- For cleanup or refactor work, what is the net result: added, removed, renamed or realigned, consolidated, and deleted?
- If the diff grew, what cleanup, safety, clearer boundary, or verification does that growth unlock?
- If UI or browser verification was required but unavailable, did you leave that risk open?
- Would a future maintainer understand this without spelunking through accidental history?

## Versioning

Update this version whenever the skill or its bundled resources change:

- Major (`2.0.0`): incompatible workflow or contract changes.
- Minor (`1.1.0`): backward-compatible capabilities or material instruction changes.
- Patch (`1.0.1`): fixes, clarifications, or small refinements.

Version: 1.0.0
