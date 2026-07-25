---
name: u-gpt-pro-research
description: Prepare high-leverage research and advice briefs for GPT Pro or another capable Codex task working on a software project. Use only when the user asks to draft, review, or improve a GPT Pro/external-model research request, or explicitly invokes $u-gpt-pro-research. Default to a repository-aware brief that directs the answering agent to inspect the available codebase; create a self-contained portable prompt only when the user requests one or the destination cannot access the repository. Never self-select, recommend, launch, or send the research merely because a task is difficult or a second opinion could help.
---

# GPT Pro Research

## Authorization Boundary

Use this skill only when the user requests a GPT Pro or external-model research brief, question, or prompt. Natural-language intent is sufficient; the user does not need to know the skill name.

Do not decide that a difficult, uncertain, high-stakes, or research-heavy task should be handed to another model. Do not recommend this workflow on your own.

Preparing a brief does not authorize launching a task, contacting another model, or modifying the repository. Do only the action the user requested:

- If asked to draft, return a draft.
- If asked to save, save it where authorized.
- If asked to launch or send it, do so only through an available authorized workflow.
- If asked to audit or edit this skill, do not run the research workflow itself.

## Objective

Turn a messy uncertainty into a focused investigation that could materially improve a decision. Optimize for the quality and leverage of the question, not the amount of context copied into it.

By default, assume the answering agent can inspect the current repository or workspace. Give it a reliable starting map, the non-repository context it cannot discover, and a demanding research contract. Do not attempt to summarize the entire codebase for it.

## Preserve Founder And Product Authority

Treat the user's explicitly stated product direction as controlling. The user has the final word on user-facing product design, behavior, scope, priorities, tone, taste, and what the product is meant to be.

Research may identify consequences, risks, tensions, or non-binding alternatives. It must not silently override, reinterpret, dilute, or supersede explicit product direction. Do not disguise a product preference as a technical necessity.

Use this authority model:

- **Product and user-facing decisions:** preserve the user's direction. Offer alternatives only as clearly labeled, non-binding advice unless the user explicitly asks for open-ended product critique or exploration.
- **Technical decisions delegated by the user:** investigate rigorously and recommend the strongest technical approach, including a decisive preferred option. This is where the research agent's expert judgment should carry the most weight.
- **Cross-boundary conflicts:** when a real technical constraint would materially change the user-facing product, explain the evidence, consequences, and feasible options. Do not choose the product tradeoff on the user's behalf; return that decision to the user.

Challenging assumptions never grants authority to replace explicit product direction. Challenge technical premises freely; challenge product direction only when the user explicitly requests that critique. Otherwise, surface material risks respectfully and continue within the stated direction wherever feasible.

## Keep Advice Inert Until Explicit Follow-Up

A request for research, review, critique, comparison, or recommendations grants permission to analyze and advise only. It is never permission to act on the resulting advice.

Treat every finding, criticism, recommendation, proposed plan, and suggested fix as non-binding and operationally inert until the user deliberately accepts a specific item in a later follow-up and explicitly authorizes the corresponding action. Do not infer acceptance from enthusiasm, silence, the strength of the evidence, the severity of a finding, or the fact that the agent believes an action is obviously correct.

The research agent may explain implementation implications or propose a sequence, but it must not modify files, start remediation, create tasks or tickets, contact external systems, change plans, or otherwise convert its own output into work. Open-ended permission to critique expands what may be examined; it does not expand action authority.

If the user later authorizes follow-through, act only on the accepted recommendation and scope named in that follow-up. Unaccepted advice remains irrelevant to execution.

## Choose the Delivery Mode

### Repository-aware mode — default

Use when the destination can inspect the relevant workspace. Point to paths, symbols, tests, documentation, configuration, history, logs, screenshots, or other evidence rather than reproducing them.

Treat listed files as starting points, not scope boundaries. Explicitly tell the answering agent to follow the evidence into other parts of the repository when necessary.

### Portable mode — explicit fallback

Use only when the user requests a self-contained prompt or the destination truly cannot access the repository. Include the minimum excerpts and summaries necessary to reason accurately. If the problem cannot be represented faithfully without repository access, say so rather than manufacturing false completeness.

See [references/gpt-pro-research-guide.md](references/gpt-pro-research-guide.md) when you need the extended templates, mode-specific guidance, or examples.

## Core Standard

Make each brief:

- **Decision-led:** connect the investigation to a consequential choice, diagnosis, or next move.
- **High-leverage:** ask the question whose answer would most reduce important uncertainty or prevent expensive mistakes.
- **Repository-grounded:** identify promising evidence and require direct inspection before conclusions.
- **Context-efficient:** append what the repository cannot reveal; point to what it can.
- **Critical within authority:** challenge technical premises, implementation, and stated options without treating explicit product direction as disposable.
- **Evidence-seeking:** require facts, inferences, and recommendations to remain distinguishable.
- **Conclusive:** request a preferred direction and its implications, not an unranked menu.
- **Practical:** request risks, edge cases, validation, and implementation consequences when relevant.
- **Final-quality:** optimize for a durable, polished solution rather than a convenient patch.
- **Founder-skimmable:** make the question and supported decision understandable immediately.

## Workflow

### 1. Understand the intended research outcome

Identify:

- What decision, diagnosis, or design uncertainty the answer should resolve.
- Why it matters now.
- What would change depending on the answer.
- Whether the target should only research or also propose a non-binding plan. The target never performs implementation; that requires a later explicit follow-up after the user reviews the advice.
- Which product decisions are already settled by the user, which advice is non-binding, and which technical decisions the user is delegating to expert judgment.

Do not turn a vague topic into a broad “review everything” prompt. Find the consequential question inside it.

### 2. Inspect enough to frame the question

