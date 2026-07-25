# Critical Codebase Assessment

Date: YYYY-MM-DD
Assessment target: ABSOLUTE_TARGET_PATH
Assessment root: ABSOLUTE_ASSESSMENT_ROOT
Assessment file: ABSOLUTE_REPORT_PATH
Assessor: Codex using `$u-codebase-critic`
Outcome: Pending

> This report may contain sensitive security or privacy evidence. Keep it local by default, redact secret values, and do not publish or commit it without explicit approval.

No code remediation was performed. The assessment report is the only persistent target-repository file created by this pass.

## Report Contents

1. Executive Summary
2. Assessment Basis
3. Evidence Snapshot
4. Scope And Current Intent
5. File Inventory And Primary Coverage
6. Dimension Coverage Matrix and D04 catalog receipt
7. Canonical Findings
8. Advisories, Hardening Opportunities, And Reviewed Hotspots
9. Independent Validation Ledger
10. Candidate Disposition Appendix
11. Verification Performed
12. Assessment Limitations And Snapshot Drift
13. Exact Per-File Coverage Ledger
14. Final Notes

## Executive Summary

Overall outcome: Pending

Use `Complete` only when the frozen inventory reconciles with no anomaly, all 33 dimensions are `Complete`, `Complete — no finding`, or evidence-backed `Not applicable`, required validation completes, and end-state drift is handled. Any blocked or deferred dimension, missing path, duplicate primary state, ledger path absent from the snapshot, failed count equation, unresolved required validation, or material snapshot drift requires `Incomplete — <reason>`. This outcome describes assessment completeness, not launch readiness or codebase safety.

Top canonical risks:

1. Pending

Strongest recurring root causes:

- Pending

Recommended remediation order:

1. Pending

Material limitations:

- Pending

### Canonical Finding Counts

Count each confirmed canonical finding once. Raw dimension candidates, merged duplicates, advisories, intended behavior, historical issues, insufficient evidence, refuted claims, and blocked validation do not increase severity totals.

| Severity | Canonical findings |
| --- | ---: |
| 5 | 0 |
| 4 | 0 |
| 3 | 0 |
| 2 | 0 |
| 1 | 0 |
| **Total** | **0** |

### Candidate Disposition Counts

| Disposition | Count |
| --- | ---: |
| Canonical finding | 0 |
| Merged into canonical finding | 0 |
| Advisory / future hardening | 0 |
| Intended behavior / accepted constraint | 0 |
| Historical / already resolved | 0 |
| Insufficient evidence | 0 |
| Refuted | 0 |
| Blocked validation | 0 |
| **Raw candidates** | **0** |

## Assessment Basis

Bundled doctrine:

- `references/coding-guide.md`
- `references/vibecoding-blunder-prevention-guide.md`
- `references/audit-dimensions.md`

Repository-local instructions read:

- Pending

Product/current-intent sources read:

- Pending

Runtime and manifest sources read:

- Pending

## Evidence Snapshot

| Field | Value |
| --- | --- |
| Audit start | Pending |
| Audit end | Pending |
| Target root | Pending |
| Repository root(s) | Pending |
| Branch(es) | Pending |
| Commit SHA(s) | Pending |
| Dirty tracked paths | Pending |
| Untracked paths in scope | Pending |
| Dirty diff digest | Pending |
| Per-file hash manifest / inventory digest | Pending |
| Worker slots available | Pending |
| Model/reasoning/speed controls | Applied / unavailable / blocked |
| End-state drift check | Pending |

If the target contains nested repositories, list every repository and SHA. Redact content, never path names needed for coverage, when dirty files may contain secrets.

## Scope And Current Intent

Included:

- Pending

Excluded from the requested assessment:

- Pending

Current product/system intent:

- Pending

Critical user and system flows:

- Pending

Explicitly out-of-scope, abandoned, prototype, or stale concepts:

- Pending

Generated, vendored, binary, cache, build, or runtime artifacts identified:

- Pending

## File Inventory And Primary Coverage

Search results, metrics, tests, and directory summaries do not count as file review. A primary-reviewed file received substantive direct source inspection by one accountable reviewer.

### Coverage Invariant

`inventory total = primary reviewed by main + primary reviewed by subagent + excluded + blocked`

| Disjoint state | Count | Notes |
| --- | ---: | --- |
| Primary reviewed — main | 0 |  |
| Primary reviewed — subagent | 0 |  |
| Excluded | 0 |  |
| Blocked | 0 |  |
| **Inventory total** | **0** |  |

Mechanical reconciliation:

- Missing inventory paths: 0
- Duplicate primary states: 0
- Ledger paths absent from snapshot: 0
- Count equation: Pending
- D33 independent result: Pending

If blocked or missing is nonzero, any primary state is duplicated, any ledger path is absent from the snapshot, or the equation fails, the final outcome must be `Incomplete — coverage reconciliation failed`.

