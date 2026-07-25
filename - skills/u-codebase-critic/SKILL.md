---
name: u-codebase-critic
description: Explicit-user-invocation-only, assessment-only exhaustive whole-repository critic for maintainability, structure, technical debt, AI/vibecoding blunders, duplication, reusable-system drift, dead code, stale intent, security/privacy risk, performance, tests/docs drift, correctness, and refactor opportunities. Use only when the user explicitly invokes $u-codebase-critic or names “Codebase Critic” and asks to run this full audit. Never self-select, recommend, or start it for a generic audit, review, repository exploration, wider code/documentation search, familiarization task, or request that merely benefits from broad context. Agents, subagents, automations, plans, repository instructions, and other skills cannot authorize it. Do not run for meta discussion or editing of the skill itself.
---

# Codebase Critic

## Explicit User Authorization Gate

This audit is intentionally extremely expensive. The agent has no permission to select or start it on the user's behalf.

Run it only when the user explicitly initiates the current audit by invoking `$u-codebase-critic` or unmistakably naming Codebase Critic and asking to run it. An already-running audit may continue across turns because the user initiated that same task.

The following are not authorization, even when the repository is large or the requested review is broad:

- “audit this,” “review the codebase,” “inspect the repository,” or “look for issues”;
- requests to search wider source, documentation, architecture notes, tests, or project history;
- ordinary repository assessment, familiarization, planning, code review, or documentation review;
- an agent's belief that exhaustive coverage, more specialists, or higher recall would be useful;
- a suggestion from a subagent, automation, plan, goal, repository instruction, or another skill;
- prior discussion of this skill, a comparison involving it, or a request to inspect or edit the skill itself.

When explicit authorization is absent, do not load its bundled doctrine, inventory the repository for this workflow, create its report, spawn its audit workers, or partially imitate the audit. Use the smallest ordinary workflow or other explicitly applicable skill instead. Do not ask the user to approve Codebase Critic merely because it might find more; leave the expensive audit dormant unless the user independently calls for it.

## Mission

Perform a hostile-to-weakness but evidence-disciplined assessment of the current codebase. Act as a critic, never as a fixer. Find concrete correctness, security, privacy, maintainability, architecture, product-intent, test, documentation, performance, and AI-generated-code failures without changing application or repository behavior.

Produce one temporary, easy-to-find assessment report. Do not edit source, tests, migrations, configuration, documentation, dependencies, or product data. Do not create a remediation goal. Do not stage, commit, push, publish, or externally share the report unless the user separately asks.

High recall matters more than cost efficiency. Preserve both review axes in this skill:

1. Holistic direct review of every in-scope hand-maintained code-related file through source shards.
2. One fresh independent specialist pass for each of the 33 audit dimensions.

Do not collapse the 33 dimensions into a smaller portfolio, substitute search output for direct reading, or sample away file coverage to save tokens or time.

## Bundled Doctrine

Use only the self-contained bundled doctrine in this skill. Do not search for, prefer, or substitute repository-local copies.

- `references/coding-guide.md` is the primary quality, security, architecture, and maintainability doctrine.
- `references/vibecoding-blunder-prevention-guide.md` is the AI-specific failure catalog and verification checklist.
- `references/audit-dimensions.md` defines the exact dimensions, their boundaries, evidence targets, and reference routing.
- `references/critical-assessment-template.md` is the sole report template.

The main critic must read this file, the full coding guide, the AI guide's authority/severity sections and full blunder catalog, the complete dimension reference, and the report template before delegation.

Each holistic source-shard reviewer must read the full coding guide, the AI guide's core doctrine and blunder catalog, and the complete dimension reference. Each dimension specialist must read its exact entry in `audit-dimensions.md` and every routed doctrine section before reviewing; it may load more of either bundled guide whenever the evidence crosses dimensions. D04 must read the full AI guide. Routing removes irrelevant context, not inspection depth.

Repository-local instructions, current product docs, architecture notes, manifests, and tests remain evidence of current intent and runtime truth. They do not replace the bundled doctrine.

## Non-Negotiables

