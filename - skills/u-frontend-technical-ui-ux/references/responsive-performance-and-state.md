# Responsive, Performance, And State Engineering

Use this reference when layout adaptation, asynchronous work, data volume, rendering cost, interaction responsiveness, animation implementation, or degraded conditions materially affect the task.

## Contents

- Adaptive Layout Contract
- Surface Transformations
- State And Asynchronous Work
- Rendering And Delivery
- Interaction Performance
- Web Performance Evidence
- Technical Motion And Reduced Motion
- Targeted Verification

## Adaptive Layout Contract

Design around content, tasks, input modes, and available space rather than a ceremonial device list.

- Identify the task that must remain possible, the information that must remain visible, and the actions that must remain reachable at each relevant size.
- Prefer intrinsic sizing, fluid layout, logical properties, container-aware components, and content-led breakpoints over device-name breakpoints.
- Preserve meaningful order across visual layout, DOM or accessibility structure, keyboard focus, and screen-reader traversal.
- Account for pointer, touch, keyboard, switch, stylus, large text, zoom, orientation, split screen, safe areas, software keyboards, and resizable windows when the platform and task implicate them.
- Avoid hover-only disclosure or actions. Hover may enrich a pointer experience but must not carry the only path.
- Keep destructive, primary, and escape actions reachable without accidental activation. Do not let sticky controls obscure focused content or validation messages.
- Test real content variation: long labels, translated copy, missing or extreme media, large values, dense tables, empty regions, and user-generated content.
- Preserve user orientation when navigation collapses or content changes form. A compact layout is not allowed to erase scope, current location, or selection.

Do not require every task to test every named viewport. Select representative widths and constraints from the actual layout boundaries, supported devices, and failure risk.

## Surface Transformations

Treat these as options, not mandatory recipes.

### Navigation And App Shells

- Separate global navigation, object or workspace navigation, and page-level actions conceptually and semantically.
- When a sidebar collapses, choose a drawer, compact rail, bottom navigation, or search/command entry according to task frequency and platform convention.
- Preserve active location, scroll position, selection, and return context where users move repeatedly between list and detail.
- Use breadcrumbs for meaningful deep hierarchy, steppers only when sequence genuinely matters, and recent or saved views when they reduce repeated navigation in dense products.
- Move low-frequency toolbar actions into overflow before hiding or displacing the primary action.
- Keep destructive actions out of routine navigation and away from accidental touch zones.

### Marketing And Content Pages

- Preserve a clear reading order, usable line lengths, media meaning, and reachable primary action as columns collapse.
- Use a single-column reading flow in narrow space unless another structure demonstrably improves comprehension; add multiple columns only when they improve scanning rather than merely filling width.
- Coordinate crop, hierarchy, and composition with the aesthetic owner while keeping the responsive mechanics and content order robust.

### Tables And Dense Data

- Keep the comparison task intact. Choose priority columns, deliberate horizontal scrolling, a summary-plus-detail view, or a different small-screen interaction based on what users compare.
- Do not convert a real table to cards merely because the viewport is narrow; cards can destroy row and column comparison.
- Keep headers, key identity, row actions, selection, and status discoverable.
- Test sticky columns and headers with zoom, focus, scroll containers, and screen readers.

### Forms And Settings

- Stack fields when space demands it, but preserve grouping, label relationships, review context, and error navigation.
- Keep explanatory text close to the decision it qualifies. Do not move a material consequence into a distant accordion on small screens.
- Ensure on-screen keyboards do not cover focused fields, errors, or submit and escape actions.

### Editors And Builders

- Preserve the primary object or canvas and the user's sense of what is being edited.
- Separate inspector, layers, assets, preview, or secondary tools according to available space without losing their relationship to the object.
- Support keyboard shortcuts and expose them in a discoverable place. Provide non-shortcut access to essential commands.
- Protect unsaved work across pane changes, navigation, reconnection, and viewport transformation.

## State And Asynchronous Work

Model asynchronous behavior explicitly rather than treating “loading” as one boolean.

For each material operation, establish:

- initiating action and whether repetition is safe;
- local pending state and authoritative server state;
- existing content that remains usable during refresh;
- cancellation or interruption behavior;
- timeout, retry, duplicate, conflict, and partial-success behavior;
- final success evidence;
- recoverable versus terminal failure;
- rollback or undo contract;
- focus and assistive-technology communication.

Use these principles:

- Give immediate acknowledgement after action without declaring success before the source of truth confirms it.
- Distinguish initial loading, background refresh, pagination, processing, empty data, stale data, partial data, and failure.
- Keep stale or partial content visible when it remains safer and more useful than a blank screen. Mark freshness and refresh status honestly.
- Preserve layout stability where possible, but do not use skeletons when their false structure misleads or adds distracting motion.
- Show meaningful stage or progress for long operations. Do not use an indefinite spinner to hide unknown or failed work.
- Retry automatically only when the action is safe and the retry policy is bounded. Explain or expose manual recovery when user intent could be duplicated.
- Use optimistic UI only when failure is detectable, correction is understandable, and rollback is reliable.
- Do not discard entered work on validation, network, payment, permission, or server failure. Exclude secrets and high-risk credentials from persistence.
- Surface conflict and merge decisions instead of silently overwriting newer data.
- For destructive or billable operations, require authoritative confirmation or a genuinely reliable undo contract. Treat idempotency as a backend dependency, not a disabled-button feature.

