# Visual Craft Reference

Use this reference for substantial composition work, typography, color, surfaces, dark mode, imagery, iconography, texture, dense layouts, page-level visual direction, or deep aesthetic critique. Keep a customized `$user-taste` in control when one is available; otherwise derive direction from the project context and explicit user direction. Treat every example as a lens to test, not a style preset.

Technical semantics, accessibility mechanics, responsive behavior, state logic, performance, legal or trust UX, component architecture, and implementation verification belong to `$u-frontend-technical-ui-ux`.

## Contents

- [Concept And Product Posture](#concept-and-product-posture)
- [Composition And Eye Flow](#composition-and-eye-flow)
- [Rhythm, Grid, Space, And Density](#rhythm-grid-space-and-density)
- [Cards, Tension, And Friction](#cards-tension-and-friction)
- [Typography Job-Fit](#typography-job-fit)
- [Typeface Craft](#typeface-craft)
- [Color And Dark Surfaces](#color-and-dark-surfaces)
- [Surfaces, Controls, And Elevation](#surfaces-controls-and-elevation)
- [Imagery, Icons, And Texture](#imagery-icons-and-texture)
- [Page, State, And Domain Lenses](#page-state-and-domain-lenses)
- [Reference Extraction And Anti-Template Checks](#reference-extraction-and-anti-template-checks)

## Concept And Product Posture

### Derive Concept From Truth

Use a creative concept only when a surface benefits from a memorable organizing idea. Style is weaker than concept. Root the idea in something the product, content, audience, or situation already contains:

- **Hidden truth:** the real behavior, fear, hope, consequence, or emotional impact behind the obvious topic.
- **Strongest feature:** the workflow, material property, interaction, or result that can organize the direction.
- **Audience language:** the terms, rituals, metaphors, constraints, symbols, or in-jokes the intended audience already understands.
- **Literalized metaphor:** a phrase, error, promise, or claim made physically visible without becoming a gimmick.
- **Unexpected combination:** two familiar ideas joined because the combination clarifies the product, not merely because it looks novel.
- **Overlooked detail:** a small domain object, mark, behavior, or material quality that can connect the system without a giant gesture.
- **Information to emotion:** a fact, status, error, or measurement connected to its human meaning or consequence.

Describe the concept in one sentence. Check that it improves understanding, comes from the subject rather than decoration, survives without explanatory copy, can become a small system, and fits the stakes. Commit one strong idea rather than producing endless stylistic options.

Do not force humor, cute metaphor, spectacle, or expressive type into severe, legal, health, financial, privacy, safety, grief-adjacent, or high-stress moments unless the product and user explicitly support it.

### Read Product Posture Without Prescribing A Look

Use product posture to constrain decisions, not to select a premade palette.

- **Serious daily work:** protect scanning, confidence, stable positions, calm density, and repeated use. Keep landing-page gloss out of work surfaces.
- **Creative workspace:** let the user's content or canvas dominate. Keep tools tactile and reachable without competing with the work.
- **Technical instrument:** emphasize precision, numeric alignment, evidence, state clarity, and compact relationships. Avoid terminal cosplay, neon, and monospace everywhere.
- **Trust or transaction:** favor familiar patterns, explicit value and consequence, sober forms, and visual calm near decisions. Avoid urgency theater and decorative clutter.
- **Editorial or knowledge:** prioritize reading rhythm, content hierarchy, line measure, figures, code, citations, and useful navigation. Avoid typographic vanity and sticky clutter.
- **Consumer companion:** allow warmth and relevant personality without infantilizing serious goals, pressuring engagement, or turning routine progress into confetti.

Combine postures when the product genuinely has multiple surfaces. A public service may need a warm, low-stress visitor flow and a dense operational staff queue. Preserve one underlying language while letting density and emphasis change by job.

## Composition And Eye Flow

Composition controls where the eye starts, moves, pauses, and finishes. A layout can be logically correct and still feel weak when attention has no path.

Before arranging a screen, establish:

- **Message or posture:** calm, urgent, precise, playful, exploratory, serious, safe, direct, or intentionally disruptive.
- **Medium and context:** phone, laptop, wide desktop, kiosk, embedded card, presentation, public display, or long reading surface.
- **Purpose:** understand, compare, decide, buy, sign up, read, create, recover, share, stop, or feel something.

Make those answers materially change the layout. A high-stakes decision needs a different attention path from an image-led portfolio. A dense operational surface should not borrow campaign-page drama merely because both can look polished.

### Focal Point And Hierarchy

Give the composition one leverage point: the object that intentionally pulls the first look. It may be a headline, artwork, editor canvas, chart, current status, warning, product artifact, result, or primary decision.

An optional three-read path can help:

1. **Hook:** earns attention through content, placement, contrast, or a meaningful visual object.
2. **Secondary detail:** explains, orients, proves, or creates useful intrigue.
3. **Finisher:** lands on meaning, decision, action, date, price, result, or next step.

Do not treat this as a universal hero template. Tables, editors, and expert workspaces may guide attention through stable structure, repeated alignment, and persistent status rather than dramatic scale.

Apply hierarchy at several scales: whole screen, region, section, card, row, and type role. If every object is level two, nothing leads. If the final read is absent, attention never becomes understanding or action.

Prefer hierarchy through position, then size, spacing, weight, contrast, color, motion, and decoration. Use several tools coherently, but do not spend them all on every object.

### Flow And Movement

Choose the flow mechanism deliberately:

- **Direct guidance:** paths, rails, arrows, gaze, lines, or step progress when sequence or route is the content.
- **Hierarchy-driven flow:** position, scale, spacing, and contrast form an invisible route; usually the safest product-UI default.
- **Layered paths:** one primary route plus secondary paths that reward attention without competing.
- **Implied movement:** cropping, repetition, progressive scale, directional texture, or subject orientation; use more freely in editorial or image-led work than in daily tools.
- **Controlled disruption:** one crop, overlap, off-grid element, unusual type move, or contrast block that pauses the eye for a product reason.
- **Temporal flow:** impact, scan, linger, pause, release. Use pacing where narrative or staged understanding matters.

Audit where the eye goes first, second, and last. Check whether forms, image subjects, diagonals, repeated elements, or negative space guide attention toward meaning or toward a dead edge. Treat F- and Z-patterns as loose observations, never laws.

## Rhythm, Grid, Space, And Density

Use repeated rhythm to build trust and scanning memory. Break rhythm only when the break communicates rank, change, or intentional emphasis.

Use a spacing scale already present in the product. A four-unit base can be useful, but it is an example rather than authority. Optical relationships, type metrics, content density, and platform conventions matter more than mathematical purity.

Group related objects through proximity before adding borders. Separate unrelated groups with meaningful space. Inspect both:

- **Macro whitespace:** large pacing, emphasis, calm, and separation between major roles.
- **Micro whitespace:** legibility, control comfort, label-value clarity, and dense scanning.
- **Passive whitespace:** comfort that lets content breathe.
- **Active whitespace:** space deliberately guiding the eye or staging a decision.

Preserve micro-space before shrinking type on dense surfaces. Density is not a defect. Expert tools can remain compact when primary controls are comfortable, metadata stays predictable, typography remains legible, and alignment creates order.

Choose grid behavior from content:

- columns for repeated page and feed structure;
- modular grids for comparable objects;
- baseline rhythm for text, tables, documentation, and mixed type;
- asymmetric composition when one object should dominate;
- compound grids when regions have different behaviors;
- manuscript or focused columns for reading and forms.

Set grids from the real container, safe areas, breakpoints, expected crops, reading measure, and scroll behavior. Empty modules can create rhythm. Break a grid only when the structure is clear enough for the break to feel intentional.

Inspect optical alignment across left and right edges, baselines, gutters, icon and text centers, repeated controls, title blocks, and panel boundaries. Correct what looks misaligned even when the coordinates match.

## Cards, Tension, And Friction

Before styling a card, row, or tile, decide what the user scans for. Let the main object, title, status, decision, image, or result lead. Keep metadata quieter and consistently placed. Put prices, totals, health, dates, or decisive values where the eye can repeatedly find them.

Avoid equal-card soup. Repeated cards may remain predictable, but vary hierarchy when one item, section, or action deserves leadership. Do not wrap every small fact in a large rounded container.

Use visual tension only when the product needs energy, urgency, or unease. Tension can come from imbalance, proximity, opposing direction, crop, contrast, or a grid break. Random tension creates distrust before the content is understood.

Use friction as a deliberate pause in an otherwise easy path. Tight spacing, overlap, rotation, blur, unusual type, crop, texture, or harsh contrast must sharpen the message or protect a decision. Remove friction that asks the user to solve the layout before completing the task.

Treat directional associations as hypotheses, not rules. Horizontal structure can feel stable, vertical emphasis can feel formal or alert, and diagonals can feel active, but content, culture, reading direction, scale, and repetition can reverse those effects.

## Typography Job-Fit

Typography carries much of perceived quality in software. Choose type by job, context, medium, and repeated use rather than novelty.

- Use one main UI family unless another role has a real purpose.
- Reserve display or script faces for short brand and campaign moments; do not force them into dense controls or long reading.
- Use serif, sans, mono, rounded, condensed, sharp, or high-contrast forms according to their real role, not a genre stereotype.
- Use monospace for code, logs, IDs, technical values, or a deliberate accent; do not make everything monospace because the product is technical.
- Let a display face add character without becoming the only source of identity.
- Respect approved house typography unless the user explicitly authorizes a new system.

Define roles rather than vibes: display, page title, section heading, body, label, value, caption, and code or technical value. Keep the routine role count small enough to feel intentional.

Treat familiar numeric ranges as starting evidence, not laws. Body text around common web reading sizes and tight display leading may work, but typeface metrics, viewport, language, distance, platform, density, and user needs decide the result. Judge actual wrapping and enlarged or narrow presentation when evidence exists; let `$u-frontend-technical-ui-ux` own formal zoom and accessibility verification.

For reading surfaces, protect comfortable measure, real paragraph rhythm, distinct links, meaningful headings, and predictable spacing for figures, code, and callouts. For data, use tabular numerals where supported, align values consistently, keep units visible, avoid meaningless decimals, and distinguish label from value.

## Typeface Craft

When typography feels wrong, inspect the craft before replacing the entire direction:

- **Stroke weight:** too heavy becomes clumsy; too thin becomes fragile or poorly rendered.
- **Tracking and word shape:** too tight blurs; too loose disintegrates. Avoid ad hoc tracking across repeated roles.
- **Kerning:** inspect brand names, CTAs, large titles, punctuation, and high-visibility pairs.
- **Proportion:** x-height, width, ascenders, descenders, counters, and apertures determine openness, compactness, and scanning comfort.
- **Optical correction:** letters, icons, and control labels often need to look centered rather than be mathematically centered.
- **Rendering:** inspect the real browser or platform output, available weights, dark presentation, antialiasing, and viewport rather than trusting a specimen.

Small UI text needs open shapes, sturdy strokes, clear counters, and spacing that survives repetition. Large type exposes kerning, curves, punctuation, and line breaks. Physical or image-rendered media such as canvas text, screenshots, LED display, vinyl, embroidery, or exported graphics punish delicate details and tight gaps.

Judge type next to the actual imagery and controls it must live with. A font specimen proves little about product fit.

## Color And Dark Surfaces

Build color as a system of roles rather than a mood-board strip: background, panel, text hierarchy, borders, accent, semantic states, and data colors where needed.

Ration accent. The fewer routine objects that use it, the more power remains for primary action, active navigation, selection, important status, and meaningful brand moments. Do not spend the accent on every icon, link, badge, border, and decorative blob.

Derive palettes from product material, brand, content, environment, and contrast needs. Let actual use prove the necessary range. Pair semantic color with text, shape, icon, or label; `$u-frontend-technical-ui-ux` owns formal accessibility and state requirements.

When building a new palette, start from the primary or brand color and derive lighter and darker roles only as real surfaces and states require them. Avoid manufacturing a large ramp before the interface proves its needs.

Treat dark mode as a new luminance and depth composition, not token inversion:

- re-establish the hierarchy of world, panel, raised, inset, and overlay surfaces;
- use luminance, borders, and restrained glow or shadow to separate layers;
- quiet borders that become too loud against dark backgrounds;
- reduce saturation across large colored areas;
- keep chips, accents, selection, and focus unmistakable without glowing text;
- inspect real imagery, code, charts, and muted text rather than only the empty shell.

Do not assume pure black or dark glass is automatically premium. Choose it only when content and product posture support it.

## Surfaces, Controls, And Elevation

Use surfaces to explain structure:

- background as the product world;
- panel as a grouped task or region;
- raised surface as an active or floating object;
- inset surface as input, canvas, media, or evidence area;
- overlay as a temporary dialog, sheet, popover, or focused layer.

Use borders when they clarify grouping, state, or affordance. Prefer space when space is enough. Watch nested cards and double borders.

Use shadows to communicate elevation, not to smudge every component. Keep ordinary panels quieter than true floating surfaces. Match radius to component role and product character rather than applying one giant radius everywhere.

Treat controls visually as typography, spacing, state, and surface working together. Keep primary and secondary actions related in geometry while differing in emphasis. Align icons optically with labels. Never give non-interactive objects hover lift, pointer language, or button-like chrome.

Let `$u-frontend-technical-ui-ux` own semantics, target size, focus, keyboard behavior, labels, and component state mechanics.

## Imagery, Icons, And Texture

Use imagery because the object matters, speeds recognition, proves the product, establishes emotional truth, or carries the work. Do not use it as replaceable generic atmosphere.

Design for variable and imperfect sources. Test bright, dark, busy, low-contrast, landscape, portrait, missing, and awkwardly cropped images. Preserve meaningful image regions. If text overlays imagery, use directional protection that preserves both text and image rather than killing the whole image with a blunt overlay.

Progressive blur can support a directional gradient when it protects text without flattening the image. Keep it only if contrast, image readability, and the technical constraints owned by `$u-frontend-technical-ui-ux` survive.

Use product screenshots and artifacts to show real depth: list and detail, before and after, collaboration, command, evidence, result, or workflow. Avoid fake metrics, impossible data, obsolete chrome, and device frames without a platform reason.

Use one icon family or a deliberately reconciled system. Match stroke and visual weight to surrounding type and control size. Use icons to aid recognition, not to decorate every label. Preserve clear labels for important or ambiguous actions.

Use illustration to orient, explain, warm, or establish brand. Avoid generic floating people, random unrelated 3D objects, cartoons that trivialize severe states, and mixed styles.

Use grain and texture in tiny amounts when they add material character. Keep them behind content and simplify them when they hurt clarity, repetition, or performance.

## Page, State, And Domain Lenses

Use these as visual prompts only. `$u-frontend-technical-ui-ux` owns flow, behavior, and technical completion.

- **Landing page:** make the product artifact, concrete promise, audience, proof, and next step visually legible. Change section rhythm by job rather than repeating identical feature cards.
- **Dashboard:** make the important answer, anomaly, evidence, or required decision dominate. Avoid metric confetti.
- **Table or dense list:** create calm through row rhythm, numeric alignment, sparse status treatment, stable positions, and visible selection.
- **Form or checkout:** keep the composition safe, explicit, sober, and low-noise near commitment.
- **Settings:** create a quiet, well-labeled workshop rather than a card gallery. Separate danger without turning the entire page red.
- **Editor or canvas:** let user content dominate; make the active object and tool context visually unmistakable.
- **Mobile:** preserve hierarchy, interruption tolerance, and glanceability. Do not merely shrink desktop density.

Give ordinary states the product's full visual language:

- loading should preserve structure rather than flash a different visual world;
- empty should retain product character without default sadness or cuteness, while leaving message, action, and semantics to `$u-frontend-technical-ui-ux`;
- error should be sober, specific, and visually recoverable;
- success should confirm without turning routine work into spectacle;
- disabled and unavailable should look intentional, distinct, and understandable;
- selected, current, focused, and active should be clearly stronger than hover.

Adjust tone by stakes. Finance, health, safety, legal, privacy, and destructive moments need sober hierarchy and no cute severe states. Technical tools need precision without cyber cosplay. Education can be warm without patronizing. AI surfaces should show bounded capability and uncertainty without magical glow or fake sentience.

## Reference Extraction And Anti-Template Checks

When studying a reference, name the principle that makes it work. Test whether that principle survives different content, viewport, product, and audience. Combine compatible lessons with the product's own structure rather than copying one source.

Reject generic paste such as:

- a purple-blue gradient blob behind a centered hero;
- equal feature cards with vague icons;
- gray card soup;
- random glassmorphism;
- one radius and shadow inflated across everything;
- mixed icon families;
- fake analytics, fake testimonials, and generic stock celebration;
- oversized type used instead of hierarchy;
- decorative animation that delays the product;
- copy that could belong to any modern team.

Fix generic output through composition and specificity: make real product material lead, use domain language, show workflow or evidence, vary section jobs, and choose one context-derived visual decision. If the fundamentals are already excellent, disciplined restraint may be the correct distinctive move.