### Holistic Source Shards

| Shard | Fresh reviewer | Assigned files | Primary reviewed | Excluded | Blocked | Raw candidates | Notes |
| --- | --- | ---: | ---: | ---: | ---: | ---: | --- |
| S01 | Pending | 0 | 0 | 0 | 0 | 0 |  |

## Dimension Coverage Matrix

Final status must be `Complete`, `Complete — no finding`, `Not applicable: evidence`, `Blocked: reason`, or `Deferred: user-approved reason`. The matrix references canonical IDs and candidate dispositions; it does not duplicate full finding prose.

| ID | Exact dimension | Fresh reviewer | Status | Supporting files read | Raw candidates | Canonical IDs | Other dispositions / limitations |
| --- | --- | --- | --- | ---: | ---: | --- | --- |
| D01 | Maintainability |  | Pending | 0 | 0 |  |  |
| D02 | Structure |  | Pending | 0 | 0 |  |  |
| D03 | Technical debt |  | Pending | 0 | 0 |  |  |
| D04 | AI/vibecoding blunders |  | Pending | 0 | 0 |  |  |
| D05 | Duplication |  | Pending | 0 | 0 |  |  |
| D06 | Dead code |  | Pending | 0 | 0 |  |  |
| D07 | Stale intent |  | Pending | 0 | 0 |  |  |
| D08 | Security risk |  | Pending | 0 | 0 |  |  |
| D09 | Privacy risk |  | Pending | 0 | 0 |  |  |
| D10 | Performance cliffs |  | Pending | 0 | 0 |  |  |
| D11 | Tests drift |  | Pending | 0 | 0 |  |  |
| D12 | Docs drift |  | Pending | 0 | 0 |  |  |
| D13 | Refactor opportunities |  | Pending | 0 | 0 |  |  |
| D14 | Correctness |  | Pending | 0 | 0 |  |  |
| D15 | Product-intent alignment |  | Pending | 0 | 0 |  |  |
| D16 | Current-intent drift |  | Pending | 0 | 0 |  |  |
| D17 | Duplicate systems |  | Pending | 0 | 0 |  |  |
| D18 | Reusable-system drift |  | Pending | 0 | 0 |  |  |
| D19 | Zombie code |  | Pending | 0 | 0 |  |  |
| D20 | Misleading names |  | Pending | 0 | 0 |  |  |
| D21 | Bad ownership boundaries |  | Pending | 0 | 0 |  |  |
| D22 | Oversized files |  | Pending | 0 | 0 |  |  |
| D23 | Oversized functions |  | Pending | 0 | 0 |  |  |
| D24 | Unnecessary complexity |  | Pending | 0 | 0 |  |  |
| D25 | Unsafe boundaries |  | Pending | 0 | 0 |  |  |
| D26 | Brittle verification |  | Pending | 0 | 0 |  |  |
| D27 | Large, complex, risky, shared, or high-churn areas |  | Pending | 0 | 0 |  |  |
| D28 | Security-sensitive areas |  | Pending | 0 | 0 |  |  |
| D29 | Data-lifecycle areas |  | Pending | 0 | 0 |  |  |
| D30 | Public-facing areas |  | Pending | 0 | 0 |  |  |
| D31 | Cross-domain files |  | Pending | 0 | 0 |  |  |
| D32 | Abandoned or prototype concepts |  | Pending | 0 | 0 |  |  |
| D33 | Coverage/accounting of every hand-maintained code-related file |  | Pending | 0 | 0 |  |  |

### D04 AI-Blunder Catalog Receipt

Resolve every catalog category as `Checked`, `Not applicable: evidence`, or `Blocked: reason`. Reference canonical IDs or candidate dispositions; do not repeat full finding prose. Any blocked category forces D04 to `Blocked: reason` and the overall assessment to `Incomplete`; D04 is complete only when all categories are checked or evidence-backed not applicable.

| Catalog category | Status | Evidence inspected | Canonical IDs / disposition |
| --- | --- | --- | --- |
| Fake completion | Pending |  |  |
| Context loss and product-intent drift | Pending |  |  |
| Patch stacking and Frankenstein architecture | Pending |  |  |
| Hallucinated APIs and outdated library usage | Pending |  |  |
| Hallucinated dependencies and slopsquatting risk | Pending |  |  |
| Insecure defaults | Pending |  |  |
| Client-side trust mistakes | Pending |  |  |
| Broken authentication and authorization | Pending |  |  |
| Injection vulnerabilities | Pending |  |  |
| Secret leakage | Pending |  |  |
| Data exposure and privacy mistakes | Pending |  |  |
| Shallow test theatre | Pending |  |  |
| Passes tests but wrong behavior | Pending |  |  |
| Error-handling fairy tales | Pending |  |  |
| Race conditions, idempotency, and double-submit bugs | Pending |  |  |
| Database and migration blunders | Pending |  |  |
| Configuration and environment mistakes | Pending |  |  |
| Overbroad permissions and excessive agency | Pending |  |  |
| Prompt injection against coding agents | Pending |  |  |
| Performance cliffs | Pending |  |  |
| UI polish gaps hidden by AI demos | Pending |  |  |
| Documentation lies | Pending |  |  |
| Type-safety erosion | Pending |  |  |
| Review-burden externalities | Pending |  |  |

