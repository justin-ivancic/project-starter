# Project Taskboard

This folder is the working taskboard for concrete tasks, bugs, polish work, and implementation-ready ideas. Task files move between folders so the project’s active state remains visible without a second tracking system.

The Project Steward defines the full work and review loop. This README defines the board itself.

## Folder Meanings

### `00 - not ready`

Founder-only drafting space for rough tasks, unfinished thoughts, and work that is explicitly not ready for implementation.

Agents must not select or implement work from this lane unless the founder explicitly moves or directs it into a ready lane.

### `01 - inbox`

Tasks that are ready to be selected and implemented.

Put priority in the filename with `P0 -`, `P1 -`, `P2 -`, and so on. Do not duplicate priority metadata inside the task body.

### `02 - active`

Tasks currently being worked on. Move a selected Inbox task here before implementation begins.

### `03 - review`

Tasks whose accepted scope appears implemented but still needs proportional proof, independent review, founder acceptance, or another explicit completion gate.

### `04 - done`

Tasks that are fully implemented, verified, reviewed as required, and aligned with their accepted expectations.

Prefix Done filenames with the last meaningful work date:

```text
YYYY-MM-DD - Task Name.md
```

## Task Card Shape

Keep task cards small enough to scan and complete. Use only the sections the task needs.

```markdown
# Task name

## Outcome

Describe the user, operator, or system result.

## Scope

Name the affected surface and important boundaries.

## Acceptance

- Observable condition that must be true.
- Risk or edge case that must remain protected.

## Verification

- Check that can falsify the implementation.

## Work Notes

Record only decisions, progress, blockers, and evidence needed to finish or review this task.
```

## Agent Workflow

1. Choose the highest-priority actionable task according to the Project Steward.
2. Move a selected Inbox task to Active before implementation.
3. Define one bounded, independently verifiable result.
4. Work within the accepted scope and update the card with material evidence or blockers.
5. Move the task to Review only when its full accepted scope is implemented.
6. Run the required proof and independent review.
7. Fix task-blocking findings and reverify the affected boundary.
8. Move the task to Done only when the completion conditions are actually met.

## Rules

- Never implement work from `00 - not ready` without explicit founder direction.
- A blocker blocks only its affected path; isolate it and continue safe work elsewhere.
- Keep product, design, naming, legal, policy, business, rollout, deployment, public-promise, and risk-acceptance decisions with their authorized owner.
- Requested features should be reachable and functional by default unless a real safety boundary or an explicitly accepted gate applies.
- Do not stop at scaffolding, placeholders, inactive modules, hidden routes, or unapproved feature flags.
- Update the Decision Map or another canonical document when work creates a durable decision.
- Update Current State only for a material posture change.
- Keep secrets, credentials, private user data, and sensitive evidence out of task cards.
- The taskboard tracks work; it does not replace code, tests, durable documentation, or the Decision Map.

## Done Cleanup

The Done lane is a short-term proof buffer, not the permanent archive.

During an explicit cleanup pass, keep only recent or high-signal cards whose context is still useful. Before removing an old Done card, move any durable decision or evidence into its owning source of truth and update live references.
