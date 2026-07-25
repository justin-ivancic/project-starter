# Bundled User Skills

This directory versions reusable user-created Codex skills with the starter. Keeping a skill here makes it shareable and reviewable; it does not automatically install, activate, or authorize the skill in an agent environment.

Each individual skill folder is self-contained: `SKILL.md` is required, `agents/openai.yaml` supplies interface metadata, and any referenced guides live under that skill’s `references/` directory.

## Catalog And Dependencies

| Skill | Role | Bundled skill dependencies | Invocation |
| --- | --- | --- | --- |
| `u-coding-doctrine` | Repository implementation, architecture, cleanup, safety, and verification discipline | None | May be selected for repository work |
| `u-codebase-critic` | Exhaustive assessment-only repository audit | None | Explicit user invocation only |
| `u-codebase-steward` | Remediation of a canonical Codebase Critic assessment | `u-codebase-critic`, `u-coding-doctrine`, `u-critical-reviewer` | Explicit user invocation only |
| `u-critical-reviewer` | Fresh, independent completion gate | None | Explicit user invocation or a user-authorized workflow only |
| `u-frontend-technical-ui-ux` | Accessible, responsive, resilient frontend behavior and proof | `u-coding-doctrine`; pairs with `u-frontend-aesthetic-art-director` when visual direction matters | May be selected for relevant frontend work |
| `u-frontend-aesthetic-art-director` | Context-specific visual direction and rendered critique | `u-justins-taste`; pairs with `u-frontend-technical-ui-ux` when implementation or behavior matters | May be selected for relevant visual work |
| `u-justins-taste` | Justin’s restrained, context-led visual judgment layer | None | May be selected for relevant visual work |
| `u-gpt-pro-research` | Repository-aware research and external-advice briefs | None | Use only for an explicitly requested research brief or invocation |

Install dependent skills together. A reference to another skill is a package dependency, not a file that should be copied inside the calling skill.

## Install Or Link

Choose only the skills that fit the project and agent environment. Copy or link each complete skill folder into the environment’s user-skill directory—for Codex, normally `$CODEX_HOME/skills` or `~/.codex/skills`—then restart or rescan the environment if required.

Project-local copies are the shared source. An installed copy may diverge later, so decide which location is authoritative before editing a skill and synchronize intentional updates.

## Maintaining The Packages

- Keep the folder name equal to the `name` in `SKILL.md`.
- Keep every local `references/`, `scripts/`, or `assets/` path relative to its own skill folder.
- Keep machine-specific paths, secrets, credentials, private data, generated caches, and operating-system metadata out of shared packages.
- Update `agents/openai.yaml` when a skill’s purpose, invocation boundary, or default prompt changes.
- Run the available skill validator and verify every referenced local file before publishing changes.
- Do not add auxiliary READMEs, changelogs, or installation guides inside individual skill folders; keep shared catalog and installation guidance in this parent README.