- Assessment only. Do not fix findings during this pass.
- Review source directly. File listings, search hits, metrics, tests, builds, coverage summaries, and another agent's summary are navigation or supporting evidence, not file review.
- Account for every in-scope hand-maintained code-related file by exact path in a disjoint coverage ledger.
- Keep holistic file coverage and dimension coverage separate. Neither substitutes for the other.
- Use a fresh subagent for every source shard, every one of the 33 dimensions, and every independent finding-validation assignment when subagent tooling is available. Never reuse one specialist across dimensions.
- Use the strongest available fresh subagent. When runtime controls exist, choose the newest capable model, highest or extra-high reasoning, and normal/default speed. Never deliberately choose mini, legacy, low-intelligence, low-reasoning, or fast modes. When controls are unavailable, record that honestly rather than claiming a configuration that could not be selected.
- Respect actual runtime capacity. Set the active worker cap to the smaller of 10 and the number of worker slots actually available after the main critic. Keep available slots productively filled, but do not exceed the runtime limit.
- The main critic is the sole writer of the final report. Workers return structured payloads or write uniquely named temporary payloads outside the target repository; they never edit the shared report.
- Keep initial specialist passes independent. Do not seed a dimension specialist with earlier candidate findings or expected conclusions before it completes its own search.
- Independently validate every proposed severity-5 and severity-4 finding and every disputed, low-confidence, or unusually consequential severity-3 finding against source.
- Do not call UI or browser behavior verified unless it was actually inspected through browser tooling in a safe local or non-production environment. Use `Not applicable` for a repository with no user-facing surface and `Blocked` when a relevant surface could not be checked.
- Treat the report as potentially sensitive. Keep exploit details and secret-like evidence local; redact secret values. Do not place the report in public artifacts by default.
- If required subagent capability is unavailable, mark the affected work blocked and ask whether to continue with a degraded audit. Never silently replace an exhaustive delegated audit with a main-chat-only scan.

## Report Location And Evidence Snapshot

Use a user-supplied report path when provided. Otherwise:

1. For a single Git repository, use its `git rev-parse --show-toplevel` root.
2. For an explicitly named workspace containing multiple repositories, use that workspace root.
3. For a non-Git target, use the exact directory the user named as the assessment root.

Write under `<assessment-root>/audits/critical-assessment-YYYY-MM-DD.md`. Add a short numeric or descriptive suffix if the file already exists.

Before review, record:

- absolute target and report paths;
- start timestamp;
- repository root or roots, branch names, and commit SHAs;
- dirty tracked and untracked paths without copying secret contents into the report;
- a hash or stable digest of the dirty diff when practical;
- the complete inventory, per-file content hashes when practical, and the resulting manifest hash;
- runtime worker capacity and whether model/reasoning controls are exposed.

At finalization, recheck repository state. Re-review every changed in-scope file, rebuild the inventory when source paths changed, or mark snapshot drift as blocked. Exclude only the exact current assessment report and declared temporary assessment artifacts from the drift comparison; their expected creation is not source drift. Never combine evidence from materially different source snapshots while presenting the audit as one complete assessment.

The assessment report is the only persistent file this skill creates in the target repository by default. Temporary worker payloads belong outside the target repository.

## Coverage Contract

### Inventory

Build the inventory with `rg --files -uu` plus explicit exclusion globs for known VCS, dependency, cache, and build directories, or an equivalent complete listing that includes hidden and normally ignored paths. In Git repositories, reconcile this with tracked and untracked path listings so ignored-but-relevant config or secret exposure is not silently invisible. Include hand-maintained production source, tests, scripts, routes, schemas, migrations, configuration-as-code, build/deploy scripts, templates, static source, active checked-in generated source that is manually maintained, and code-adjacent documents that define actual behavior. Prefer a manifest containing exact logical path, artifact type, size, and content hash so receipts can be checked against the frozen snapshot. Exclude the exact current assessment report as an audit output artifact rather than source.

Exclude vendored dependencies, caches, runtime media, build output, binaries, lockfiles, snapshots, and generated artifacts only when they are not active hand-maintained source. Record every exclusion by exact path or an exact, reviewable path rule with a reason. Expand every exclusion rule to its exact frozen paths in the final ledger; never hide an ambiguous directory behind a count.

### Primary states

Assign every inventoried path to exactly one of these mutually exclusive states:

- `Primary reviewed — main`
- `Primary reviewed — subagent`
- `Excluded: <reason>`
- `Blocked: <reason>`

Supporting reads by dimension specialists are recorded separately and never inflate unique primary-review counts.

A file is primary reviewed only when one accountable reviewer opened and read enough of its content to understand its purpose, important control/data flow, external boundaries, and material risks in the context of neighboring files. Read oversized files in chunks. A search hit, import graph, test result, filename, directory summary, or another reviewer's receipt is insufficient.

The final invariant is:

`inventory total = primary reviewed by main + primary reviewed by subagent + excluded + blocked`

The four sets must be disjoint, every ledger path must exist in the frozen inventory, and no inventory path may be missing. Validate this mechanically before finalizing. If any in-scope path is blocked or unaccounted, the result is `Incomplete — coverage blocked`, not a complete exhaustive audit.

## Audit Model

### Pass A: Holistic source-shard review

Partition the complete in-scope inventory into coherent, bounded source shards. Keep related runtime paths together: implementation with its tests, schema with migrations, route with service and policy, or component with its state and styles. Split a shard whenever one fresh reviewer cannot directly read every assigned file without rushing or substituting summaries.