## Rendering And Delivery

Choose techniques from the actual framework, product, and measurement.

- Prioritize the first useful content and primary task rather than optimizing a decorative shell.
- Avoid hiding critical UI behind unnecessary client-side bundles or sequential requests.
- Use server rendering, static rendering, streaming, progressive enhancement, partial hydration, or client rendering only where each fits the stack and interaction.
- Reserve dimensions or aspect ratios for late media and embedded content to reduce layout shift.
- Use responsive image sources, suitable compression and formats, lazy loading, and fetch priority according to whether an asset is critical or deferred.
- Avoid lazy-loading likely largest-contentful-paint media or other immediately needed content.
- Load fonts without blocking the task. Use appropriate subsets, fallbacks, and metric compatibility where font swaps would destabilize layout.
- Keep placeholders dimensionally related to final content when a placeholder is useful.
- Split or defer expensive editors, charts, maps, media, and secondary panels when doing so improves the real route rather than a synthetic score.
- Preserve server-rendered semantics and usable fallback behavior when JavaScript is slow or fails where progressive enhancement is practical.

## Interaction Performance

- Keep typing, pointer tracking, dragging, scrolling, and direct manipulation immediate.
- Avoid expensive synchronous work inside input handlers. Move computation, rendering, or network work out of the critical interaction path where possible.
- Debounce or throttle network and derived work without delaying the local input response.
- Prevent avoidable rerenders and unnecessary large-tree updates using the patterns native to the existing framework.
- Virtualize large collections only after measuring need, and preserve keyboard, focus, accessible counts, restoration, and find-in-page expectations.
- Avoid layout thrashing. Batch reads and writes or use framework/platform scheduling mechanisms appropriately.
- Prefer compositor-friendly transform and opacity animation when they express the required motion. Measure layout animation rather than banning it categorically.
- Consider low-power, thermal, memory, and constrained-device behavior for repeated or media-heavy interactions.
- Do not add a large animation or interaction dependency for a small effect without a measured and maintainable reason.

## Web Performance Evidence

Use current official definitions when a task depends on Web Vitals; the metric set and guidance can evolve.

Use the official [web.dev Web Vitals guidance](https://web.dev/articles/vitals) as a technical starting point and verify the current metric definitions before making a release or population claim.

At the time of this revision, common “good” Core Web Vitals thresholds are:

- Largest Contentful Paint at or below 2.5 seconds;
- Interaction to Next Paint at or below 200 milliseconds;
- Cumulative Layout Shift at or below 0.1.

Evaluate population claims at the 75th percentile and segment mobile and desktop where field tooling does so. Treat field data as user evidence and lab tools as reproducible diagnostics; neither replaces the other.

Do not turn the numbers into vanity gates:

- identify the affected route, population, device class, and observation window;
- distinguish cold navigation, warm navigation, cached data, and authenticated application behavior;
- preserve task correctness and accessibility while optimizing;
- compare before and after when claiming improvement or non-regression;
- state when only lab evidence or no production field data is available.

For native or desktop surfaces, apply the same product outcomes with platform-appropriate instrumentation: fast useful presentation, immediate input response, stable content, efficient scrolling, restrained resource use, and no transition jank.

## Technical Motion And Reduced Motion

Let art direction define why motion exists, its spatial reading, personality, and relative pace. Implement that direction within these constraints:

- Tie motion to a real cause, state, or spatial relationship. Do not use animation to conceal latency or distract from an incomplete layout.
- Keep interactions interruptible and reversible where the action is interruptible. Clean up timers, listeners, animation handles, and stale completion callbacks.
- Maintain correct focus, inertness, hit testing, and accessibility state throughout opening, closing, reordering, dragging, and route transitions.
- Avoid animated properties that cause unacceptable layout or paint work in the affected tree. Measure when layout animation is structurally necessary.
- Do not impose universal duration or easing values. Reuse the approved product or platform motion system and verify the repeated experience.

For reduced motion:

- Detect the platform preference and apply it at component or motion-system boundaries.
- Remove nonessential parallax, large scaling, spatial sweeps, autoplay movement, shimmer, and repeated decorative motion.
- Replace spatial transitions with an instantaneous state change or a restrained non-spatial cue when feedback still matters.
- Preserve essential status, progress, and cause-and-effect information. Reduced motion is not reduced understanding.
- Do not use a universal `*` rule with near-zero durations and `!important`; it can override component contracts, interfere with event-driven logic, and erase useful feedback.
- Test the reduced path itself. A media query's presence does not prove correct behavior.

## Targeted Verification

Add the applicable domain proof to the core contract: actual layout-transformation boundaries; content and input extremes; selected async, offline, conflict, and duplicate states; input responsiveness and layout stability; large-list or critical-media behavior; ordinary and reduced-motion paths; and before-and-after evidence for any performance claim.

Inspect the real route with surrounding layout and data flow. A component story can isolate behavior, but it cannot prove route-level focus, overflow, performance, or recovery.
