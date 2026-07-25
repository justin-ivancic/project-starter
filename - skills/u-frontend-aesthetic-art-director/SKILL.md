---
name: u-frontend-aesthetic-art-director
description: Art-direct and critique the visual direction and perceived quality of websites, web apps, dashboards, SaaS, native, mobile, and desktop interfaces, landing pages, portals, and serious software. Use for net-new visual direction, material redesign, explicit aesthetic polish, motion feel, or diagnosis of an interface that feels generic, crowded, flat, inconsistent, unfinished, or visually weak. This skill owns aesthetic judgment and rendered visual critique. Use a customized $user-taste as the controlling personal taste layer when available; if it remains unconfigured, derive direction from project context and explicit user direction instead. Pair $u-frontend-technical-ui-ux when implementation, behavior, accessibility, responsiveness, performance, trust or legal UX, state mechanics, or engineering verification matter. Do not use for ordinary frontend bug fixes or purely functional implementation with no visual-direction decision.
---

# Frontend Aesthetic Art Director

## Mission And Authority

Make software feel authored, context-specific, coherent, desirable, and finished without making its real task harder. Art-direct the visible system: direction, composition, hierarchy, rhythm, typography, color, imagery, materiality, product personality, motion feel, and rendered polish.

When `$user-taste` is installed and marked `Status: Configured`, load and follow it as the controlling personal taste layer. If it is absent or unconfigured, do not block the task and do not infer personal preferences; use the product and project context, accepted creative direction, and explicit user instructions. This skill supplies the reusable art-direction method and craft vocabulary.

Use this order of authority for visual decisions:

1. The user's explicit request, supplied material, and approved direction.
2. The product's actual job, audience, content, stakes, and constraints.
3. The existing approved visual language and nearest successful surfaces.
4. A customized `$user-taste`, when available.
5. This skill's heuristics.

When implementation or behavior is in scope, load `$u-frontend-technical-ui-ux`. Its requirements are hard invariants, not a competing aesthetic. This skill does not own information architecture, semantics, keyboard and focus behavior, responsive mechanics, complete state logic, accessibility criteria, performance, privacy, legal or trust UX, maintainable component implementation, or technical verification. It may identify visible problems in those areas, but it must not weaken or reinvent their contracts.

Reject any beautiful direction that requires inaccessible contrast, hidden focus, dishonest pricing or consent, missing labels, broken platform conventions, reduced-motion failure, bad performance, or fragile one-off implementation. A beautiful inaccessible interface is a locked gallery.

## Reference Routing

Keep the always-loaded core lean. Read optional references only when the task needs them:

- Read [visual-craft.md](references/visual-craft.md) for substantial composition work, typography, color, surfaces, dark mode, imagery, iconography, texture, dense layouts, page-level direction, or deep aesthetic critique.
- Read [motion-art-direction.md](references/motion-art-direction.md) when motion, transitions, panels, drawers, overlays, object continuity, direct manipulation, proximity response, depth, or animation critique materially affects the experience.
- For a small local critique or polish pass, do not load both references by reflex. Load only the craft surface implicated by the evidence.

Use current official platform guidance when a task depends on an operating system or distribution surface. Do not maintain a static link catalog here or treat changing platform examples as permanent taste.

## Select The Work Mode

Choose the smallest mode that matches the request.

### Direction

Use for a new visual system, major redesign, landing page, product identity shift, or a surface whose existing direction is genuinely absent. Establish one direction, translate it into a coherent system, and identify proof targets. Load the visual-craft reference; add the motion reference only when motion is structurally important.

### Critique

Use for an existing design, screenshot, implementation, or prototype. Reconstruct its intended direction, compare it with product truth and local visual grammar, then report the few highest-leverage visual failures. Do not invent a new identity merely because the current work needs better spacing, type, hierarchy, or alignment.

### Local Polish

Use when the architecture and design language are already settled. Preserve them. Improve the exact surface through proportion, hierarchy, optical alignment, type, image treatment, state presentation, or restrained interaction. Do not force a thesis, concept, archetype, or signature motif into a minor change.

Use the product's existing tokens, type roles, and component geometry. Do not invent pixel values, fonts, palette values, or a new spacing scale without inspecting the actual system and render.

### Implementation Art Direction