## Canonical Findings

Sort canonical findings by severity, then impact and confidence. Use one full record per root cause. Cite evidence against the frozen snapshot with exact `path:line` or `path:symbol` anchors.

### CC-001 — [Severity 5–1] Title

- Primary dimension:
- Dimension tags:
- Confidence: High / Medium / Low
- Source candidates and reviewers:
- Affected paths / boundary:
- Confirmation: Main-confirmed; independent validation not required / Independently confirmed / Independently confirmed with adjustment

Evidence:

- `path/to/file.ext:line` — concise observed source fact.

Observed failure or risk:

Pending

Why it matters:

Pending

Counterevidence, guards, or uncertainty:

Pending

Long-term direction:

Pending

Confirmation evidence:

- Main critic:
- Independent validator(s): Not required / reviewer names
- Direct evidence checked:
- Decision and rationale:

## Advisories, Hardening Opportunities, And Reviewed Hotspots

Keep useful observations here when they are not current canonical defects: intentional behavior, accepted constraints, future hardening, high-risk areas reviewed without a finding, and negative/refuting evidence. Do not assign them severity or include them in finding totals.

| ID | Type | Area | Evidence | Why recorded | Related dimensions/findings |
| --- | --- | --- | --- | --- | --- |
| A-001 | Advisory / intended / hotspot / refutation |  |  |  |  |

## Independent Validation Ledger

Every proposed severity-5 and severity-4 candidate and every disputed, low-confidence, or unusually consequential severity-3 candidate must appear here, including rejected or blocked validation.

| Candidate / canonical ID | Fresh validator | Direct files checked | Result | Independent severity | Adjustment, rejection, or blocker rationale |
| --- | --- | --- | --- | ---: | --- |
|  |  |  |  |  |  |

## Candidate Disposition Appendix

Every raw worker candidate receives exactly one final disposition. Preserve provenance even when several candidates merge.

| Raw candidate | Dimension | Reviewer | Proposed severity | Disposition | Canonical ID / evidence-backed reason |
| --- | --- | --- | ---: | --- | --- |
|  |  |  |  |  |  |

Allowed dispositions:

- `Canonical: CC-xxx`
- `Merged into CC-xxx`
- `Advisory / future hardening`
- `Intended behavior / accepted constraint`
- `Historical / already resolved at snapshot`
- `Insufficient evidence`
- `Refuted`
- `Blocked validation`

`Blocked validation` is never a canonical finding and never enters severity totals. Preserve it here and in the independent validation ledger as unresolved evidence.

## Verification Performed

### Non-mutating checks run

| Check | Exact command or method | Result | Evidence strengthened | Tracked/source mutation check |
| --- | --- | --- | --- | --- |
|  |  |  |  |  |

### Checks failed

| Check | Failure summary | Related finding or limitation |
| --- | --- | --- |
|  |  |  |

### Checks intentionally not run

| Check | Reason it was unsafe, mutating, unavailable, or disproportionate | Resulting uncertainty |
| --- | --- | --- |
|  |  |  |

### Checks blocked

| Check | Attempts | Blocker | Resulting uncertainty |
| --- | --- | --- | --- |
|  |  |  |  |

### Visual / Browser Verification

Status: Performed / Not applicable / Blocked

Surfaces and states inspected:

- Pending

Evidence and limitations:

- Pending

## Assessment Limitations And Snapshot Drift

- Unreviewed or blocked source:
- Unavailable services, environments, or credentials:
- Dynamic, generated, reflective, external, or deployment behavior not provable statically:
- End-state repository changes and re-review performed:
- Remaining uncertainty:

## Exact Per-File Coverage Ledger

Every frozen-inventory path appears exactly once. Supporting reads may list multiple dimension reviewers but do not change the primary state or unique counts.

| Exact path | Snapshot hash | Primary state | Primary reviewer / shard | Supporting dimension reviewers | Substantive receipt, exclusion reason, or blocker |
| --- | --- | --- | --- | --- | --- |
| `path/to/file` | `sha256:...` | Primary reviewed — subagent | reviewer / S01 | D08, D14 | Purpose, runtime role, important boundaries, and related tests inspected |

## Final Notes

- Overall outcome:
- Coverage invariant:
- All 33 dimensions resolved:
- Strongest recurring pattern:
- Recommended remediation order:
- Visual/browser status:
- No remediation performed: yes
- Report handling: Not staged/committed/pushed/published/shared, or exact separately authorized action and authorization
