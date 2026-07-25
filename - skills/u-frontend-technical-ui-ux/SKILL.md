---
name: u-frontend-technical-ui-ux
description: Technical UI/UX execution and review contract for web and application interfaces where user-visible behavior, accessibility, responsive or adaptive mechanics, state completeness, performance, privacy, trust, sensitive flows, or interaction verification materially matter. Use when planning, building, diagnosing, fixing, reviewing, or refactoring frontend flows, forms, dashboards, editors, settings, authentication, checkout, onboarding, data-heavy surfaces, or cross-platform UI behavior, and whenever visual UI work creates or changes frontend code. Pair $u-frontend-aesthetic-art-director for visual direction and use $u-coding-doctrine when code is created or changed. Do not use for purely aesthetic direction or critique without implementation, backend-only work, or brand/content advice with no interface code or behavior.
---

# Frontend Technical UI/UX

## Mission And Authority

Turn product intent into interfaces that remain understandable, operable, recoverable, and trustworthy under real conditions. Treat UI as behavior under stress, not a screenshot: loading, failure, stale data, keyboard and touch input, zoom, narrow space, localization, permissions, payment, cancellation, destructive actions, interrupted sessions, and tired users all count.

Own the technical interaction contract:

- information architecture and task flow;
- semantics, accessibility behavior, keyboard and focus mechanics;
- state completeness, persistence, recovery, and feedback;
- responsive and adaptive behavior across input modes and viewports;
- frontend performance and technical motion constraints;
- privacy, trust, and legally sensitive UI defaults;
- rendered interaction verification and completion evidence.

Respect adjacent owners:

- When code is created or changed, load and follow `$u-coding-doctrine` for implementation architecture, domain boundaries, dependency choices, code quality, tests, migrations, deletion, and maintainability. This skill may require a frontend behavior; it must not invent a competing code doctrine.
- Pair `$u-frontend-aesthetic-art-director` when visual direction, composition, typography, color, imagery, product personality, motion feel, or perceived polish matters. That skill owns visible direction; this skill owns the behavior and technical floor that direction must preserve.
- Route backend authorization, rate limiting, idempotency, data retention, cryptography, and vulnerability decisions to the relevant backend or security work. Identify them as dependencies; do not imply that UI code proves them.
- Use current official platform guidance and relevant platform-specific skills for native implementation APIs, storefront policy, and operating-system conventions.

Never claim legal, accessibility, security, privacy, or platform compliance from this skill. Implement safer defaults within the authorized task, state the target and evidence, and flag unresolved obligations. A legal or policy trigger does not authorize unrelated product, backend, or business changes; request direction before materially expanding scope.

### Visual-Direction Stop

If the interface already works and the request is purely to make it more distinctive, premium, beautiful, branded, polished, or visually coherent, stop using this skill as the decision maker and route the work to `$u-frontend-aesthetic-art-director`, which in turn applies `$u-justins-taste`. Do not answer with a generic palette, typography recipe, card treatment, radius system, decorative motif, or motion personality merely because this skill was explicitly loaded. State only any technical constraints the visual direction must preserve when they are relevant to the request.

## Reference Routing

Read only the references implicated by the task:

- Read [accessibility-and-components.md](references/accessibility-and-components.md) for accessibility implementation or review, semantics, forms, authentication inputs, custom widgets, dialogs, focus, announcements, tables, search, filters, or component contracts.
- Read [responsive-performance-and-state.md](references/responsive-performance-and-state.md) for responsive or adaptive layouts, loading and async behavior, large data surfaces, interaction performance, Core Web Vitals, technical animation constraints, reduced motion, or degraded-network behavior.
- Read [trust-and-sensitive-flows.md](references/trust-and-sensitive-flows.md) for privacy, permissions, consent, tracking, payments, pricing, subscriptions, cancellation, destructive actions, authentication or account recovery, AI features, ads, marketplaces, user-generated content, minors, or other legally sensitive flows. Verify current official guidance before relying on a jurisdiction, date, threshold, or platform rule.
- Read [platform-patterns-and-verification.md](references/platform-patterns-and-verification.md) for native mobile, desktop, PWA, embedded surfaces, dashboards, editors, settings, onboarding, authentication, shared primitives or component-system integration, or a substantial implementation/review that needs the full verification matrix.

