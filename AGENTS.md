# Agent Instructions

This is the default entry point for agents working in this project. Use it to find the smallest set of current sources needed for the user’s request. Do not turn orientation into a requirement to read the entire repository.

## Start Here

1. Read the current user request and inspect the working tree if this folder already uses Git.
2. Read `0 - headquarter/current-state.md` for the project’s material posture and source-of-truth map.
3. Read the current `# Messages to agent` section of `0 - headquarter/founder-inbox.md`.
4. Consult `0 - headquarter/decision-map.md` when the work could affect accepted product, technical, design, policy, business, rollout, deployment, or risk direction.
5. Read `0 - taskboard/README.md` before selecting or moving a taskboard card.
6. Read `0 - headquarter/unified-systems.md` before creating or changing shared behavior, infrastructure, components, workflows, or cross-cutting state.
7. Inspect only the code, documentation, tasks, tests, research, and evidence needed for the current result.

`0 - archive/` is historical material, not current authority. Do not use it to infer current intent. Open it only when the user explicitly asks for historical retrieval or comparison.

## Authority And Truth

Use this order when sources disagree:

1. The current user request and governing instructions.
2. Accepted decisions and current canonical documentation.
3. Active behavior, contracts, and tests.
4. Recent tasks, research, and audits.
5. Historical material.

Do not let old code, stale documentation, speculative notes, or research silently override accepted direction. Put unresolved founder-owned decisions in the founder inbox; resolve technical questions from the repository and reliable technical evidence.

## Working In The Repository

- Direct user requests take priority over autonomous task selection.
- If the user invokes the Project Steward, follow `0 - headquarter/project-steward - 4.md`.
- Otherwise, use the taskboard only when work is already represented there or when a durable multi-step task genuinely benefits from a card. Do not create process for a tiny request.
- Never implement from `0 - taskboard/00 - not ready/` without explicit founder direction.
- Requested features are reachable and functional by default. Do not add unapproved feature flags, hidden routes, inactive modules, staff-only wrappers, or disabled defaults. Isolate only genuinely unsafe activation.
- Prefer existing systems and current platform capabilities. Update the Decision Map, Current State, Unified Systems map, or durable documentation only when the truth they own materially changes.
- Keep secrets, credentials, private user data, and sensitive operational values out of repository documents, tasks, examples, logs, screenshots, and commits.

## Bundled Skills

The folders under `- skills/` are convenience copies, not active project-local skills. Do not treat their presence in the repository as installation or activation. Use skills installed in the agent environment’s normal skill directory; for Codex, that is `$CODEX_HOME/skills`, or `~/.codex/skills` when `CODEX_HOME` is not set. See `- skills/README.md` when installing copies or checking dependencies.

When a required skill is installed and available, follow it according to its own trigger rules. In particular:

- use `u-coding-doctrine` for repository implementation, structural changes, cleanup, and verification;
- do not implicitly start `u-codebase-critic`, `u-codebase-steward`, or `u-critical-reviewer`; those skills define explicit authorization gates;
- use `user-taste` only after it has been customized; while it remains the bundled placeholder, rely on explicit user direction and the project's creative context.

If a workflow requires a skill or tool that is unavailable, keep the affected path in Review or report the exact limitation. Do not pretend the gate ran.

## Git And External Actions

- If this downloaded folder has no `.git` directory, do not initialize Git unless the user asks.
- If Git is already in use, preserve unrelated work, stage only task-owned files, review the staged diff, and create a clear local commit at a completed task boundary unless the user asks not to.
- Treat nested repositories separately.
- Do not rewrite history, push, open a pull request, deploy, operate infrastructure, change external settings, or send external messages without explicit authorization.

## Completion

Finish with the requested outcome, proportional verification, and a concise account of remaining risk or blockers. Passing checks are evidence, not permission to ignore mismatched behavior, stale documentation, missing review, or an unresolved authority decision.
