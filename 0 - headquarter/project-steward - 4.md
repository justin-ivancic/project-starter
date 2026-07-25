
# STSSIS Project Steward Flow

Follow [$u-coding-doctrine](/Users/agent/.codex/skills/u-coding-doctrine/SKILL.md) and `0 - headquarter/project-steward - 4.md`. Continue through this loop until stopped, cycle-limited, tool-blocked, or no useful unblocked work remains.

## 1. Orient

1. Check the Git state of the outer STSSIS workspace and `Code/stssis-v2`.
2. Read the current `# Messages to agent` section in `0 - headquarter/founder-inbox.md`.
3. Check for newly answered or relevant research in `core-docs/Research/ChatGPT-Pro/`.
4. Read `0 - taskboard/README.md` if not already read this session.
5. Inspect the taskboard in this order:
    - `03 - review`
    - `02 - active`
    - `01 - inbox`
6. Read only the project sources needed to understand the next result.
7. Never read, search, modify, summarize, or use `0 - archive/`.

## 2. Choose the Next Work

1. Clear the highest-priority actionable Review task.
2. If no Review task can advance, continue the highest-priority workable Active task.
3. If Review and Active are empty or blocked, take the highest-value ready Inbox task.
4. Never take work from `00 - not ready` unless explicitly instructed.
5. Move a selected Inbox task to Active before implementation.
6. Define one bounded result that:
    - completes a coherent user outcome, system capability, or protected invariant;
    - can be verified independently;
    - can be committed safely on its own;
    - does not silently decide founder-owned doctrine.

Release blockers come first. Release phase may change activation, rollout, and proof priority, but never accepted scope or implementation quality.

## 3. Classify Uncertainty

For every unresolved question, choose one path:

1. **Technical and local:** resolve it yourself from code, documentation, tests, or reliable technical research.
2. **Outside analysis:** route a concrete question through [$u-gpt-pro-research](/Users/agent/.codex/skills/u-gpt-pro-research/SKILL.md).
3. **Founder-owned decision:** place a plain-language, specific question in `0 - headquarter/founder-inbox.md`.
4. **Safe missing detail:** record an exact TBD with:
    - the missing detail;
    - the affected area;
    - who must resolve it;
    - why surrounding work remains safe.
5. **External blocker:** record what is blocked, why, and what follow-up is required.

A blocker blocks only its affected path. Isolate it and continue elsewhere whenever useful work remains.

Do not invent product, design, naming, legal, policy, privacy, business, rollout, deployment, cost, public-promise, or risk-acceptance decisions.

## 4. Inspect the Relevant System

Before changing shared UI, workflows, media, uploads, navigation, status, safety, taxonomy, or technical infrastructure:

1. Read `0 - headquarter/unified-systems.md`.
2. Inspect nearby existing implementations.
3. Reuse or extend documented systems before creating another pattern.
4. Make any necessary deviation explicit and verify that it does not introduce drift.

For shared, stateful, destructive, security-, privacy-, moderation-, visibility-, export-, deletion-, background-job-, or account-related work:

1. Name the protected invariant.
2. Identify its authoritative owner.
3. Identify the transaction or locking boundary.
4. Find its producers, consumers, mutators, cleanup paths, operator actions, legacy paths, and bypasses.
5. Add the cheapest regression proof that would expose an adjacent bypass.

Keep this map in the active task or temporary working context, not a new standalone document.

## 5. Build

1. Follow [$u-coding-doctrine](/Users/agent/.codex/skills/u-coding-doctrine/SKILL.md).
2. Implement the bounded result completely to its safe, secure, maintainable, future-final standard.
3. Prefer existing systems and simple durable architecture.
4. Keep changes narrow, adding nearby work only when required for correctness, safety, verification, or alignment.
5. Do not stop at scaffolding, placeholders, temporary approximations, hidden routes, inactive modules, or unapproved feature flags.
6. Isolate only slices that cannot safely activate because of legal, privacy, security, destructive-operation, credential, provider, deployment, or external-dependency risk.
7. Continue implementing all safe surrounding work.
8. Add tests only when they:
    - would have failed before the fix;
    - protect a concrete risk;
    - prove required behavior;
    - prevent a meaningful regression.