Do not load every reference by reflex. A local semantic fix may need only the accessibility reference; a subscription settings flow may need all four.

## Select The Work Mode

Choose the smallest mode that matches the request.

### Plan Or Design Behavior

Define the user task, flow, state model, component contracts, responsive transformations, risky consequences, recovery paths, and proof plan. Do not fabricate repository facts or implementation evidence.

### Implement

Inspect the existing system, make the smallest durable change that satisfies the interaction contract, and verify the real surface. Preserve approved patterns unless evidence justifies changing them.

### Review Or Diagnose

Inspect the implementation and rendered behavior, then lead with concrete defects and consequences. A review request does not authorize fixes. Distinguish observed failures from plausible risks and missing evidence.

### Local Technical Fix

Repair the implicated behavior without turning a focused task into a redesign, design-system project, or compliance program. Check the nearest shared primitive and sibling surfaces before making a one-off correction.

## Inspect Before Deciding

Establish what is real before prescribing a pattern:

- the user's requested outcome, authorized scope, and settled product decisions;
- the primary user, task, frequency, stakes, and consequence of failure;
- what must be understood before action and what safe escape or recovery exists;
- the framework, routing, rendering model, component library, tokens, form strategy, accessibility utilities, tests, build scripts, and CI already present;
- the nearest successful components and flows, including how they handle focus, errors, pending work, permissions, and narrow layouts;
- the actual surface at relevant viewports and input modes, with realistic or hostile content;
- relevant platform, procurement, contractual, privacy, payment, or distribution constraints;
- which dependencies belong outside the frontend and whether they already exist.

When evidence is unavailable, keep recommendations relative and name the gap. Do not disguise an assumed viewport, state, API guarantee, legal duty, or test result as observed fact.

## Select Risks And States

Do not dump every possible state into every screen. Select the states implied by the task, component, data source, platform, and consequence.

Consider:

- **Interaction:** default, hover where a pointer exists, focus, pressed, selected, expanded, disabled or otherwise unavailable.
- **Work:** dirty, saving, saved, conflicting, queued, processing, interrupted, canceled.
- **Data:** loading, partial, empty, stale, refreshing, malformed, very large, failed.
- **Network:** slow, offline, retrying, timed out, duplicate response.
- **Identity and permission:** signed out, expired session, insufficient permission, revoked access, step-up authentication.
- **Outcome:** success, recoverable error, permanent failure, undo available, rollback failed.
- **Content:** long labels, translation expansion, large text, missing media, dense data, unusual aspect ratios.
- **Risk:** destructive, billable, public, privacy-sensitive, irreversible, or safety-relevant.

Critical flows require stronger coverage than cosmetic controls. Every selected state needs a clear entry condition, visible result, assistive-technology communication where necessary, allowed actions, and recovery or next step.

## Core Technical Contract

### Task And Flow

- Make the primary task, current context, consequential status, and next action understandable.
- Structure navigation around the user's mental model rather than internal services or database tables.
- Keep active location and scope clear. Do not hide essential navigation or actions behind hover, a command palette, or unexplained iconography.
- Put information needed for a decision before the action. Put material price, renewal, privacy, or destructive consequences next to the decision rather than behind optional disclosure.
- Use stable, concrete labels. Keep critical-flow and error copy calm, actionable, and non-blaming; do not use cute or joking language where money, privacy, security, loss, or safety is involved.
- Preserve safe escape and recovery: cancel, retry, undo, review, edit, export, support, or an honest terminal explanation as appropriate.

### Semantics And Accessibility