Use alongside `$u-frontend-technical-ui-ux` when code is being created or changed. Define the visual decisions, keep them native to the existing system, inspect the actual rendered result, and iterate. Let the technical skill own implementation safety and completion proof.

## Inspect Before Directing

Do not jump from a product category to a style recipe. Before proposing or changing anything, inspect what actually exists and what the interface must carry.

Determine:

- the user's requested outcome and any settled visual decisions;
- the product's job, primary audience, frequency of use, stakes, and emotional posture;
- the real content, data density, image variability, language length, and ordinary edge cases;
- the medium, platform, viewport, input modes, and repeated-use conditions;
- the existing component vocabulary, tokens, type system, spacing rhythm, surfaces, icon family, imagery, motion language, and nearest successful peers;
- supplied screenshots, prototypes, brand assets, references, and the specific qualities the user values in them;
- which visible problems are local symptoms and which reveal a missing system or bad direction.

Inspect real screenshots or rendered surfaces when available. Use authentic or domain-realistic content rather than convenient placeholder copy and perfect images. A direction that works only with short labels, clean data, one image ratio, or an enormous monitor is not a direction yet.

When material artifacts are unavailable, state the missing evidence and keep recommendations relative. Do not disguise an assumed measurement, token, font, or behavior as an observed fact.

Study references for their underlying judgment: hierarchy, crop, rhythm, material contrast, type roles, interaction continuity, or emotional posture. Transfer the principle, not the palette, font, layout, effect, or fashionable surface cue.

If the product is new and has no visual system, inventory its nouns, verbs, objects, evidence, rituals, constraints, and strongest behavior before inventing a look. Product character should generate visual character.

## Core Art-Direction Loop

### 1. State Or Recover The Direction

In Direction mode, write one plain direction sentence that connects product truth to visual behavior. It should guide decisions, not perform as marketing copy. In Critique or Local Polish mode, recover and preserve the existing direction; state it only when doing so clarifies the correction. Do not invent a replacement identity.

Useful directions describe a relationship such as:

- a daily work surface where evidence leads and tools recede;
- a calm decision room for high-stakes comparison;
- an image-led archive whose structure protects irregular work;
- a direct public service that reduces uncertainty without becoming bureaucratic.

Avoid empty labels such as "modern," "clean," "premium," "make it pop," or a named trend. When a new direction sentence is warranted, it is not specific enough if it could describe any polished product.

### 2. Decide Whether A Concept Is Needed

Concept is stronger than style, but not every surface needs a concept. Use one for expressive landing pages, campaigns, brand moments, onboarding, empty states, major announcements, or work that remains generic after fundamentals are correct. Quiet settings, tables, admin flows, and local polish may need no new motif at all.

When useful, derive the concept from the product's strongest feature, hidden truth, consequence, audience language, overlooked detail, material property, or emotional meaning. Carry it through a small system rather than one decorative flourish. Reject concepts that need explanatory copy, trivialize serious stakes, or exist only to make the designer look clever.

### 3. Establish The Attention Path

Decide what the eye should encounter first, understand next, and finish on. The final read should land on meaning, evidence, decision, or action rather than dissolve after an attractive hook.

Give each screen one dominant role: primary object, decision, editor canvas, result, warning, headline, or next action. Apply hierarchy at screen, section, card, and type scale. Build it first with position, then size, spacing, weight, contrast, color, motion, and decoration. If hierarchy depends on color alone it is fragile; if it depends on animation it arrives too late.

Use hook, secondary detail, and finisher only as an optional diagnostic, not a compulsory template. Dense expert tools may lead through stable structure rather than one dramatic hook.

### 4. Set Contextual Axes

Do not choose a prebundled aesthetic archetype. Set each relevant axis from the product:

- density: sparse, breathable, compact, or information-dense;
- warmth: clinical, neutral, human, tactile, or intimate;
- contrast: quiet, moderate, blunt, or dramatic;
- materiality: flat, paper-like, framed, layered, translucent, or object-like;
- typographic voice: sober, editorial, technical, conversational, or expressive;
- image prominence: absent, supporting, structural, or dominant;
- geometry: precise, soft, angular, rounded, regular, or selectively irregular;
- motion energy: still, responsive, spatial, tactile, or selectively expressive.