Inspect the workspace sufficiently to avoid a generic or misdirected brief. Locate likely entry points, existing documentation, important tests, relevant configuration, recent changes, and obvious neighboring systems.

Stop before duplicating the full research assignment. The drafting agent should establish the map and expose uncertainty; the answering agent should perform the deeper investigation independently.

### 3. Separate discoverable and non-discoverable context

Point to repository evidence instead of pasting it. Append only context the answering agent otherwise lacks, such as:

- User intent and decision stakes.
- Explicit product direction and user-facing decisions, preserved as controlling instructions rather than demoted to preferences.
- Product, business, legal, operational, or taste constraints.
- Relevant conversation history.
- Reasons earlier approaches were rejected.
- Known production behavior or evidence not stored in the repository.
- The authoritative branch, worktree, diff, or uncommitted state when it matters.
- Hard constraints and challengeable preferences.

Label uncertain claims and hypotheses. Do not convert guesses into facts while compressing context.

### 4. Write one primary question

Prefer one strong primary question. Add subordinate questions only when they are necessary to answer it.

A strong question:

- Names the decision or uncertainty.
- Leaves room to reject the current framing.
- Supplies evaluation criteria without dictating the answer.
- Is bounded enough to investigate deeply.
- Demands a recommendation supported by evidence.

Avoid yes/no validation, generic best-practice requests, preselected solutions disguised as questions, and sprawling audits with no decision target.

### 5. Build the brief

Use only the sections that add value. A strong default structure is:

```markdown
# [Focused research title]

## Plain Language For Founder

[In 1-3 short sentences: what we need to learn and what decision it supports.]

## Primary Question

[The single high-leverage question.]

## Why This Matters

[The stakes, blocked decision, or costly uncertainty.]

## Repository Starting Points

- `[path or symbol]` — [why it may matter]

These are starting points, not assumed scope boundaries. Follow the evidence into
other code, tests, configuration, documentation, and history where necessary.

## Known Facts, Hypotheses, And Context Outside The Repository

[Only information that materially changes the investigation. Clearly label hypotheses.]

## Constraints And Evaluation Criteria

[Controlling product direction and hard constraints first; challengeable preferences second.]

## Decision Authority

[State what the user has already decided, what advice is non-binding, what technical
judgment is delegated, which cross-boundary tradeoffs must return to the user, and
that no recommendation authorizes follow-through without a later explicit request.]

## Research Contract

[How evidence should be gathered, what assumptions should be challenged, and what
the answer must distinguish or verify.]

## Requested Outcome

[The recommendation, analysis, plan, risks, or other deliverable actually needed.]
```

Omit empty or ceremonial sections. Add task-specific sections when they clarify the investigation.

### 6. Set the evidence and answer standard

When relevant, instruct the answering agent to:

- Inspect implementation, call paths, data flow, tests, configuration, documentation, and history before concluding.
- Search beyond the supplied starting points.
- Use current primary sources for external facts or changing technology claims.
- Cite concrete repository or source evidence closely enough to verify important claims.
- Separate observed facts, reasoned inferences, and recommendations.
- Identify contradictions between code, tests, documentation, and intended behavior.
- Challenge flawed assumptions and consider realistic alternatives.
- Preserve explicit product direction and clearly label product alternatives as non-binding unless open-ended critique was requested.
- Keep all findings and recommendations operationally inert until the user explicitly accepts and authorizes a later follow-up.
- Clearly recommend the best final direction and explain tradeoffs.
- State material uncertainty and the evidence needed to resolve it.
- Include implementation implications, risks, edge cases, and validation where useful.

Do not mechanically request every item. Tailor the contract to the research question.

### 7. Tighten before returning

Remove generic project summaries, copied code the destination can inspect, exhaustive file inventories, repeated quality slogans, and response-format bureaucracy.

Return the brief inline unless the user requested a saved document. When saving, preserve any user-specified naming or numbering convention. Do not invent a numeric filing scheme.

## Task-Specific Emphasis

- **Research or dependency choice:** define the decision, evaluation criteria, realistic candidates, current-version evidence, and implementation consequences.
- **Architecture:** identify current boundaries and pain points, then request repository-grounded alternatives, migration implications, and a final recommendation.
- **Debugging:** provide symptoms and inaccessible runtime evidence; point to likely flows and require verification of root cause before proposing a fix.
- **Code review:** define purpose and invariants; identify the relevant change or subsystem and require evidence beyond the obvious diff when necessary.
- **UX or product:** treat explicit user-facing direction as controlling; include user intent, product constraints, and inaccessible research; direct inspection of existing UI, states, tests, and design-system evidence. Offer product alternatives as non-binding unless the user requested open-ended critique.
- **Implementation planning:** define current and target states, operational constraints, migration or compatibility risks, verification, and what “done” means.

## Final Check

Before returning the brief, verify:

- The user actually requested this workflow.
- The delivery mode matches the destination’s real capabilities.
- The brief centers one consequential question and supported decision.
- Repository context is linked or pointed to rather than needlessly copied.
- Non-repository context and hard constraints are present.
- Starting points are not presented as complete scope.
- Facts, hypotheses, and preferences are distinguishable.
- Settled product direction, non-binding advice, delegated technical judgment, and cross-boundary decisions are distinguishable.
- The brief states that critique and recommendations do not authorize implementation or any other follow-through.
- The research contract demands evidence without becoming a generic checklist.
- The requested outcome is concrete and appropriately authorized.
- The answering agent can challenge the premise and still give a clear recommendation.

## Versioning

Update this version whenever the skill or its bundled resources change:

- Major (`2.0.0`): incompatible workflow or contract changes.
- Minor (`1.1.0`): backward-compatible capabilities or material instruction changes.
- Patch (`1.0.1`): fixes, clarifications, or small refinements.

Version: 1.0.0