- Target WCAG 2.2 Level AA for web content by default unless a stricter or different contractual target controls. Treat the target as an engineering baseline, not a compliance claim.
- Use native elements and platform controls first. Use ARIA or custom widgets only when the native platform cannot express the interaction and the complete behavior is implemented.
- Preserve meaningful landmarks, a clear and logical heading hierarchy, accessible names, reading order, and relationships. A single clear main heading is usually useful; do not manufacture a hidden `h1` merely to satisfy a fake absolute rule.
- Make the core task operable by keyboard or equivalent assistive input. Keep focus visible, unobscured, logical, and intentionally managed across temporary surfaces and route changes.
- Give forms persistent labels, useful instructions, associated errors, preserved non-sensitive input, and actionable recovery. Support paste, autofill, password managers, and translation unless a documented constraint truly prevents it.
- Preserve contrast, non-color cues, zoom, reflow, large text, target usability, forced-color behavior where relevant, and reduced-motion preferences.
- Treat automated accessibility checks as partial evidence. Manually exercise critical flows with keyboard and supported assistive technology.

Read the accessibility reference whenever implementation details or custom components matter.

### Components And Feedback

- Use buttons for actions and links for navigation or resource retrieval. Keep labels concrete and consequence-aware.
- Prevent duplicate actions while communicating progress. UI disabling alone is not server-side duplicate protection.
- Use dialogs for focused decisions. Associate their title, make modal backgrounds inert, manage initial and return focus according to the user's workflow, and provide an understandable exit or safe resolution.
- Keep transient feedback non-critical. Required information and errors must remain available long enough to understand and act on.
- For destructive actions, name the object, consequence, scope, reversibility, and safe alternative. Confirm only when consequence warrants interruption; do not normalize confirmation fatigue.

### State, Persistence, And Recovery

- Distinguish loading, empty, stale, refreshing, partial, and failed states. Never present a failed request as empty data.
- Give immediate feedback after action. For long work, show stage or meaningful progress rather than indefinite animation.
- Use optimistic updates only when failure is detectable and recovery is reliable. Keep stale content visible during refresh when that is safer than blanking the surface.
- Preserve work through validation failure, navigation, interruption, and session expiry when appropriate. Never persist passwords, one-time codes, CVV, raw card credentials, or other secrets for convenience.
- Make retry safe. Surface duplicate, conflict, and rollback outcomes rather than pretending success.

### Responsive And Adaptive Behavior

- Design for the task, content, input modes, and available space rather than a fixed list of devices.
- Keep DOM or accessibility order aligned with reading and focus order. Do not use visual rearrangement to create a contradictory interaction sequence.
- Avoid hover-only behavior. Provide equivalent touch, keyboard, switch, and assistive-input paths where the platform supports them.
- Change the interaction model when necessary: a dense table may become priority columns plus detail, and an editor may separate canvas from inspector. Do not merely crush a desktop surface into a narrow column.
- Test the relevant extremes, including narrow space, zoom or large text, long content, touch, and resizable or split-screen contexts when applicable.

### Performance And Technical Motion

- Treat responsiveness, stable layout, and fast useful rendering as trust properties.
- Protect input immediacy, avoid unnecessary work in interaction handlers, reserve space for late content, and choose rendering or loading strategies that fit the actual stack.
- Measure material claims. For web work, use current Core Web Vitals definitions and field data when available; do not present a lab run as population evidence.
- Let the aesthetic skill own motion feel. Own only technical constraints: causality, interruptibility, focus, inertness, performance-safe implementation, and reduced-motion behavior.
- Remove, reduce, or replace nonessential spatial motion for reduced-motion users. Do not install a global `0.01ms !important` reset that can damage component logic; give affected components deliberate reduced paths.

### Privacy, Trust, And Sensitive Actions

- Ask for sensitive permissions in context, explain the benefit and consequence, and provide a later way to revoke or change the choice.
- Make public, private, shared, billable, and destructive states explicit before action.
- Default user content to private unless the product's purpose or an approved existing policy genuinely requires sharing; when public-by-default is essential, make that state unmistakable before creation or publication.
- Minimize collection and avoid leaking sensitive data through URLs, client logs, analytics, screenshots, previews, or error messages.
- Use plain choices without confirmshaming, fake scarcity, disguised ads, hidden costs, punitive refusal paths, or cancellation mazes.
- Treat confirmation, warning, and disabled UI as communication—not authorization or security enforcement.
- Load the trust reference for any consent, payment, subscription, AI, marketplace, tracking, minor, or legally sensitive flow. Verify current official rules instead of relying on remembered dates or static summaries.

