---
name: user-taste
description: >-
  Define, refine, and apply a user-authored personal taste layer for visual
  direction, UI polish, brand surfaces, typography, imagery, motion, creative
  production, and critique. Use when the user explicitly asks to personalize
  or update their taste profile, or after customization when visual work
  should reflect it. This bundled copy starts unconfigured: during setup,
  invite open-ended reflection, ask targeted follow-ups, and replace the
  placeholders with distilled principles; do not apply it as personal taste
  until the user confirms the profile.
---

# User Taste

Status: Unconfigured

This is a private personalization template, not a generic design doctrine. It supports two modes:

- **Setup mode:** Help the user articulate their taste and replace the placeholders below.
- **Application mode:** Apply the profile only after its status is `Configured`.

If the profile is unconfigured and the user did not ask to personalize it, do not infer personal preferences. Rely on the project's accepted creative direction, explicit user instructions, product context, and the applicable visual or technical skill.

## Setup Mode

Begin with one open invitation:

> Tell me about your taste in whatever form feels natural—you can ramble. What do you repeatedly value or reject, and why? Think beyond visual design: products, architecture, books, tools, film, fashion, music, games, spaces, or experiences can all be useful if you explain what quality carries over. Examples and counterexamples help, but the reasoning matters more than the names.

If the user has already supplied useful material, do not make them repeat it. Let the first response be broad and associative. Then ask only the smallest useful set of follow-ups, usually one to three at a time. Explore whichever areas remain unclear:

- what feels excellent, cheap, generic, excessive, sterile, unfinished, or dishonest;
- the values or philosophy beneath those reactions;
- admired and disliked examples, including what should and should not transfer from them;
- analogies from other interests and the specific quality each analogy represents;
- meaningful tensions such as restraint versus expressiveness, warmth versus precision, novelty versus familiarity, density versus breathing room, or polish versus character;
- preferences that change by product, audience, medium, or task;
- the standard that separates merely acceptable work from work that feels genuinely cared for.

Do not force every topic into the conversation. Probe vague adjectives with concrete comparisons or “why” questions. Welcome uncertainty and contradiction; they often reveal context-dependent judgment rather than inconsistency.

### Distill And Save

Turn the conversation into guidance another agent can use:

1. Separate durable principles, contextual preferences, hard dislikes, useful examples, and unresolved questions.
2. Translate “I like this” into the underlying quality. Keep an example only when it clarifies that quality; never copy its surface style by default.
3. Write concise, operational guidance in the user's meaning and voice. Preserve meaningful tensions instead of flattening them into generic adjectives.
4. Show the user a compact synthesis and ask them to correct material inaccuracies or missing priorities.
5. Once the user confirms the synthesis or explicitly delegates final judgment, replace the placeholders in `Personal Taste Profile` and change the status to `Configured`. Preserve the setup instructions.
6. Ask whether the configured skill may be invoked automatically. Keep `allow_implicit_invocation: false` unless the user explicitly wants that behavior.

If the skill source cannot be edited, return the complete ready-to-paste profile and identify the `SKILL.md` that should receive it. Do not retain private anecdotes or identifying details unless they are necessary to apply the taste and the user wants them included.

## Application Mode

Use a configured profile as a judgment layer, not a rigid style recipe. The current request, product truth, audience, medium, constraints, and accepted project direction remain higher authority. Apply the reasons behind examples, not their palette, typography, layout, effects, or fashionable surface cues.

Do not invent preferences that the profile does not support. When a missing preference would materially change the result, ask the user; otherwise make a context-led choice and identify it as such.

## Personal Taste Profile

### Quality Bar

_[What should finished, high-quality work feel like, and what separates it from merely acceptable work?]_

### Principles And Philosophy

_[Which durable values should guide repeated judgments, and why do they matter?]_

### Preferences And Aversions

_[What qualities tend to work or fail? Include context, priorities, and hard dislikes rather than a generic list of adjectives.]_

### Composition, Imagery, And Typography

_[How should space, hierarchy, proportion, imagery, type, rhythm, density, and optical detail be judged?]_

### Motion And Interaction

_[When should an experience move or respond, what should that communicate, and what feels excessive or lifeless?]_

### Examples And Transferable Qualities

_[Which examples or cross-domain analogies are useful, what quality does each demonstrate, and what should not be copied literally?]_

### Review Questions

_[Which questions should an agent ask before approving work in this user's name?]_