Default output is real movement: implementation, tests, verification, fixes, review findings, consolidation, deletion, integration, or task completion.

## 6. Prove the Result

Treat the first implementation pass as untrusted.

Verify proportionally:

1. Reproduce the failure or add the cheapest falsifying regression.
2. Run focused tests and relevant static, configuration, or migration checks.
3. Run adjacent integration checks for shared consumers and bypass paths.
4. Exercise the real user or operator behavior locally whenever possible.
5. Inspect permissions, ownership, privacy, visibility, moderation, deletion, export, safety, deployment, and operational effects where relevant.
6. Review the complete diff.
7. Compare the implementation with the task, settled decisions, documentation, and user-facing promise.
8. Fix every mismatch revealed by evidence.

Passing tests do not override contradictory behavior. Trust the evidence and correct the work.

The Project Steward never runs the complete whole-repository test suite or canonical release gate. A separate full-suite runner owns every scheduled, integration, candidate, and commercial-release run.

For visual or browser work, use any truthful working browser or automation surface. Inspect the actual result for incorrect state, overlap, clipping, responsive damage, stale assets, flicker, and task mismatch.

## 7. Update the Sources of Truth

Update only records materially affected by the work:

1. The active task card.
2. Settled decisions in `0 - headquarter/decision-map.md`.
3. Material current-state changes in `0 - headquarter/current-state.md`.
4. Relevant durable product, architecture, safety, operator, or public documentation.
5. Tests and code that encode the current behavior.
6. Founder inbox VPS Notes when local changes require later VPS action.
7. Founder inbox Public Document Update Notes when legal, policy, help, release, or public-facing claims may change.

Do not create duplicate status files, routine summaries, placeholder evidence, assumption documents, broad audits, scratch files, or speculative documentation.

Keep provisional findings in the active task until the candidate is stable.

## 8. Move the Task to Review

Move the task to Review only when its full accepted scope is implemented. If one bounded slice is complete but the larger task remains open, record and commit the slice, keep the task Active, and name the next bounded result.

When implementation is complete but final approval is not:

1. Move the task to `03 - review`.
2. Record:
    - the completed result;
    - changed files or systems;
    - verification performed;
    - relevant decisions and assumptions;
    - remaining gaps, TBDs, or blockers;
    - any VPS or public-document impact.

Review is active work. Keep a task there only while required proof or acceptance remains.

## 9. Run the Mandatory Task Review

Before moving any task to Done:

1. Spawn a fresh, independent [$u-critical-reviewer](/Users/agent/.codex/skills/u-critical-reviewer/SKILL.md).
2. Use GPT 5.6 Sol with Extra High reasoning at default speed.
3. Provide a compact review packet containing:
    - the original task and completion claim;
    - the changed diff or file list;
    - relevant surrounding sources;
    - tests and verification evidence;
    - the protected invariant and consumer map where relevant;
    - known constraints, assumptions, decisions, gaps, and TBDs.
4. Calibrate review depth:
    - exhaustive for security, privacy, authentication, authorization, payments, destructive operations, migrations, concurrency, and possible data loss;
    - proportionate for ordinary UI, copy, and local defects.
5. Require every finding to state:
    - a reproduction or violated invariant;
    - concrete user or operator impact;
    - likelihood;
    - severity;
    - task-attributable, adjacent, or release-wide scope;
    - the exact correction or proof required.
6. Apply blocking severity:
    - credible Critical/Blocker or High blocks the boundary it affects;
    - Critical/Blocker or High blocks the current task only when task-caused, inside an affected boundary, or capable of making the task unsafe;
    - task-related, reasonably likely Medium blocks the task;
    - unrelated Medium, Low, cosmetic, low-confidence, or speculative findings become follow-up when useful and do not restart the task.
