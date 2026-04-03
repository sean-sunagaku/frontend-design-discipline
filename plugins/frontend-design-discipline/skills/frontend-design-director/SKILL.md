---
name: frontend-design-director
description: Create a locked design-direction packet before building a visually sensitive landing page, Figma screen, or premium frontend UI. Use when the user wants a strong first impression, wants to avoid generic or "ugly" output, or when quality depends on art direction and reject lists before implementation.
---

# Frontend Design Director

## Overview

Use this skill before building. Its job is to stop weak UI before it exists.

Turn the user's brief into a strict build packet that defines:

1. what the first screen must make someone feel
2. what visual idea each section will own
3. what patterns are forbidden
4. what bar the work must clear before it is considered done

Do not start drawing, coding, or composing screens until this packet exists.

## Core Rule

If the design still depends on explanation after the packet is written, the packet is not ready.

Do not allow:

- generic SaaS split-screen hero
- feature card grid as the first impression
- weak mockup used as a fake visual anchor
- copy-heavy sections that compensate for weak composition
- multiple accent colors or unrelated visual metaphors
- "we can fix it in the review loop" as the primary plan

This skill exists because late recovery is expensive. Bias toward over-defining the visual bar before the first build pass.

## Required Build Packet

Before any build, write these sections in concise form:

### 1. First Impression

One sentence.

- What must someone feel in the first 3 seconds?
- What must this not be mistaken for?

Example:

- `A nocturnal release room, not a generic B2B dashboard.`

### 2. Visual Thesis

One sentence describing mood, material, and energy.

- name the atmosphere
- name the dominant material or surface quality
- name the level of motion or restraint

### 3. Anti-Goals

Write 3 to 7 bullets.

These must be concrete, visual, and easy to reject in review.

Bad:

- `Make it better`

Good:

- `No left-text/right-mockup hero unless the visual side is genuinely dominant`
- `No interchangeable three-card feature row`
- `No decorative gradients standing in for product imagery`

### 4. Section Jobs

Define one job per section.

- Hero
- Support
- Detail
- Final CTA

Each section must have:

- one dominant visual idea
- one primary takeaway
- one reason it exists

### 5. Dominant Visual Plan

For each section, state what the eye lands on first.

If you cannot name the dominant visual in one sentence, the section is too vague.

### 6. Typography and Color Discipline

Lock:

- display type role
- body type role
- typeface count
- accent color count
- contrast strategy
- whether the brand wordmark or product name is the loudest text

Default to two typefaces max and one accent color max unless the brief clearly demands otherwise.

Do not default to a safe generic font pair without intention. State why the chosen type direction fits the product.

Examples:

- `Display type should feel editorial and controlled, not startup-generic.`
- `Body type should disappear into the reading flow and not compete with the hero.`

### 7. Hero Scale Budget

Lock the hero typography before building.

State:

- target line count for the headline on desktop
- target width of the text column
- whether the hero visual or the headline is the louder element
- what must remain comfortably visible in the first viewport besides the headline

Reject plans where:

- the headline becomes the entire composition
- supporting copy and CTA are pushed into a cramped leftover corner
- the brand mark becomes visually negligible next to the headline
- the hero only works because the headline is huge

Default bar:

- desktop headline should usually read in 2 to 4 lines
- the text block should not consume so much height that the CTA cluster feels trapped at the bottom
- the hero must still feel balanced if the headline is reduced by one size step

### 8. Section Text Line Budget

Lock the intended wrapping behavior for the rest of the page before building.

For each section, define the target line count for:

- section eyebrow
- section heading
- supporting copy
- proof points or column titles
- CTA labels

Default bar:

- support/detail section headings should usually land in 1 to 3 lines
- supporting paragraphs should usually land in 1 to 4 lines depending on measure
- proof-point titles should usually stay within 1 to 2 lines
- proof-point body copy should usually stay within 1 to 3 lines
- nav labels and CTA labels should stay on 1 line unless there is a strong reason not to

Reject plans where:

- lower sections only work because narrow columns force awkward 3-line or 4-line headings
- every proof item wraps the same way, creating a repetitive column rhythm
- body copy is long enough that layout density must rescue it
- labels, chips, or CTA text are expected to wrap by default

If a section looks better when the copy is shorter or the measure is wider, treat that as the correct fix, not as optional polish.

### 9. Imagery Strategy

State what kind of visual anchor will carry the page.

- real-looking workspace
- editorial crop
- product surface
- annotated timeline
- photography

If the first screen would still work with no image or no strong visual plane, the plan is weak.

### 10. CTA Stance

Define:

- the main action
- the emotional tone of the CTA
- what the close should feel like

Reject vague CTA language that does not conclude the page.

### 11. Pass Bar

Write 5 to 8 bullets describing what must be true for the work to pass.

These must be visual and observable.

Good:

- `The first viewport cannot be mistaken for a generic task-management SaaS page.`
- `The hero must read as one composition, not two equal columns in negotiation.`
- `Every lower section must have a dominant subject, not a row of similar blocks.`

### 12. Build Instruction

End with a short directive paragraph that a builder can execute without reinterpretation.

This is the handoff to Figma/code work.

## Preflight Review

After writing the packet, review it before building.

This review can happen at any of these design-stage checkpoints:

- raw brief
- first direction notes
- locked build packet
- rough wireframe or low-fidelity section plan

The earlier the review happens, the cheaper the correction.

If subagents are available and the user did not forbid delegation:

- prefer an independent subagent preflight review first
- use `$frontend-preflight-critic` by default
- route to `$frontend-brand-critic` or `$frontend-composition-critic` as a second opinion when the main risk is obvious

If subagents are unavailable, run the same preflight in-thread.

Do not proceed to build until the packet either:

- passes, or
- has only minor polish issues that do not threaten the main impression

## Relationship To Other Skills

- Use this skill before `$review-refine-loop` when the work is visually sensitive.
- Use this skill alongside `$frontend-skill` when the brief calls for a strong landing page or hero-led UI. Compress `$frontend-skill` into the packet instead of jumping straight into composition.
- After a build exists, use the narrow critic skills for targeted review.

## Output Contract

Return the build packet in this order:

1. First Impression
2. Visual Thesis
3. Anti-Goals
4. Section Jobs
5. Dominant Visual Plan
6. Typography and Color Discipline
7. Hero Scale Budget
8. Section Text Line Budget
9. Imagery Strategy
10. CTA Stance
11. Pass Bar
12. Build Instruction

Do not pad it with generic design commentary.