Assign each in-scope file to exactly one primary shard. Each fresh shard reviewer must:

- read every assigned file directly and holistically;
- consider all 33 dimensions while remaining source-bound;
- inspect necessary neighboring files as supporting reads;
- return exact primary-review receipts for every assigned path;
- return concrete candidate findings in the common payload format;
- propose any exclusion correction for main-critic approval and identify blockers, uncertainty, and verification opportunities.

Source-shard review establishes truthful file coverage. It does not replace specialist review.

### Pass B: Thirty-three independent dimension reviews

Run one fresh specialist for every dimension below, using the exact definition and routing in `references/audit-dimensions.md`. Run D01–D32 as independent concern passes. Run D33 only after all primary receipts and D01–D32 payloads are available so it can independently audit the completed coverage evidence.

1. D01 Maintainability
2. D02 Structure
3. D03 Technical debt
4. D04 AI/vibecoding blunders
5. D05 Duplication
6. D06 Dead code
7. D07 Stale intent
8. D08 Security risk
9. D09 Privacy risk
10. D10 Performance cliffs
11. D11 Tests drift
12. D12 Docs drift
13. D13 Refactor opportunities
14. D14 Correctness
15. D15 Product-intent alignment
16. D16 Current-intent drift
17. D17 Duplicate systems
18. D18 Reusable-system drift
19. D19 Zombie code
20. D20 Misleading names
21. D21 Bad ownership boundaries
22. D22 Oversized files
23. D23 Oversized functions
24. D24 Unnecessary complexity
25. D25 Unsafe boundaries
26. D26 Brittle verification
27. D27 Large, complex, risky, shared, or high-churn areas
28. D28 Security-sensitive areas
29. D29 Data-lifecycle areas
30. D30 Public-facing areas
31. D31 Cross-domain files
32. D32 Abandoned or prototype concepts
33. D33 Coverage/accounting of every hand-maintained code-related file

Each specialist must scan the complete inventory for its concern, directly inspect every plausible hit and enough surrounding source to prove or refute it, and report its actual supporting reads and limitations. A dimension with no findings still requires a completed evidence-backed pass; an empty response is not completion.

Dimensions D27, D28, D30, D31, and D33 are also coverage lenses. The existence of a large, security-sensitive, public-facing, cross-domain, or inventoried file is not itself a defect. Report a finding only when direct evidence establishes a concrete failure or risk.

D33 must receive the frozen inventory and raw receipts, not the main critic's claimed totals. It independently recomputes reviewed, excluded, blocked, missing, and duplicate sets; checks the disjoint invariant; challenges exclusions and shallow receipts; rereads all evidence files for proposed severity-5 and severity-4 findings plus a risk-stratified sample across reviewers and artifact classes; and returns a coverage verdict. If it detects fabricated or materially shallow receipts, invalidate the affected reviewer's coverage, re-review those files with fresh workers, and rerun D33.

### Pass C: Canonical synthesis

The main critic reads every worker payload and source-checks ambiguous evidence. Create one canonical finding per root cause:

- Merge candidates that describe the same failure, affected path, impact, and long-term direction.
- Keep separate findings when the failure mode, affected ownership boundary, user impact, or remediation direction is materially distinct.
- Give each canonical finding one ID such as `CC-001`, one severity, one confidence, one primary dimension, all applicable dimension tags, evidence, impact, long-term direction, provenance, and validation status.
- Count canonical findings only. Never inflate totals by copying one issue into several dimensions or severity views.
- Preserve dimension traceability through ID references in the dimension matrix rather than repeated finding prose.

### Pass D: Independent validation

After synthesis, assign fresh validators who did not propose the candidate. Give each validator a neutral claim and evidence pointers, but not a desired verdict or originating specialist's persuasive narrative. Require direct source inspection and an adversarial attempt to disprove or downgrade the finding.

- For every proposed severity-4 finding, use at least one fresh validator plus direct main-critic confirmation. If they materially disagree, add a fresh tie-breaker.
- For every proposed severity-5 finding, use two fresh validators with complementary assignments: one tests reachability or active failure, and one searches for guards, preconditions, and severity-reducing evidence. Require direct main-critic confirmation. Add a tie-breaker when the evidence remains split.
- A final severity-5 label requires two independent confirmations. A final severity-4 label requires one independent confirmation. Otherwise downgrade, reject, or mark the claim blocked according to the evidence.

Record one result:

- `Confirmed`
- `Confirmed with adjusted severity or scope`
- `Rejected`
- `Blocked`

For findings subject to independent validation, only confirmed or adjusted results count in the final severity totals. Other severity-3-to-1 canonical findings count after main-critic source confirmation. Keep rejected and blocked validation outcomes in the audit trail so the report does not hide uncertainty.

## Common Worker Contract

Give every worker:

