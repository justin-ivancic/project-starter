# Motion Art Direction Reference

Use this reference when motion, transitions, panels, drawers, overlays, direct manipulation, object continuity, proximity behavior, depth, or animation critique materially shapes the experience.

Keep a customized `$user-taste` in control when one is available. If it remains unconfigured, derive motion direction from the project context and explicit user direction. Pair `$u-frontend-technical-ui-ux` for focus, inertness, keyboard and touch behavior, interruptibility, reduced-motion implementation, performance, property choice, component state mechanics, and technical testing. This reference owns motion intent, personality, spatial choreography, and visual critique.

## Contents

- [Motion Starts With The Still Frame](#motion-starts-with-the-still-frame)
- [Motion Roles And Personality](#motion-roles-and-personality)
- [Spatial Accountability](#spatial-accountability)
- [Surface Type Before Animation](#surface-type-before-animation)
- [State, Layout, And Visual Sequencing](#state-layout-and-visual-sequencing)
- [Timing, Easing, And Cadence](#timing-easing-and-cadence)
- [Continuity, Depth, And Direct Manipulation](#continuity-depth-and-direct-manipulation)
- [Push Transitions](#push-transitions)
- [Proximity Response](#proximity-response)
- [Motion Craft And Proof](#motion-craft-and-proof)
- [Failure Patterns](#failure-patterns)

## Motion Starts With The Still Frame

Fix the still frame first. Motion cannot rescue weak hierarchy, uncertain layout, bad spacing, or missing state clarity. The start and end states should each make sense when frozen.

Use motion to make strong structure clearer, more responsive, more continuous, or selectively memorable. Do not animate merely because the interface feels visually plain. Stillness can be an intentional product characteristic.

Before proposing motion, state in one sentence:

- the trigger;
- the user's intent;
- the start state;
- the end state;
- the relationship or feedback the motion must clarify.

If that sentence has no useful answer, the motion probably has no job.

## Motion Roles And Personality

Classify the motion before tuning it.

### Functional

Use for direct task feedback: press, select, drag, reorder, filter, save, copy, load, complete, fail, insert, remove, or change state. Keep feedback close to the action and fast enough to preserve confidence.

### Structural

Use for product shape and spatial relationships: view changes, panels, expansion, card-to-detail, tab adjacency, overlay layers, navigation, object continuity, and make-room transitions. Structural motion should answer where the surface came from, where it went, what layer the user occupies, and how to return.

### Emotional

Use selectively for brand memory, warmth, delight, or ceremony. Reserve it for moments whose emotional value can carry the cost. Do not make routine saves, ordinary navigation, repeated table actions, or high-stakes errors perform for attention.

Set personality from the product rather than a trend:

- serious repeated-use software usually feels fast, understated, and confidence-building;
- creative tools may feel tactile, object-oriented, and slightly expressive;
- technical instruments usually feel crisp, directional, and information-preserving;
- consumer companions may feel warmer and more rewarding without becoming sticky;
- editorial and image-led surfaces may use continuity and pacing without becoming a carnival.

These are hypotheses to test. An explicit product direction can justify another answer.

## Spatial Accountability

Every moving surface needs:

- an origin;
- a destination;
- a stable edge, anchor, or object relationship.

A right-side inspector should feel attached to the right edge. A bottom sheet should belong to the bottom edge. A popover should arise from its trigger. A card-to-detail transition should preserve the opened object. A selected marker should move between real peer positions.

If a surface appears from the middle, snaps to an edge, moves neighboring content twice, changes direction without reason, or settles after the layout has already jumped, the motion is exposing uncertainty.

Animate the minimum meaningful relationship. One stable boundary or object moving clearly is stronger than the entire interface drifting.

## Surface Type Before Animation

Identify what the surface is before choosing how it moves:

- **Make-room panel:** becomes part of the page and changes neighboring space.
- **Overlay sheet or drawer:** sits above the page without reflowing the underlying composition.
- **Modal dialog or window:** creates a focused layer and decision.
- **Popover or menu:** remains spatially tied to a trigger.
- **Passive detail or status surface:** appears without taking task ownership.
- **Object-to-detail transition:** preserves identity between a source object and expanded state.
- **Replacement surface:** one rail, panel, or state takes the place of another in the same region.

Do not apply one generic drawer animation to every panel-like object. Surface type controls visual ownership, source direction, distance, layering, and how much of the surrounding composition should respond. `$u-frontend-technical-ui-ux` controls the behavioral contract.

## State, Layout, And Visual Sequencing

Separate three events:

1. **Semantic state:** what the product now means or considers active.
2. **Layout commitment:** what space exists and which region owns it.
3. **Visual motion:** how the user perceives the change.

They may occur close together, but they should not fight for ownership. For a make-room panel, the page can commit space as one coherent movement while the inner content follows slightly later. The result should read as "the page made room" rather than "an overlay arrived and shoved everything."

Give each large change one perceptual motion owner. Avoid choreography that makes several layout regions appear to move independently or fight for attention. Let `$u-frontend-technical-ui-ux` choose the properties and implementation structure.

Keep immediate local feedback even when a larger transition takes longer. A trigger should answer promptly; secondary choreography must not make the product feel slow.

Treat reduced motion as an intentionally art-directed alternate path, not an amputated version. Preserve state, visibility, hierarchy, cause, and task completion while removing unnecessary travel, scale, parallax, long fades, and spectacle. Let `$u-frontend-technical-ui-ux` choose and verify the implementation.

## Timing, Easing, And Cadence

Treat timing as proportional to distance, scale, importance, interruption, and product personality. Small local feedback should feel immediate. Larger spatial changes can take longer when the user benefits from seeing the relationship.

Use numeric ranges only as starting studies, never universal tokens:

- very small press or hover feedback often lives around a tenth of a second;
- selection, toggle, or compact state changes often tolerate roughly one to two tenths;
- menus, popovers, dialogs, and panels may need somewhat longer when distance and layering matter;
- route or large object transitions can take longer only when continuity earns the time.

Test the actual scale, display, frame rate, input method, and repetition. What feels refined once can feel sluggish on the fiftieth use.

Use easing to communicate physical intent:

- incoming elements often decelerate as they settle;
- exiting elements often accelerate away;
- visible repositioning often needs a coherent ease on both ends;
- constant progress can remain linear;
- springs are seasoning for direct manipulation or playful material, not a default for serious work.

Use stagger only when sequence clarifies reading or relationship. Remove it when the user needs the entire set immediately, when lists are long, or when repeated use turns choreography into latency.

Build a small semantic vocabulary such as surface enter, surface exit, make room, replace rail, menu reveal, object continuity, anchor feedback, and soft collapse. Related movements should share cadence and physical logic without forcing every component onto one identical duration.

## Continuity, Depth, And Direct Manipulation

Use continuity to preserve object identity and spatial memory:

- keep selected objects, cursors, and active markers connected to their source;
- maintain stable edges and regions through expansion or replacement;
- show where inserted, removed, or reordered items belong;
- keep image, canvas, or document motion subordinate to the user's work.

Depth can come from relative scale, layer order, crop, occlusion, surface separation, and differential movement rather than heavy shadow. Use parallax or layered depth only when it preserves content, performs well, and remains comfortable after repetition.

Direct manipulation may justify a light spring, pickup elevation, resistance, or settle because the user is moving an object. Do not transfer that playfulness to unrelated navigation or high-stakes confirmation.

Prototype motion early only when it determines structure: panel versus overlay, swipe versus navigation, card expansion, object-to-detail, drag and reorder, or spatial replacement. Otherwise establish the static system first.

## Push Transitions

Use a push transition when a side surface should become part of the page rather than float above it: inspectors, anchored comments, side sheets, recommendation rails, or shared side regions.

Anchor the surface to its true edge. Reveal inward. Move neighboring content once as part of the same spatial decision. Preserve the important content region and avoid title or canvas jolts, double shifts, late realignment, stacked competing panels, and horizontal overflow.

Decide how narrow viewports change the surface with `$u-frontend-technical-ui-ux`; a push transition that works on desktop may need an overlay or replacement model on mobile.

## Proximity Response

Do not make direct hover the only moment an interface feels alive. On pointer devices, proximity can gently prepare an object before contact through restrained emphasis, orientation, local depth, preview, or shared light behavior.

Use proximity only when it supports intent or scanning. Keep it:

- subtle enough not to distract nearby reading;
- reversible and calm when the pointer leaves;
- localized rather than a page-wide spotlight trick;
- nonessential for understanding or task completion;
- compatible with the keyboard, touch, and reduced-motion paths owned by `$u-frontend-technical-ui-ux`.

Do not automatically add magnetism, halos, tilt, glow, or cursor effects. Choose the smallest response that belongs to the product.

## Motion Craft And Proof

Use this loop:

1. Fix the still frame.
2. Define trigger, intent, start, end, and success.
3. Choose functional, structural, emotional, or restrained combined role.
4. Identify source, destination, anchor, and surface type.
5. Make the smallest motion study that can expose the decision.
6. Inspect it with real density, long content, repeated items, and the actual surrounding layout.
7. Compare normal and reduced-motion intent, desktop and narrow behavior, and pointer and keyboard paths with the technical skill.
8. Refine what feels wrong: timing, distance, easing, delay, direction, layering, state clarity, or the static design itself.

For important transitions, use evidence capable of showing motion: video, screenshot burst, frame sampling, geometry traces, or live browser inspection. A static screenshot cannot prove the absence of flicker, double movement, bad sequencing, or layout jank.

Check that the source edge remains stable, titles and content do not jolt, scroll does not jump, replacement does not blink, imagery is not occluded, and repeated use remains comfortable.

Study references for why their motion works. Combine principles with the product's own structure. Avoid tutorial-copy energy and portfolio-showpiece animation.

## Failure Patterns

Reject motion that:

- delays content or the user's goal;
- repeats forever near reading or data scanning;
- competes with typing, comparison, or direct manipulation;
- hides latency or layout instability;
- replaces clear labels or visible state;
- uses bounce, spring, parallax, stagger, blur, or depth without clarifying a relationship;
- makes every component lift, glow, or drift;
- appears from nowhere or settles in multiple stages;
- causes neighboring content to move twice;
- ignores the product's frequency of use and emotional stakes;
- exists only because the interface otherwise feels generic;
- lacks an intentional reduced-motion counterpart.

When motion feels wrong, first ask whether the static composition or surface model is wrong. Remove motion before adding more machinery.