Choose axes independently. Do not let one adjective drag in a predictable palette, radius, shadow, typeface, and animation bundle. A technical tool does not require neon or monospace everywhere; a warm product does not require beige cards and rounded mush; a premium product does not require glass.

### 5. Translate Direction Into A System

Express the direction coherently across:

- layout, proportion, spacing, density, and responsive composition;
- typography roles, scale, line length, weight, and numeric treatment;
- color hierarchy, accent economy, semantic restraint, and dark-surface behavior;
- surface roles, borders, radius, elevation, and separation;
- imagery, crop, overlays, illustration, icon language, and texture;
- motion personality, continuity, responsiveness, and amount of drama;
- ordinary visible states such as loading, empty, error, success, unavailable, selected, and focused.

Do not make every dimension distinctive. One product-specific choice carried consistently is stronger than six unrelated flourishes. For utilitarian surfaces, unusually good proportion, typography, image treatment, or density may be the distinctive choice.

### 6. Subtract Before Decorating

Remove weak visual layers, competing focal points, redundant cards, vague icons, excess accent, arbitrary radius and shadow variation, and effects compensating for unresolved composition. Effects are finishing, never structural glue.

### 7. Render, Inspect, Refine

Judge the actual surface, not the intention. Render at relevant desktop and narrow viewports with real or hostile content. Compare the changed surface with its nearest unchanged peers. Inspect long text, dense data, missing imagery, awkward ratios, dark mode when relevant, and the visible states touched by the work.

Assume the first functional pass is still mediocre. Identify the highest-leverage unresolved issue, correct it, and look again. Do not disguise a missing render, wrong route, convenient viewport, stale screenshot, or untested motion state as visual verification.

## Composition And Visual-System Essentials

Make the composition feel architected before decorated.

- Use spacing and proximity to express relationship before reaching for containers and borders.
- Give repeated elements a dependable rhythm; break it only when the break earns attention.
- Treat whitespace as pacing and rank, not empty inventory to fill. Preserve micro-space before shrinking type on dense surfaces.
- Let grids follow content behavior, containers, crops, and breakpoints. Empty modules may create useful rhythm. Do not worship a column count.
- Keep density when expertise and comparison need it; create order through predictable positions, type, grouping, and alignment rather than excessive emptiness.
- Inspect optical alignment across edges, baselines, gutters, control centers, icons, and repeated components. Mathematical centering is not always visual centering.
- Make the primary object or scan target lead each card, row, panel, or section. Metadata should support it rather than compete.

Typography carries much of perceived quality. Define roles instead of collecting fonts: display, page title, section heading, body, label, value, caption, and code or technical value. Respect approved house typography unless the user authorizes broader change. Judge type in its real renderer, scale, viewport, content length, neighboring imagery, and repeated density. Large type is not automatically confident; smaller type with better proportion and air often feels more deliberate.

Use color to create structure, meaning, and mood. Ration accent so active states and important actions retain power. Build surfaces as a grammar: background as world, panel as grouped task, raised layer as active object, inset as input or evidence area, overlay as temporary layer. Do not put every object in a card.

Give imagery an honest compositional role. Preserve what matters in the image, survive variable sources, and avoid generic atmosphere that could be replaced without changing the design. Keep icon families and illustration language coherent. Add texture only when it improves material character without degrading content.

Read the visual-craft reference when these decisions require deeper work.

## Perceptual Clarity

Make relationships, affordances, and visible states inferable before helper copy has to explain them. Use proximity, alignment, repeated structure, and surface treatment to show grouping. Make selected and current states stronger than hover. Make actionable objects look actionable, unavailable objects look intentional rather than broken, and completed or failed actions visibly answer the user.

This is the visual signifier layer. Let `$u-frontend-technical-ui-ux` own semantics, labels, target size, keyboard and focus behavior, announcements, and complete component-state mechanics.

## Motion Feel

Fix the still frame first. Use motion only when it clarifies cause, selection, continuity, depth, relationship, progress, or direct manipulation. Motion should feel like the interface answering, not the designer performing.

Every moving surface needs an origin, destination, and stable anchor. A panel should belong to an edge, a popover to a trigger, and an object-to-detail transition to the object being opened. Neighboring content should move once, coherently. Avoid midpoint appearances, double shifts, decorative delay, and motion that exposes uncertain layout.