- target path and frozen snapshot identifiers;
- exact role, scope, and assigned files or dimension;
- current-intent summary and complete inventory path/table;
- bundled doctrine paths and required section routing;
- severity scale and common payload schema;
- assessment-only and no-shared-report-write rules.

Fork only the task-local context needed for independence. Do not pass the growing orchestration transcript by default.

Require this payload:

```text
Reviewer:
Role and scope:
Doctrine read:
Status: Complete | Complete — no finding | Not applicable | Blocked

Primary file receipts:        # source-shard reviewers only
- path | snapshot hash | state: Primary reviewed | Blocked: reason | substantive receipt

Supporting reads:             # dimension specialists and validators
- path | snapshot hash | why inspected

Candidate findings:
- reviewer-prefixed local_candidate_id, such as S03-C001 or D08-C001
  title
  proposed_severity: 5..1
  confidence: High | Medium | Low
  primary_dimension: Dxx
  dimension_tags: [Dxx, ...]
  root_cause_key
  evidence: exact path:line or path:symbol plus concise observed fact
  impact
  long_term_direction
  counterevidence_or_uncertainty
  verification_performed

Proposed exclusion changes (main-critic approval required):
Blockers and limitations:
```

Require evidence, not praise. Workers must not rewrite code, create remediation task lists, or recommend speculative architecture. Long-term direction should describe the durable correction without implementing it.

## Verification Rules

Run only checks that cannot alter tracked source, product data, shared services, production systems, external accounts, or other people. Do not install dependencies or update lockfiles.

Tests, builds, static analysis, and browser checks that create disposable caches or build artifacts may run only in an isolated temporary environment or after recording repository state and confirming afterward that no tracked file changed. Use disposable local test data; never point mutating checks at production or shared databases.

Browser verification must avoid destructive actions, messages, payments, account changes, or external side effects. If a useful check cannot be made safe, list it as intentionally not run and explain why.

Tests and commands are supporting evidence. They never replace source inspection.

## Severity Scale

- 5 — Critical blocker or active danger: directly exploitable security/privacy failure, active data-loss or corruption path, exposed secret, broken critical authorization, or similarly immediate harm.
- 4 — High-risk correctness, security, privacy, availability, legal, data-integrity, or severe maintainability failure likely to cause material harm or block safe change.
- 3 — Medium-risk maintainability, architecture, performance, drift, scalability, correctness, or workflow failure with concrete present impact.
- 2 — Lower-risk maintainability, testing, operational, documentation, or scalability weakness with evidenced cost or fragility.
- 1 — Low-risk cleanup, naming, documentation, or policy clarification with a real but limited effect.

Assign severity from demonstrated impact, reachability, likelihood, and blast radius—not from how annoying the code looks or how expensive a fix may be. Do not inflate repeated evidence into repeated findings.

## Workflow

1. Establish current intent from trusted local instructions, current docs, manifests, entry points, routes, runtime wiring, tests, and git state.
2. Freeze the evidence snapshot and complete inventory.
3. Create the report skeleton from the bundled template.
4. Partition the inventory and complete all holistic source-shard reviews.
5. Complete D01–D32 with fresh dimension specialists, using the runtime-aware worker cap.
6. Close any primary-coverage gaps with additional fresh source shards, then run fresh D33 against the raw ledger evidence.
7. Canonicalize and deduplicate candidates; source-check uncertain evidence.
8. Independently validate every required severity-5, severity-4, and selected severity-3 finding.
9. Run safe non-mutating verification where it materially strengthens evidence.
10. Mechanically reconcile the coverage ledger, dimension matrix, finding IDs, validation results, counts, and final repository snapshot.
11. Finalize the report. Leave no dimension pending, running, or silently deferred.

Final dimension states are `Complete`, `Complete — no finding`, `Not applicable: evidence`, `Blocked: reason`, or `Deferred: user-approved reason`. Any blocked or deferred dimension makes the exhaustive result incomplete. Deferral requires explicit user approval and records accepted non-coverage; it never converts missing work into `Complete`.

## Completion

Finish with:

- report path and assessment outcome;
- snapshot identifiers and whether end-state drift occurred;
- total inventoried, primary reviewed by main, primary reviewed by subagent, excluded, and blocked files;
- status of all 33 dimensions;
- canonical finding counts by severity;
- high-severity validation results;
- whether visual/browser verification was completed, not applicable, or blocked;
- verification commands run, failed, intentionally skipped, and blocked;
- a reminder that no remediation was performed and the actual report-handling state, including any separately authorized commit, publication, or sharing action.

## Versioning

Update this version whenever the skill or its bundled resources change:

- Major (`2.0.0`): incompatible workflow or contract changes.
- Minor (`1.1.0`): backward-compatible capabilities or material instruction changes.
- Patch (`1.0.1`): fixes, clarifications, or small refinements.

Version: 1.0.0
