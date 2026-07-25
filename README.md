# Project Starter

A practical repository foundation for serious, AI-assisted projects.

Project Starter provides a durable folder structure, a file-based taskboard, a founder decision channel, current-state and systems maps, and a complete stewardship loop. It is designed to help a founder and AI agents keep implementation, decisions, verification, and project memory aligned without turning the repository into process overhead.

## What It Includes

- **A root agent entry point** that explains where to orient, what owns each kind of truth, and how to work safely.
- **Project headquarters** for the founder inbox, current state, durable decisions, unified systems, and stewardship instructions.
- **A visible taskboard** with Not Ready, Inbox, Active, Review, and Done lanes.
- **Clear decision boundaries** between technical work, outside research, founder-owned choices, and external blockers.
- **Verification and review discipline** before work is treated as complete.
- **Dedicated homes** for code, core documentation, research, creative direction, audits, experiments, brainstorming, and reusable skills.
- **Placeholder-backed empty directories** so the complete structure survives ZIP downloads and version control.

## Repository Structure

```text
.
├── AGENTS.md              Default navigation and operating rules for coding agents
├── 0 - headquarter/       Project orientation, decisions, systems, and stewardship
├── 0 - taskboard/         File-based work lanes from drafting through completion
├── 0 - archive/           Historical material; never a current source of truth
├── - skills/              Project-local or exportable AI-agent skills
├── audits/                Bounded audit outputs and durable findings
├── brainstorming/         Early exploration that is not yet accepted direction
├── bug-proof/             Regression and failure-proofing material
├── code/                  Application code
│   └── experiments/       Disposable implementation exploration, not production truth
├── core-docs/             Durable product, technical, policy, and operating docs
│   └── research/          Research inputs and answered outside-analysis questions
└── creative-direction/    Visual, interaction, voice, and experience direction
```

Use only the folders that earn a real purpose in the project. Empty folders are available destinations, not a requirement to produce documents or process.

## How To Navigate

For a quick human orientation, read this README and [`current-state.md`](0%20-%20headquarter/current-state.md). Use the Decision Map for accepted durable direction, the founder inbox for current founder messages and unresolved founder-owned questions, and the taskboard for concrete work.

Agents begin with [`AGENTS.md`](AGENTS.md). It routes them through the same sources without requiring every document to be read for every task. Detailed evidence stays with the code, task, audit, research note, or durable document that owns it.

## Folder Use

| Folder | Put Here | Keep Elsewhere |
| --- | --- | --- |
| `0 - headquarter/` | Current posture, accepted durable decisions, founder questions, shared-system routing, and stewardship instructions | Detailed task history, raw research, routine test output, and speculative notes |
| `0 - taskboard/` | Concrete, bounded work moving from drafting through implementation and review | Canonical product truth, long-form specifications, and permanent evidence |
| `0 - archive/` | Material intentionally retired from current use but retained for history | Anything an agent should treat as current authority |
| `- skills/` | Self-contained, reusable agent-skill packages and the parent catalog | Machine-specific paths, secrets, caches, and project facts that belong in headquarters or core docs |
| `audits/` | Bounded assessment reports and durable findings | Routine progress notes; never publish sensitive exploit or secret material by default |
| `brainstorming/` | Early exploration and alternatives that have not been accepted | Settled decisions or implementation-ready tasks |
| `bug-proof/` | Durable failure reproductions, regression evidence, and incident-proofing material that does not belong beside the code | Duplicate copies of tests or implementation-owned fixtures |
| `code/` | The project’s implementation, tests, configuration, and code-adjacent instructions | Product decisions, raw research, or unrelated operational notes |
| `code/experiments/` | Disposable prototypes used to answer a specific implementation question | Production paths or behavior treated as complete |
| `core-docs/` | Durable product, technical, policy, safety, and operating documentation | Temporary status reports, task cards, and unaccepted ideas |
| `core-docs/research/` | Research inputs, answered outside-analysis questions, and evidence awaiting integration | Accepted direction that should be promoted into the Decision Map or canonical docs |
| `creative-direction/` | Accepted visual, interaction, voice, and experience direction | Application code or generic inspiration with no project decision attached |

## Start a New Project

### Recommended: download the folder

1. On GitHub, select **Code → Download ZIP**.
2. Extract the ZIP and rename the folder for the new project.
3. Complete the personalization checklist below.
4. Begin using the structure as an ordinary folder.

A downloaded ZIP contains no `.git` directory, does not retain this repository's remote, and does not become a repository unless you explicitly initialize Git.

### Optional: add Git later

If the project should be version-controlled, initialize Git when you are ready:

```bash
git init -b main
git add .
git commit -m "Initialize project"
```

Cloning is also available when you intentionally want a Git repository from the start. A clone includes Git history and points `origin` at this source repository, so change or remove that remote before using the clone as an independent project:

```bash
git remote remove origin
```

## Personalize Before First Use

The included [`project-steward - 4.md`](0%20-%20headquarter/project-steward%20-%204.md) is a portable stewardship loop for this structure. Keep it only if the project benefits from a file-based work queue and repeated agent-led execution.

Before running it:

- set the project name and first verified facts in `current-state.md`;
- identify the real implementation location and keep its setup and verification commands beside the code;
- record any nested repositories, deployment boundaries, or separate release-gate runner in current project documentation;
- install or link the bundled skills that the chosen workflow needs;
- add any immediate founder instruction under `# Messages to agent`;
- remove workflow rules that genuinely do not apply, without weakening real safety, review, or authority boundaries.

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

- [`AGENTS.md`](AGENTS.md): default orientation, authority, navigation, skill, Git, and external-action rules for agents.
- [`founder-inbox.md`](0%20-%20headquarter/founder-inbox.md): direct founder messages, open founder questions, deployment or operations actions, and public-document impacts.
- [`current-state.md`](0%20-%20headquarter/current-state.md): short, material orientation snapshot.
- [`decision-map.md`](0%20-%20headquarter/decision-map.md): accepted durable decisions and their authority.
- [`unified-systems.md`](0%20-%20headquarter/unified-systems.md): routing map for shared systems and intentional boundaries.
- [`project-steward - 4.md`](0%20-%20headquarter/project-steward%20-%204.md): the end-to-end work, proof, review, and completion loop.
- [`0 - taskboard/README.md`](0%20-%20taskboard/README.md): lane meanings, task shape, and board rules.
- [`- skills/README.md`](-%20skills/README.md): bundled skill catalog, dependency map, and installation guidance.

## Using Custom Skills

The `- skills/` directory is a repository home for skills you want to share, version, or adapt with the project. A skill is not automatically installed merely because it exists here. See its [catalog and dependency map](-%20skills/README.md) before installing or invoking a workflow, and keep machine-specific paths out of shared instructions.

## License

Project Starter is available under the [MIT License](LICENSE). You may use, copy, modify, distribute, and build on it, including for commercial projects, while preserving the copyright and license notice.