## Implementation Discipline

- Reuse the repository's established component, token, form, validation, state, and test systems when they are adequate.
- Add or improve the smallest shared primitive that actually reduces drift. Do not create a parallel design system, exhaustive component catalog, or new token scale for a local task.
- Keep visual values native to the existing system and approved art direction. Do not impose universal fonts, radii, spacing, easing, or animation timing from this skill.
- Keep behavior explicit at boundaries: pending versus complete, local versus server truth, allowed versus unauthorized, reversible versus permanent.
- Identify backend or policy dependencies separately and verify their contract. Do not conceal missing authorization, idempotency, retention, billing, or audit behavior behind polished frontend states.
- Follow the repository's established quality gates and `$u-coding-doctrine`. Prefer deletion and simplification when they preserve behavior and reduce duplicate systems.

For a solo developer or tiny team with no adequate existing system, establish only the smallest coherent spine the current product needs: semantic tokens, a compact set of real primitives and layout helpers, one form and validation strategy, one state/request approach, and progressive enhancement where practical. Do not prebuild an exhaustive design system or copy this sentence into a component catalog.

## Verification Contract

Scale proof to consequence and changed behavior. Material interaction, layout, responsive, state, or visual-code changes require inspection of the real rendered surface. For a narrowly scoped semantic or internal fix, component-level rendered evidence may be proportionate when route setup would add no meaningful proof. Planning-only work does not require fabricated implementation evidence. State any unavailable environment or limitation.

For affected behavior, use the strongest applicable combination of:

- type, lint, build, unit, component, integration, and end-to-end checks already supported by the repository;
- happy path plus meaningful failure, denial, cancellation, retry, or interruption paths for critical flows;
- keyboard-only operation, focus order and visibility, zoom or large text, reduced motion, and supported screen-reader smoke testing;
- relevant narrow, wide, touch, resizable, split-screen, or orientation contexts;
- slow network, offline, expired session, stale data, hostile content, duplicate submission, and data-loss recovery where implicated;
- performance measurement for materially changed critical surfaces.

Inspect the actual route and state, not merely a component in isolation, when surrounding layout, navigation, focus, permissions, or data flow affects the result. Record what was tested, what passed, what could not be tested, and what remains uncertain. Never invent evidence.

Read the verification reference for a substantial implementation or release-facing review.

## Completion Gate

Do not call the task complete until, where relevant:

- the primary user task and safe recovery path work;
- the selected state model is implemented without false empty or success states;
- semantics, accessible names, keyboard behavior, focus, forms, and announcements are correct;
- the layout survives implicated content, viewport, zoom, text, and input conditions;
- sensitive consequences are clear and safer defaults remain within authorized scope;
- frontend and backend responsibilities are not confused;
- performance and reduced-motion behavior are acceptable for the changed surface;
- rendered behavior has been inspected at the level proportionate to the implemented change;
- applicable checks have passed, or unavailable proof and residual risk are explicit;
- the implementation fits the existing system and `$u-coding-doctrine`.

## Report The Work

Keep the handoff concise and evidence-based. State:

1. the user-visible behavior changed or assessed;
2. the important state, accessibility, responsive, performance, or sensitive-flow decisions;
3. verification actually performed and its result;
4. unresolved dependencies, unavailable evidence, and residual risk.

Do not expose the internal checklist merely to prove that the skill was followed. Do not drown the user in compliance theater.

## Versioning

Update this version whenever the skill or its bundled resources change:

- Major (`2.0.0`): incompatible workflow or contract changes.
- Minor (`1.1.0`): backward-compatible capabilities or material instruction changes.
- Patch (`1.0.1`): fixes, clarifications, or small refinements.

Version: 1.0.0
