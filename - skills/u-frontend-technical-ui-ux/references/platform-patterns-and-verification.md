# Platform, Product Patterns, And Verification

Use this reference for native mobile, desktop, PWA, embedded interfaces, recurring product surfaces, or substantial implementation and review work that needs complete proof.

## Contents

- Platform Adaptation Rule
- Web And PWA Surfaces
- Native Mobile Surfaces
- Desktop And Resizable Surfaces
- Existing Systems And Primitives
- Product-Surface Stress Patterns
- Verification Strategy
- Automated Evidence
- Rendered And Manual Evidence
- Completion Evidence

## Platform Adaptation Rule

Apply the cross-platform outcome without pretending that web markup is a native implementation API.

For every platform, preserve:

- meaningful structure, names, roles, values, state, grouping, and order;
- keyboard, touch, pointer, switch, remote, stylus, voice, or other supported input behavior;
- clear focus or selection and predictable back, close, cancel, and escape behavior;
- text scaling, contrast, reduced motion, safe areas, orientation, resizing, and system appearance preferences;
- permissions requested in context and manageable later;
- loading, interruption, offline, restoration, and destructive-action recovery;
- responsive input and stable content;
- platform-conventional navigation and system integration where it improves understanding.

Before implementing native or distribution-specific behavior, use the relevant platform skill and current official documentation. Platform conventions, API capabilities, privacy declarations, storefront billing, and review rules change. This reference supplies the interaction contract, not a substitute SDK guide.

## Web And PWA Surfaces

- Preserve semantic HTML and progressive enhancement where practical.
- Keep URL, history, title, route focus, refresh, deep-link, and back/forward behavior coherent.
- Treat installed, standalone, and offline contexts deliberately. Do not claim offline support because a service worker exists.
- Account for browser zoom, text resizing, translation, password managers, autofill, forced colors, reduced motion, touch, and keyboard.
- Use safe-area insets where installed or mobile contexts require them.
- Keep permission prompts and browser-controlled UI aligned with the in-product explanation.
- Verify caching, stale assets, update availability, failed installation, reconnect, and restored sessions when the PWA claims those capabilities.

## Native Mobile Surfaces

- Map structure and controls to the platform accessibility tree using native labels, traits or roles, values, hints, grouping, and traversal.
- Respect platform back behavior, swipe or gesture conventions, safe areas, system bars, keyboard insets, orientation, dynamic type or font scaling, and screen-reader navigation.
- Do not import a web modal, hover, tab, toast, or navigation pattern without checking its native equivalent and lifecycle.
- Request camera, microphone, photos, files, location, contacts, notifications, tracking, or health permissions only in context. Handle denial, restricted state, one-time access, later revocation, and operating-system settings.
- Preserve task and state through backgrounding, termination, interruption, deep links, handoff, and reconnection where the product promises it.
- Verify ordinary and reduced motion using platform settings, not only an in-app switch.
- Keep storefront privacy, subscription, entitlement, external-purchase, and account-deletion paths aligned with the current distribution contract.

## Desktop And Resizable Surfaces

- Support resizable windows, constrained minimum dimensions, large or multiple displays, system scaling, high contrast, reduced motion, and keyboard navigation appropriate to the platform.
- Preserve focus, command availability, selection, unsaved state, and window restoration across dialogs, auxiliary windows, minimize, sleep, and relaunch.
- Use menus, shortcuts, context menus, toolbars, drag and drop, file pickers, and system notifications according to platform expectations and with equivalent accessible paths.
- Keep destructive commands separated from routine navigation and make shortcuts discoverable.
- Test pointer precision assumptions with keyboard and assistive input. Do not make tiny targets acceptable merely because a mouse is likely.
- For embedded or kiosk surfaces, define the actual input, timeout, connectivity, privacy, escape, reset, and support constraints rather than inheriting desktop assumptions.

## Existing Systems And Primitives

Inspect before adding infrastructure:

- existing components, variants, slots, composition patterns, and accessibility contracts;
- design tokens and semantic aliases;
- form, validation, state, request, cache, routing, analytics, error, and internationalization strategies;
- component stories, visual tests, accessibility tests, E2E fixtures, and browser automation;
- nearest sibling flows and known exceptions.

Prefer one adequate shared contract over parallel local inventions. Improve a shared primitive when multiple real consumers need the same behavior; keep a local implementation when premature generalization would make the system harder.

Do not create an exhaustive primitive catalog from this skill. Do not impose fonts, spacing scales, radii, shadows, easing, or durations. Reuse approved values and let the aesthetic owner define visible relationships. Technical ownership covers semantic token wiring, state mapping, fallbacks, maintainable reuse, and proof.

Avoid:

- clickable generic containers replacing native controls;
- custom widgets without complete behavior;
- one-off spacing or z-index values that bypass the system without reason;
- global CSS resets that damage movable components;
- parallel form, toast, dialog, icon, token, or responsive systems;
- accessibility overlays as a substitute for accessible implementation;
- comments or abstractions that preserve obsolete intent rather than useful context.

Follow `$u-coding-doctrine` when changing architecture, shared systems, dependencies, or duplicated implementation.

## Product-Surface Stress Patterns

Use only the pattern implicated by the task.

### Dashboard Or Monitoring Surface

- Lead structurally with the question, decision, status, or action the user came to resolve.
- Expose time range, scope, freshness, source, and sync state where interpretation depends on them.
- Allow movement from summary to supporting evidence.
- Isolate regional loading and failure so one broken source does not falsify or blank the whole surface.
- Keep filters, drill-down, selection, and return context stable.
- Let the aesthetic skill decide visible hierarchy and chart treatment; keep semantics, interaction, state, and performance technical.

