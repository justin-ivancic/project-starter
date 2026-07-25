# Project Starter

A practical repository foundation for serious, AI-assisted projects.

Project Starter provides a durable folder structure, a file-based taskboard, a founder decision channel, current-state and systems maps, and a complete stewardship loop. It is designed to help a founder and AI agents keep implementation, decisions, verification, and project memory aligned without turning the repository into process overhead.

## What It Includes

- **Project headquarters** for the founder inbox, current state, durable decisions, unified systems, and stewardship instructions.
- **A visible taskboard** with Not Ready, Inbox, Active, Review, and Done lanes.
- **Clear decision boundaries** between technical work, outside research, founder-owned choices, and external blockers.
- **Verification and review discipline** before work is treated as complete.
- **Dedicated homes** for code, core documentation, research, creative direction, audits, experiments, brainstorming, and reusable skills.
- **Git-ready empty directories** so the complete structure survives cloning and template creation.

## Repository Structure

```text
.
├── 0 - headquarter/       Project orientation, decisions, systems, and stewardship
├── 0 - taskboard/         File-based work lanes from drafting through completion
├── 0 - archive/           Historical material; never a current source of truth
├── - skills/              Project-local or exportable AI-agent skills
├── audits/                Bounded audit outputs and durable findings
├── brainstorming/         Early exploration that is not yet accepted direction
├── bug-proof/             Regression and failure-proofing material
├── code/                  Application code and implementation experiments
├── core-docs/             Durable product, technical, policy, and operating docs
└── creative-direction/    Visual, interaction, voice, and experience direction
```

## Start a New Project

### Recommended: use it as a GitHub template

1. Mark this repository as a **Template repository** in GitHub Settings.
2. Select **Use this template** and create a new repository.
3. Clone the new repository. Its Git history and remote belong to the new project.
4. Complete the personalization checklist below.
5. Commit the personalized baseline before implementation begins.

### Alternative: clone or download

If you clone this repository directly, change `origin` to your own repository before treating the copy as a new project:

```bash
git remote set-url origin https://github.com/YOUR-NAME/YOUR-PROJECT.git
```

If you download the ZIP, initialize Git after extraction:

```bash
git init -b main
git add .
git commit -m "Initialize project"
```

## Personalize Before First Use

The included [`project-steward - 4.md`](0%20-%20headquarter/project-steward%20-%204.md) is an exact working copy from the STSSIS project. It is included as a strong real-world starting point, not as a universal drop-in instruction.

Before running it:

- replace the project name and workspace paths;
- replace `Code/stssis-v2` with the real implementation path;
- update absolute skill links for the local agent environment;
- update research, reviewer, and full-suite-runner assumptions;
- set the project name and first verified facts in `current-state.md`;
- add any immediate founder instruction under `# Messages to agent`;
- remove rules that do not apply, without weakening real safety or review boundaries.

Do not let an agent run the steward loop blindly before this personalization is complete.

## Core Workflow

1. **Orient** from current Git state, founder messages, current state, and the taskboard.
2. **Select** the highest-priority actionable Review, Active, or Inbox task.
3. **Classify uncertainty** as technical, research, founder-owned, safely incomplete, or externally blocked.
4. **Build** one complete, bounded result using existing systems first.
5. **Prove** the result with focused checks, real behavior, and proportional review.
6. **Update truth** only where decisions, current posture, systems, or durable documentation changed.
7. **Commit** only task-owned files in a clear local Git state.

The taskboard tracks work. It does not replace code, tests, the Decision Map, Current State, or durable documentation.

## Key Files

- [`founder-inbox.md`](0%20-%20headquarter/founder-inbox.md): direct founder messages, open founder questions, VPS actions, and public-document impacts.
- [`current-state.md`](0%20-%20headquarter/current-state.md): short, material orientation snapshot.
- [`decision-map.md`](0%20-%20headquarter/decision-map.md): accepted durable decisions and their authority.
- [`unified-systems.md`](0%20-%20headquarter/unified-systems.md): routing map for shared systems and intentional boundaries.
- [`project-steward - 4.md`](0%20-%20headquarter/project-steward%20-%204.md): the end-to-end work, proof, review, and completion loop.
- [`0 - taskboard/README.md`](0%20-%20taskboard/README.md): lane meanings, task shape, and board rules.

## Using Custom Skills

The `- skills/` directory is a repository home for skills you want to share, version, or adapt with the project. A skill is not automatically installed merely because it exists here. Install or link it according to the conventions of the agent environment that will use it, and keep machine-specific paths out of shared instructions where possible.

## License

Project Starter is available under the [MIT License](LICENSE). You may use, copy, modify, distribute, and build on it, including for commercial projects, while preserving the copyright and license notice.
