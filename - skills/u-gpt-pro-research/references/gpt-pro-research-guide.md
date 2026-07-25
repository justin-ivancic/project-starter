# GPT Pro Research Brief Guide

Use this reference when the core workflow needs a fuller template, a portable fallback, or help turning an ambiguous topic into a high-leverage repository investigation.

## Contents

1. Question selection
2. Decision authority
3. Repository-aware context design
4. Research contracts
5. Repository-aware template
6. Portable fallback template
7. Task-specific patterns
8. Example
9. Failure modes

## 1. Select The Question Before Writing The Prompt

The primary work is choosing what the answering agent should investigate. A polished prompt cannot rescue a low-value question.

Look for uncertainty that is both consequential and answerable through evidence. Useful targets often include:

- A disputed architectural boundary.
- A failure whose actual cause is unclear.
- A technology choice with expensive downstream consequences.
- A proposed refactor whose benefits or migration cost are uncertain.
- A product decision where implementation reality constrains the options.
- A conflict between documented intent and actual behavior.

Frame the question around the decision the answer should unlock.

Weak:

> Review our synchronization architecture and suggest improvements.

Stronger:

> Given the current offline write path, retry model, and conflict behavior in this repository, should synchronization continue to derive operations from persisted snapshots, or should intent be recorded explicitly at the domain boundary? Recommend the smallest durable architecture that supports multi-device correctness without introducing collaboration-grade complexity prematurely.

The stronger question identifies the decision, competing directions, and evaluation criteria while still allowing the investigator to reject the framing.

### A useful selection test

Ask:

1. What important decision becomes easier after this research?
2. What costly mistake could this research prevent?
3. What evidence can the answering agent inspect?
4. Is the question narrow enough for depth but broad enough to challenge assumptions?
5. Would a generic answer be obviously inadequate?

If the brief cannot answer those questions, tighten the research target before adding context.

## 2. Preserve Decision Authority

Research quality does not grant product authority. Explicit user direction about the user-facing product is controlling unless the user asks for that direction itself to be challenged.

Research permission also does not grant action authority. Even when the user explicitly requests critique, every finding and recommendation remains non-binding and operationally inert. The user must deliberately accept a specific recommendation and authorize its execution in a later follow-up before any implementation or external action begins.

Distinguish four categories:

- **Settled product direction:** what the product should be, do, feel like, prioritize, expose, or avoid. Preserve it.
- **Non-binding product advice:** risks, implications, and alternatives the research agent may surface for the user's consideration. Label it clearly as advice.
- **Delegated technical judgment:** architecture, correctness, security, performance, maintainability, migrations, testing, and implementation choices the user wants expert help deciding. Recommend decisively here.
- **Cross-boundary decisions:** technical realities that would materially alter user-facing behavior, scope, experience, or product intent. Explain the conflict and options, then return the product tradeoff to the user.
- **Action authority:** absent throughout the research task. Analysis, critique, a proposed plan, and even an urgent finding do not authorize follow-through.

Do not claim that a preferred implementation pattern is technically mandatory merely to override the user's product choice. When the stated direction is feasible, solve within it. When it is infeasible or creates a material risk, demonstrate that with evidence and ask the user to choose among the real tradeoffs.

Useful wording:

> Treat the founder's explicitly stated user-facing product direction as controlling. You may identify consequences and offer clearly labeled, non-binding alternatives, but do not override or reinterpret that direction. For technical decisions delegated to you, recommend the strongest approach. If a genuine technical constraint would force a product change, explain the evidence and options and return that tradeoff to the founder.

Add this execution boundary to every brief:

> This task is research and advice only. Every finding, criticism, recommendation, and proposed plan is non-binding and authorizes no follow-through. Do not modify files, start remediation, create tasks or tickets, contact external systems, or take any other action based on your own output. Implementation requires the founder to accept a specific recommendation and explicitly authorize it in a later follow-up.

## 3. Design Context For A Repository-Aware Agent

Repository access changes what belongs in a prompt.

### Point to discoverable evidence

Prefer:

- Paths and symbols.
- Relevant tests or fixtures.
- Configuration entry points.
- Architecture or product documentation.
- Database migrations and schemas.
- A diff, branch, commit, or worktree when the research concerns changes.
- Commands or logs already available in the workspace.

Explain why an entry point may matter, but do not summarize it so aggressively that the summary becomes the investigator’s assumed truth.

Use wording such as:

> Begin with the paths below, but treat them as leads rather than complete scope. Trace their callers, consumers, tests, data ownership, configuration, and neighboring systems wherever the evidence leads.

### Append what cannot be discovered

Include:

- The user’s actual decision, priorities, and settled product direction.
- Product strategy or desired experience.
- Legal, commercial, deployment, or organizational constraints.
- Relevant prior discussion and rejected approaches.
- Runtime or production evidence absent from the repository.
- Time horizon and compatibility expectations.
- Whether the target is research-only or may make changes.