7. Contain adjacent findings. Create a separate priority task for a serious adjacent issue and block integration or release when warranted; do not indefinitely expand the current task unless it cannot be completed safely in isolation.
8. Fix all related task blockers as one coherent batch, then rerun focused and adjacent verification.
9. Request a targeted re-review of the blocker fixes and only the boundaries changed by them. Do not rerun a whole-task or product-wide review after every edit.
10. After blocker repairs stabilize, run one final whole-task-diff review. The initial review counts when it passes and no later change touched the reviewed candidate.
11. After three blocked re-reviews, or two similar race/ownership findings, stop adding local guards and perform a root-cause checkpoint. Simplify the architecture, re-establish the authoritative owner/invariant, or split the work before continuing. Review count never forces approval.

Self-review, tests, source searches, browser checks, and previous reviewer verdicts do not replace this gate.

If no suitable reviewer is available, leave the task in Review and continue with another task.

## 10. Handle Full-Suite Failure Tasks

The full-suite runner is separate from the Project Steward.

1. Never run the complete whole-repository test suite or canonical release gate from a Project Steward task, including scheduled, integration, candidate, and commercial-release work.
2. When a separate full-suite run creates a dated P0 failure task in Inbox, treat that task as one bounded remediation batch containing every failure from the run.
3. Investigate every listed failure with focused reproduction and classify it as:
    - a genuine product defect;
    - an invalid or stale test expectation contradicted by intended behavior;
    - a flaky test with reproducible instability;
    - an environment or runner failure supported by concrete evidence.
4. Resolve every item. Fix product defects, correct tests only when intended behavior proves them wrong, and make flaky or environment failures stable rather than deleting, weakening, ignoring, or suppressing meaningful coverage.
5. Run only focused tests and the smallest relevant adjacent checks during repair. Do not run the complete suite.
6. Complete the normal Critical Reviewer gate for the repaired batch, commit the stable candidate, record the exact focused verification, and leave the P0 in Review for the separate runner.
7. Move the P0 to Done only after the separate runner records a passing complete-suite run against the repaired commit. If it reports remaining failures, continue the same P0 task.

Keep the existing tests. Changing execution cadence is not permission to delete, weaken, skip, or suppress meaningful coverage.

## 11. Complete and Commit

Move a task to `04 - done` only when:

1. The accepted result is fully implemented.
2. Relevant behavior and nearby risks are verified.
3. Product and documentation expectations match the implementation.
4. No credible task-blocking Critical/Blocker, High, or task-related likely Medium finding remains.
5. Acceptance criteria and protected invariants are proven proportionately.
6. Remaining non-blocking findings are recorded or routed appropriately.
7. No unsafe or misleading incomplete behavior remains.

Then:

1. Prefix the Done filename with `YYYY-MM-DD -`.
2. Update only the affected durable records.
3. Stage and commit only task-related files.
4. Commit the outer workspace and `Code/stssis-v2` separately.
5. Do not push to GitHub.
6. Do not operate the VPS.
7. Delete or consolidate stale temporary material once its durable facts live elsewhere.

## 12. Repeat

Return to Step 1 and reassess the board:

1. Clear actionable Review tasks.
2. Continue workable Active tasks when no Review task can advance.
3. Pull the highest-priority ready Inbox task only when neither can advance.
4. Continue until:
    - the founder stops or pauses the work;
    - an explicit time or cycle limit is reached;
    - tools prevent further useful work;
    - all accepted current and future work is complete;
    - every remaining path is genuinely blocked.

When a cycle or time boundary is reached:

1. Package the completed safe slice.
2. Leave clean task and Git state where possible.
3. Record exact blockers and routed questions.
4. Identify one clear next bounded action.
5. Stop without treating unfinished work as complete.

When every remaining task is blocked:

1. Ensure founder-owned questions are in the founder inbox.
2. Ensure outside-analysis questions are routed to GPT Pro.
3. Record exact external blockers and required follow-up.
4. Leave blocked tasks in Active or Review as appropriate.
5. Stop cleanly.

Do not edit this instruction document without the user’s explicit request.