### Editor Or Builder

- Protect work continuously where feasible and show saved, saving, offline, conflicting, failed, and authoritative states honestly.
- Provide undo and redo according to a defined history contract.
- Warn before actual data loss, not every navigation event.
- Keep shortcuts discoverable and essential actions reachable without them.
- Preserve selection, canvas or object context, inspector relationship, and focus when layout adapts.
- Test large documents, missing assets, backgrounding, reconnect, conflicts, and failed publish or export.

### Admin Or Settings

- Group controls by user task and consequence rather than backend service names.
- Show current state, scope, inheritance, and consequence before a change.
- Keep account deletion, data export, privacy, security, subscription, and permission management findable when the product supports them.
- Separate dangerous operations from routine settings without hiding them.
- Identify authorization, audit, propagation delay, and rollback as backend dependencies.
- Test partial permissions and the difference between view, edit, manage, and owner roles.

### Onboarding

- Ask only what is needed to reach first value or meet a genuine prerequisite.
- Defer optional personalization and sensitive permissions until context exists.
- Let users skip nonessential steps and return later.
- Show progress only when sequence and remaining work are meaningful.
- Seed empty states with domain-realistic examples, import, or creation paths without pretending user data exists.
- Preserve progress through interruption, authentication, verification, and recoverable failure.

### Authentication

- Support password managers, autofill, paste, one-time-code retrieval, passkeys where appropriate, and accessible recovery.
- Preserve the destination and non-sensitive work through sign-in or reauthentication.
- Handle expired, revoked, challenged, locked, and insufficient-access states distinctly.
- Keep account-enumeration and rate-limiting behavior aligned with the threat model and backend contract.
- Test deep links, multi-factor interruption, lost factors, session timeout, and return focus.

### Checkout Or Subscription Management

Use the trust reference. Additionally verify route persistence, back behavior, processor return paths, challenged or delayed payment, duplicate action protection, entitlement refresh, and confirmation state at the relevant supported layout boundaries.

## Verification Strategy

Choose proof from risk and changed behavior. A green build proves compilation, not usability. A polished screenshot proves appearance, not interaction. An automated accessibility scan proves only the rules it can detect.

Establish before testing:

- changed user task and affected routes;
- supported platforms, browsers, devices, assistive technologies, and input modes;
- selected states and content extremes;
- existing baseline and regression risks;
- available fixtures, accounts, permissions, network controls, and observability;
- evidence that can and cannot be obtained locally.

Use the narrowest environment that can prove the behavior, then inspect the integrated route when surrounding layout, focus, data, auth, or navigation matters.

## Automated Evidence

Run the repository-supported subset relevant to the change:

- type checking, lint, formatting, and build;
- unit tests for state transitions, validation, transformation, and recovery logic;
- component tests for names, roles, keyboard behavior, focus, announcements, and variants;
- integration tests for requests, cache, permissions, optimistic behavior, conflict, and retries;
- end-to-end tests for critical happy paths plus at least one meaningful failure, denial, cancellation, or interruption path;
- automated accessibility checks at component and routed-page level;
- visual regression where it is established and the changed state is represented;
- bundle, rendering, or performance checks for material critical-surface changes.

Do not create brittle snapshots or duplicate the framework's behavior merely to increase test count. Test product contracts and regressions.

## Rendered And Manual Evidence

For implemented user-facing behavior, inspect the actual rendered surface. Select applicable checks:

### Task And State

- complete the primary task and safe escape;
- exercise loading, empty, stale, partial, error, success, canceled, offline, timeout, retry, conflict, and permission states that the risk model selected;
- submit rapidly or repeatedly to test duplicate protection;
- interrupt navigation, refresh, background, or session where work persistence matters;
- verify server truth after optimistic or delayed outcomes.

### Accessibility And Input

- keyboard-only completion, visible and unobscured focus, logical order, and return focus;
- supported screen-reader smoke test through critical flow and dynamic updates;
- touch target and software-keyboard behavior;
- zoom, large text, narrow reflow, translation expansion, forced colors, and reduced motion where applicable;
- pointer, keyboard, touch, and platform back or escape parity.

### Responsive And Content

- actual layout transformation boundaries rather than arbitrary screenshots;
- narrow, wide, resizable, split-screen, orientation, and safe-area contexts implicated by the platform;
- long labels, dense data, large values, missing media, unusual ratios, user-generated content, and empty regions;
- sticky regions, scroll restoration, selection, overflow, and on-screen keyboard obstruction.

### Performance And Resilience

- slow or failed network, stale cache, offline and reconnect behavior;
- input responsiveness, long tasks, large lists, image and font loading, and layout stability;
- ordinary and reduced-motion paths under rapid input;
- before-and-after measurement when claiming improvement.

### Sensitive Flows

- disclosure and material terms before action;
- refusal, withdrawal, cancellation, permission denial, step-up authentication, and support paths;
- delayed, challenged, duplicate, partially completed, reversed, or failed billing and destructive outcomes;
- confirmation, receipt, access, export, deletion, audit, and redaction behavior.

## Completion Evidence

Report evidence by outcome, not tool theater:

- the exact behavior and routes exercised;
- checks run and their results;
- viewports, input modes, accessibility environments, and states inspected;
- performance evidence and whether it is lab or field data;
- unavailable environments or tests;
- backend, security, policy, and platform dependencies;
- residual risk and a concrete next proof step.

If rendering or interaction testing was genuinely unavailable, say so and do not call those surfaces verified. If the aesthetic skill is active, its rendered critique gate is additional; technical verification does not claim visual-direction quality.