### Identify the authoritative state only when needed

If the answer depends on current changes, specify the relevant branch, diff, worktree, or uncommitted files. Do not add git boilerplate when the research concerns the repository generally.

### Avoid premature interpretation

Separate:

- **Known fact:** directly observed or supplied evidence.
- **Hypothesis:** plausible but unverified explanation.
- **Preference:** desired direction that can be challenged.
- **Constraint:** requirement the recommendation must obey.

This prevents the prompt-writing agent from laundering its own assumptions into the research premise.

## 4. Write A Tailored Research Contract

The research contract tells the answering agent what rigor is required. It should not prescribe the answer or become a generic compliance checklist.

Select the clauses that matter:

### Repository evidence

> Inspect the actual implementation, tests, configuration, documentation, and relevant history before reaching a conclusion. Cite the concrete paths, symbols, or changes that support material claims.

### Scope expansion

> The listed files are starting points, not assumed boundaries. Follow call paths, data flow, ownership, generated code, configuration, and downstream consumers where relevant.

### Epistemic clarity

> Distinguish what the repository demonstrates from what you infer and what you recommend. Label uncertainty instead of filling gaps with confident assumptions.

### Contradictions

> Look for disagreement between implementation, tests, documentation, migrations, configuration, and stated intent. Treat those contradictions as evidence rather than automatically choosing one source as authoritative.

### External research

> For changing technical facts, use current primary sources and cite them near the supported claim. Connect external research back to the constraints and implementation in this repository.

### Challenge and recommendation

> Do not assume the current framing or proposed options are correct. Consider better alternatives, but clearly identify the final direction you recommend and why it is superior here.

Use that clause for technical framing. When explicit product direction exists, add:

> Preserve the founder's stated product direction. Product alternatives are non-binding unless open-ended product critique was requested. If technical evidence creates a real conflict with that direction, explain the consequences and options without choosing the product tradeoff on the founder's behalf.

### Final-quality implementation

> Optimize for the durable, production-quality solution. Separate any necessary transition from the desired end state, and include implementation implications, risks, edge cases, and verification.

### Research-only boundary

> Investigate and advise only. Every finding, criticism, recommendation, and proposed plan is non-binding and operationally inert. Do not modify repository files, start remediation, create tasks or tickets, create external records, contact external systems, or take deployment actions. A later explicit user follow-up must accept a specific recommendation and authorize its execution before any follow-through begins.

Always use this boundary. A critique request cannot authorize implementation in the same research task; follow-through requires a later explicit user request after the advice exists and can be reviewed.

## 5. Repository-Aware Template

```markdown
# [Focused title]

## Plain Language For Founder

[What we need to learn and what decision the answer should support, in 1-3 sentences.]

## Primary Question

[One consequential question.]

## Why This Matters

[Decision stakes, risk, or blocked work.]

## Repository Starting Points

- `[path, symbol, test, document, or change]` — [why it may matter]

These are starting points, not assumed scope boundaries. Follow the evidence into
other parts of the repository where necessary.

## Known Facts

- [Directly supported fact]

## Hypotheses Or Uncertainty

- [Unverified interpretation or open question]

## Context Outside The Repository

- [User intent, production evidence, prior decision, or other inaccessible context]

## Constraints And Evaluation Criteria

### Settled product direction

- [Controlling user-facing decision; do not silently override]

### Hard constraints

- [Must be obeyed]

### Challengeable preferences

- [May be rejected with good reason]

## Decision Authority

- Product and user-facing advice is [non-binding / explicitly open for critique].
- Technical judgment is delegated for [named areas].
- Return any product-changing technical tradeoff to the founder.
- All findings and recommendations remain inert until accepted and authorized in a later follow-up.

## Research Contract

[Selected evidence, scope, critique, and authorization requirements.]

## Requested Outcome

[The exact recommendation, diagnosis, comparison, plan, or validation needed.]
```

This is a menu, not paperwork. Combine or omit sections when the result remains clear.

## 6. Portable Fallback Template

Use this only when the destination cannot inspect the repository.

```markdown
# [Focused title]

## Plain Language For Founder

[The question and supported decision.]

## Primary Question

[One consequential question.]

## Project And Current Objective

[Only the orientation needed for this question.]

## Relevant Architecture And Behavior

[A faithful, bounded description of the system and data flow.]

## Selected Evidence

### `[file path or evidence source]`

[Purpose, relevance, and necessary excerpt or observation.]

## Known Facts, Hypotheses, And Missing Evidence

[Keep them visibly separate.]

## Constraints And Evaluation Criteria

[Settled product direction and hard constraints first; preferences second.]

## Decision Authority

[What is settled, what advice is non-binding, what technical judgment is delegated,
what cross-boundary tradeoffs must return to the founder, and that all follow-through
requires a later explicit authorization.]

## Previous Attempts Or Rejected Options

[Only those that could change the recommendation.]

## Requested Outcome

[Recommendation, reasoning, implementation implications, risks, and validation.]
```

