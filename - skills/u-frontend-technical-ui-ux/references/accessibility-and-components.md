# Accessibility And Component Behavior

Use this reference when accessibility, semantics, forms, focus, announcements, custom widgets, or reusable component behavior materially affects the task.

## Contents

- Target And Evidence
- Structure And Semantics
- Keyboard And Focus
- Forms And Authentication Inputs
- Visual And Perceptual Access
- ARIA And Custom Widgets
- Component Contracts
- Accessibility Verification

## Target And Evidence

Use WCAG 2.2 Level AA as the default web engineering target unless a contract, procurement requirement, platform, or user instruction specifies a stricter or different target. A newer internal target does not erase a named contractual standard; record both when they differ.

Do not claim conformance from a checklist, automated scan, library choice, or this reference. Conformance depends on the complete scoped experience and applicable standard. Report the target, surfaces inspected, methods used, failures found, and gaps remaining.

When legal, procurement, or platform treatment matters, verify current official sources. Standards, harmonization status, enforcement dates, and platform accessibility requirements change.

Use the official [WCAG 2.2 Recommendation](https://www.w3.org/TR/WCAG22/) and [WAI-ARIA Authoring Practices Guide](https://www.w3.org/WAI/ARIA/apg/) as stable technical starting points, then verify that the version and interpretation fit the task. For a public product with an accessibility commitment or obligation, keep a findable route for accessibility feedback or support.

## Structure And Semantics

- Use the native element whose semantics and behavior match the task. Use a button for an action, a link for navigation or a resource, a table for tabular relationships, and lists for list structure.
- Mark page regions with appropriate native landmarks. Give repeated or multiple regions useful accessible names when needed for distinction.
- Provide a clear, meaningful heading hierarchy that reflects content structure. One clear main heading is usually appropriate, but multiple `h1` elements or another coherent structure are not automatically accessibility failures. Do not add invisible headings merely to satisfy a mechanical rule.
- Keep DOM, reading, visual, and focus order aligned. If visual rearrangement changes meaning or interaction sequence, change the underlying structure rather than relying on CSS order.
- Give icon-only and otherwise non-text controls an accessible name that describes the action or result, not the icon's appearance.
- Declare the primary document language and mark meaningful language changes.
- Preserve relationships between labels, instructions, values, units, status, help, and errors programmatically.
- Do not use title attributes, placeholders, color, position, or visual grouping as the only source of essential meaning.

For native surfaces, map the same obligations to platform accessibility APIs: labels, hints, roles or traits, values, state, grouping, traversal order, dynamic type or font scaling, and content descriptions.

## Keyboard And Focus

Make every core action operable by keyboard or an equivalent supported assistive input.

- Keep focus indicators visible against their actual adjacent colors and unobscured by sticky headers, overlays, cookie banners, or scroll containers. A generic `currentColor` outline is not proof of adequate visibility.
- Keep focus order aligned with task order. Avoid positive `tabindex` and manual focus choreography unless the widget pattern genuinely requires it.
- On route or major context changes, move or preserve focus according to what helps the user understand the new context. Do not reset focus by reflex.
- When a modal opens, place focus at a useful starting point based on its content and consequence. Keep focus inside while it is modal and make the background inert.
- When a modal closes, return focus to the invoking control when it still exists and remains the logical next step. Otherwise move focus to the next meaningful workflow location.
- Support Escape for dialogs and transient surfaces according to the platform pattern. Do not create a dismissless dialog merely by invoking “legal” or “security” as a reason; provide an explicit safe resolution or exit and verify the exceptional workflow.
- Use arrow-key, Home, End, Page Up, Page Down, typeahead, or roving-tabindex behavior only when the chosen composite-widget pattern calls for it and the complete pattern is implemented.
- Provide a way to bypass repeated navigation or blocks where required. A correctly placed skip link, landmark navigation, or equivalent may satisfy the need.
- Keep unavailable actions understandable. If disabling a control would hide how to proceed, keep the explanation adjacent and consider whether an enabled action with validation is clearer.

## Forms And Authentication Inputs

Treat a form as a recovery system, not a data-entry trap.

- Give every control a persistent programmatic label. Use placeholder text only for examples or formatting hints.
- State required and optional status consistently. Avoid requiring users to infer it from an asterisk with no explanation.
- Use appropriate input types, `autocomplete`, `inputmode`, constraints, and platform equivalents. Do not fight browser, password-manager, autofill, or translation behavior without a proven reason.
- Allow paste into password, one-time-code, confirmation, and payment fields. Avoid cognitive-function tests when a supported authentication alternative can meet the security need.
- Validate at a useful time. Do not announce errors on every keystroke when the user has not had a chance to finish.
- Identify the field, explain the problem, and suggest a correction. Associate help and error content with the input without overwriting existing descriptions.
- Announce newly introduced blocking errors with an appropriate summary or live-region strategy. Do not make every validation message assertive.
- Preserve non-sensitive entries after validation, network, or payment failure. Never retain passwords, one-time codes, CVV, raw card credentials, secret recovery material, or similarly sensitive values for convenience.
- Keep focus on or move it to the most useful recovery point after submission. For multi-error forms, provide a usable error summary and links when appropriate.
- Avoid unnecessary field splitting. When domain structure requires segments, make the group, labels, navigation, paste behavior, and error handling coherent.
- For long workflows, preserve progress, communicate saving honestly, allow review, and explain what will happen on exit or session expiry.

Do not canonize a framework wrapper such as `React.cloneElement` as the generic field pattern. Prefer explicit composition or the repository's established field API so existing properties, descriptions, refs, and event handlers are not silently overwritten.

## Visual And Perceptual Access

- Meet applicable contrast requirements: commonly at least 4.5:1 for normal text, 3:1 for large text, and 3:1 for meaningful non-text interface indicators under WCAG 2.2 AA, subject to the criterion definitions and exceptions. Check placeholder, focus, selected, error, and forced-color behavior where relevant. Keep disabled or inactive UI understandable even where a standard provides a contrast exception; distinguish voluntary clarity from a conformance claim.
- Do not rely on color alone for status, selection, required fields, chart meaning, or validation.
- Support text resizing to 200% without loss of content or function. Support reflow at the applicable narrow equivalent, commonly 320 CSS pixels for web content, except genuinely two-dimensional content covered by the standard's exceptions.
- Keep controls and targets usable with touch, tremor, magnification, and dense layouts. For WCAG 2.2 AA web work, account for the 24-by-24 CSS-pixel minimum target criterion and its spacing, inline, equivalent, user-agent, and essential exceptions rather than treating one number as universal design advice.
- Preserve readable line wrapping, label association, status visibility, and action access under large text and localization expansion.
- Avoid flashes and motion patterns that can trigger physical reactions. Respect user preferences for reduced motion, contrast, transparency, and text size where the platform exposes them.
- Test forced colors or high-contrast modes when custom control surfaces, charts, icons, or focus indicators could disappear.
- Do not hide essential content from assistive technology merely to simplify the visual layout.

## ARIA And Custom Widgets

Use ARIA to expose behavior that already exists; it does not create behavior.

- Prefer native controls. No ARIA is better than incorrect ARIA.
- Do not put `aria-hidden="true"` on focusable content or an ancestor of focusable content.
- Keep roles, names, values, states, and properties synchronized with visible behavior.
- Use `aria-live` sparingly. Use polite status for ordinary asynchronous updates and assertive interruption only for genuinely urgent information.
- Do not apply `aria-busy`, `aria-disabled`, `aria-invalid`, expanded state, selection state, or progress values without implementing the corresponding interaction and visual behavior.
- Follow the current official WAI-ARIA Authoring Practices for custom widgets. Treat its examples as interaction patterns, not copy-paste production components.
- Test the browser and assistive-technology combinations the product actually supports. Correct markup alone does not prove a usable accessibility tree.

## Component Contracts

### Buttons, Links, And Pending Actions

- Use explicit labels such as “Save changes,” “Export data,” or “Cancel plan” when consequence matters. Generic “OK” or “Continue” is acceptable only when context makes the result unmistakable.
- Prevent repeated activation while a request is pending and expose progress in text or a programmatic status. A spinner alone is not a status.
- Decide whether the pending control should remain focusable. Native `disabled` prevents activation and form submission but can remove discoverability; `aria-disabled` preserves focus but requires guarded interaction. Follow the existing component contract.
- Treat server-side idempotency or duplicate protection as a separate dependency for billable, destructive, or otherwise consequential actions.

### Dialogs, Sheets, Popovers, And Drawers

- Choose the surface by behavior, not fashion. Use a modal only when interaction outside it must pause.
- Associate the title and any essential description. Keep close controls named and reachable.
- Make modal background content inert. Avoid stacked modals unless the workflow truly requires them and focus behavior is proven.
- Preserve on-screen keyboard access, safe areas, scrolling, and reachable actions on small screens.
- Name destructive objects and consequences. Default focus should not make accidental destructive confirmation easy.

### Toasts, Status, Alerts, And Errors

- Use transient toasts only for non-critical feedback that is also reflected in persistent state when needed.
- Keep required instructions, warnings, and errors present until resolved or intentionally dismissed.
- Do not steal focus for routine success. Move focus only when the task context actually changes.
- Offer undo for reversible destructive actions when the rollback is reliable and its time limit is clear.

### Tables And Data Grids

- Use native table semantics for ordinary tabular reading and comparison.
- Use an interactive grid pattern only when spreadsheet-like cell navigation is truly needed; then implement its complete focus and keyboard model.
- Keep headers, sort state, selection, row actions, and accessible counts understandable.
- Add sorting, filtering, pagination, density, column visibility, or export only when they support the real task; do not turn every table into a data-grid product.
- Preserve numeric comparison through consistent alignment and tabular figures where the approved typography supports them; coordinate the visible treatment with the aesthetic owner.
- Virtualize only after measuring need. Preserve focus, accessible position or count, scrolling, and restoration behavior.
- Test sticky regions, overflow, zoom, narrow space, and screen-reader navigation together.
- Distinguish loading, empty, partial, and failed regions. Give a true empty state an appropriate next action; one failed widget must not falsify or erase unrelated data.

### Search, Filters, Tabs, And Command Surfaces

- State the search scope and make active filters discoverable and removable.
- Preserve filter or query state across navigation when that supports recurring work.
- Give no-result states a clear explanation and recovery path.
- Use tabs only for peer views of the same context. Keep selected state and controlled panel relationships programmatic.
- Do not hide critical commands exclusively inside a command palette or shortcut.
- Implement grouping, typeahead, selection, and keyboard behavior according to the chosen official pattern.

## Accessibility Verification

Use automation to find detectable failures, then perform manual interaction checks.

For material changes, add the applicable accessibility-specific proof to the core contract: keyboard completion; focus order, visibility, restoration, and obstruction; names, roles, states, relationships, and announcements; zoom, text resizing, reflow, and localization; supported screen-reader smoke testing; target usability; and forced-color or reduced-motion behavior where implicated. Use automated checks at both component and routed-flow level when the repository supports them.

Record supported environments and gaps. Automated success is not a substitute for manual proof, and one screen-reader/browser pairing is not universal coverage.