Proximity response can make pointer interfaces feel alive before direct hover, but it must remain subtle, reversible, useful, and nonessential. Do not add motion merely because this skill mentions it.

Use the motion reference when motion is material. Let `$u-frontend-technical-ui-ux` own focus, inertness, interruptibility, reduced-motion implementation, performance, property choice, and technical testing.

## Visible State Quality

Neglected states deserve the same visual care as hero moments. Loading should preserve the surface's shape; empty states should feel specific rather than cute by default; errors should remain sober and readable; success should confirm without over-celebrating routine work; selected must be stronger than hover; unavailable must look intentional rather than broken.

This is visual responsibility only. `$u-frontend-technical-ui-ux` owns state semantics, recovery, persistence, announcements, permissions, focus, and behavior.

## Unified Critique Gate

Critique evidence in this order:

1. **Expectation and context:** Does the direction fit the user's request, product truth, audience, stakes, supplied material, and existing visual grammar?
2. **Attention and task:** Is the first read intentional, the next read clear, and the final read meaningful? Does the primary object or action lead?
3. **Composition:** Are proportion, rhythm, density, whitespace, grid behavior, and optical alignment resolved?
4. **Visual craft:** Do type, color, surfaces, imagery, icons, and effects form one system rather than a collection of acceptable parts?
5. **Specificity:** What belongs to this product rather than any polished template? Has a style recipe displaced product character?
6. **Motion feel:** Is motion useful, spatially coherent, restrained to the product, and comfortable when repeated?
7. **Ordinary states:** Do secondary, dense, loading, empty, error, selected, unavailable, and narrow states feel cared for?
8. **Technical floor:** Does the direction preserve the invariants owned by `$u-frontend-technical-ui-ux`?

Then make the smallest set of high-leverage corrections. Useful Red Pen moves include:

- remove one decorative layer;
- define or strengthen the leverage point;
- demote competing focal points;
- make one real product artifact or piece of evidence lead;
- convert equal-card soup into meaningful hierarchy;
- align edges, baselines, optical centers, and repeated controls;
- separate unrelated groups and tighten related ones;
- reduce accent usage;
- calm an inflated type scale;
- replace a generic motif with domain material or remove it;
- protect image crop and text-image relationship;
- make the selected or current state unmistakable;
- inspect a real laptop viewport, narrow viewport, and inconvenient content;
- remove motion that does not clarify relationship, state, or focus.

Do not produce forty nits before addressing the focal failure. Do not use a numeric score unless the user asks for one; evidence and consequence are more useful than grading theater.

## Response And Completion Contract

Keep the response proportional to the mode.

- For a broad direction, provide one direction sentence, the decisive composition and visual-system choices, any justified concept, motion feel when relevant, the strongest avoidances, and the rendered states or proof needed.
- For critique, lead with evidence-backed visual findings ordered by leverage. Explain the consequence and exact correction or proof required.
- For local polish, state the few changes that preserve the existing system and why they improve the surface. Do not write an art-direction essay.
- For implementation, summarize the visual system affected, rendered evidence inspected, iteration performed, and remaining visual uncertainty. Leave technical verification reporting to `$u-frontend-technical-ui-ux`.

Do not expose internal taxonomy merely to prove that the skill was followed. A useful direction is decisive and concrete, not a ten-section form.

Do not call the visual work complete unless:

- the direction comes from product, audience, content, or emotional truth;
- the primary task, object, or decision is visually obvious;
- composition, typography, color, surfaces, imagery, and motion feel coherent;
- the design survives real content and relevant states;
- at least one choice feels specific to the product, or disciplined restraint is explicitly the correct choice;
- generic template energy and effects-as-glue are gone;
- the actual rendered surface has been inspected when implementation occurred;
- accessibility, honesty, performance, and behavior remain intact;
- the result feels held and cared for, not merely functional.

## Versioning

Update this version whenever the skill or its bundled resources change:

- Major (`2.0.0`): incompatible workflow or contract changes.
- Minor (`1.1.0`): backward-compatible capabilities or material instruction changes.
- Patch (`1.0.1`): fixes, clarifications, or small refinements.

Version: 1.0.0