Do not claim the prompt is complete merely because it follows the template. If omitted repository evidence could materially reverse the recommendation, narrow the question or state that repository access is required.

## 7. Task-Specific Patterns

### Architecture

Direct the investigator toward ownership, boundaries, invariants, current pain, data flow, deployment constraints, and migration paths. Ask for the simplest architecture that meets the real horizon rather than speculative maximalism.

### Debugging

Include expected and actual behavior, reproduction conditions, frequency, environment, logs, and production observations that are not in the repository. Require the agent to trace and verify the root cause before designing the fix.

### Technology or dependency research

State the concrete capability being selected and evaluation criteria. Require current primary-source research plus inspection of local compatibility constraints. Ask for a final recommendation, rejected alternatives, adoption cost, and exit risk.

### Code or design review

Identify the code’s purpose, invariants, and relevant change or subsystem. Require investigation beyond the obvious entry point when callers, consumers, persistence, security, or migrations can affect correctness.

### UX and product

Provide user intent and settled product direction that code cannot reveal. Direct the agent to inspect the implemented flow, state coverage, responsive behavior, accessibility evidence, wording, tests, and design-system patterns before recommending changes. Unless open-ended critique was requested, keep alternatives non-binding and optimize within the founder's direction.

### Implementation planning

Define current and target states, operational constraints, migration or compatibility requirements, validation, and completion criteria. Require sequencing that reaches the clean end state without leaving duplicate systems or indefinite scaffolding.

## 8. Example

```markdown
# Decide The Durable Boundary Between Local Writes And Synchronization

## Plain Language For Founder

We need to decide whether synchronization should keep inferring changes after local
saves or whether domain actions should become explicit. The answer should prevent a
prematurely complex rewrite while removing correctness risks that will worsen later.

## Primary Question

Given the repository’s actual local-write, retry, deletion, ordering, and conflict
paths, what is the smallest durable boundary between persistence and synchronization?
Should the system retain snapshot-derived operations, introduce explicit domain
operations, or use a different model?

## Repository Starting Points

- `src/persistence/` — local writes and transaction ownership.
- `src/sync/` — queueing, retry, ordering, and conflict behavior.
- `tests/sync/` — currently asserted invariants and missing failure coverage.
- `docs/offline-behavior.md` — intended offline contract; verify it against code.

These are leads, not scope boundaries. Trace callers, schema migrations, background
workers, deletion behavior, and downstream API assumptions where relevant.

## Known Facts, Hypotheses, And Context Outside The Repository

- Fact: offline use is a hard product requirement.
- Hypothesis: deriving operations from final snapshots is losing intent needed for
  reliable ordering and conflict handling; verify this against the implementation.
- Preference: avoid collaboration-grade machinery before multi-user editing exists.

## Constraints And Evaluation Criteria

- Existing local data must migrate without loss.
- Normal editing must remain responsive.
- Correctness and understandable ownership matter more than minimizing the first diff.
- Complexity must be justified by current or credibly near-term requirements.

## Decision Authority

- Offline-first behavior is settled product direction.
- The agent should recommend the strongest synchronization architecture.
- Any option that changes visible offline behavior must return to the founder for a product decision.
- Every recommendation is advice only; implementation requires a later explicit follow-up.

## Research Contract

Inspect the implementation, tests, migrations, configuration, and relevant history.
Distinguish demonstrated behavior from inference. Challenge the three options if the
repository supports a better design. Research only; do not modify files.

## Requested Outcome

Recommend one final architecture. Explain the evidence, rejected alternatives, module
and data ownership, migration path, failure modes, tests, and any uncertainty that
requires runtime proof.
```

## 9. Failure Modes

Reject or revise a brief that:

- Replaces repository inspection with a large second-hand summary.
- Lists files as if they prove the writer’s hypothesis.
- Asks for broad improvement without naming a decision.
- Embeds the desired conclusion in the question.
- Confuses preferences with non-negotiable constraints.
- Treats explicit product direction as merely another assumption to challenge.
- Uses technical authority to smuggle in an unapproved product decision.
- Gives weak technical advice because product authority was mistaken for a ban on technical judgment.
- Requests every possible deliverable regardless of relevance.
- Demands certainty unsupported by available evidence.
- Requires plain text so rigidly that useful citations or artifacts become impossible.
- Silently authorizes code changes, external writes, or task launches.
- Treats a request for critique, a severe finding, or its own implementation plan as permission to begin follow-through.
- Bundles research and remediation so the user cannot review and accept the advice first.
- Uses a portable prompt when the destination can inspect the repository.
- Pretends a portable prompt is complete when key evidence remains inaccessible.

The final brief should make deep investigation easier without pre-performing it, and should create the conditions for a clear, evidence-backed decision.
