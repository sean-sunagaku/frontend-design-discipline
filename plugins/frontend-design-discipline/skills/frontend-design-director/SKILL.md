---
name: frontend-design-director
description: Create a locked design-direction packet before building a visually sensitive landing page, app surface, dashboard, feature view, Figma screen, or premium frontend UI. Use when the user wants a strong first impression, wants to avoid generic or "ugly" output, or when quality depends on art direction and reject lists before implementation.
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

This skill is not only for landing pages. Use the same packet discipline for:

- app home screens
- dashboards
- workflow or task views
- editors and detail views
- settings or admin surfaces
- multi-panel product screens

## Core Rule

If the design still depends on explanation after the packet is written, the packet is not ready.

If the user explicitly names companion tools or skills for the task, treat them as required parts of the workflow, not as optional hints.

Examples:

- if the user names `Figma`, you must actually use Figma for the build phase
- if the user names `Frontend Design Discipline`, you must actually run the design-direction and review flow
- if the user names `Frontend Skill`, you must actually use it to strengthen the visual thesis and art direction

Do not silently collapse these into one another. If one required companion is unavailable, say so clearly instead of pretending the others cover it.

Do not allow:

- generic SaaS split-screen hero
- feature card grid as the first impression
- weak mockup used as a fake visual anchor
- copy-heavy sections that compensate for weak composition
- multiple accent colors or unrelated visual metaphors
- "we can fix it in the review loop" as the primary plan

This skill exists because late recovery is expensive. Bias toward over-defining the visual bar before the first build pass.

Structure is part of the bar, not a later implementation detail.

For Figma, HTML, and frontend builds, default to real layout structure first:

- auto layout, stacks, grids, and nested frames in Figma
- semantic sections, lists, flex, and grid in HTML/CSS
- explicit parent-child hierarchy for every major zone and text cluster
- every meaningful element should belong to a real parent frame, wrapper, row, column, card, list item, strip, note group, or text cluster rather than floating alone

Do not treat loose absolute positioning as the default build method.
Absolute placement is acceptable only for decorative layers, controlled overlays, or intentionally freeform hero art where the primary reading content still lives inside a stable structure.
For primary content, default to section -> group frame -> row or column -> card, note group, or text cluster.

Although many examples below use landing-page language, the same discipline applies to any high-visibility surface:

- a homepage or marketing page
- an app home or dashboard
- a feature screen or workflow view
- a settings, reporting, or management surface

When the artifact is not a landing page, translate the examples rather than ignoring the rule. A `hero` usually maps to the primary opening zone, and `final CTA` usually maps to the main commit or next-step area.

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

### 4. Surface Mapping

Before defining jobs, map the artifact into major surface zones.

For landing pages, a common mapping is:

- Hero
- Support
- Detail
- Final CTA

For application UI, use the closest equivalent:

- primary opening or identity zone
- main working zone
- supporting or contextual zone
- focused detail or inspection zone
- commit, save, confirm, or next-step zone

Examples:

- dashboard: opening identity strip, overview workspace, active thread/focus panel, primary action area
- workflow screen: entry context, main task canvas, side context, commit/continue area
- settings page: page identity, grouped controls, risky-action area, save/apply zone
- editor/detail view: object identity, main canvas, inspector/context rail, save/publish zone

The names do not matter. The dominance and job of each zone do.

### 5. Zone Jobs

Define one job per major zone.

For landing pages, this often means:

- Hero
- Support
- Detail
- Final CTA

For app screens or product surfaces, map the same structure to:

- primary opening zone
- secondary or supporting zones
- focused detail zone
- closing action or commit zone

Each zone must have:

- one dominant visual idea
- one primary takeaway
- one reason it exists

### 6. Dominant Visual Plan

For each major zone, state what the eye lands on first.

If you cannot name the dominant visual in one sentence, the zone is too vague.

### 7. Structural Layout Discipline

Define how the artifact will be structurally built, not just how it should look.

For every major zone, decide the structural parent and the local layout model:

- stack / auto layout
- grid
- split layout with a protected breathing corridor
- freeform art plane with structured text overlay

For Figma, default to:

- frames instead of loose groups for meaningful regions
- nested frames that reflect zone -> cluster -> element hierarchy
- auto layout for text clusters, CTA groups, note stacks, proof items, and repeated patterns
- absolute positioning only for decoration, annotation accents, or deliberate hero artwork
- section -> group frame -> row or column frame -> text cluster is the default build order
- a board or surface should still be decomposed into structured children such as timeline rows, cards, strips, rails, notes, and copy clusters
- text should not be scattered as standalone layers when it could belong to one card, row, note group, strip, or heading cluster

For HTML/frontend, default to:

- semantic containers such as `header`, `main`, `section`, `aside`, `nav`, `footer`
- flex or grid for primary layout
- stable wrappers for text clusters and action groups
- absolute positioning only for decorative or controlled overlay elements
- rows, columns, cards, strips, lists, and annotation groups should be explicit wrappers rather than visually implied spacing
- text nodes should belong to semantic clusters instead of being sprinkled directly into the page root

Reject plans where:

- the builder could interpret the screen as "place things until it looks right"
- important reading content has no clear parent container
- text layers are expected to float independently in open space
- a CTA, caption, or helper line has no structural cluster
- a side-by-side zone has no declared parent layout and no protected corridor
- the likely Figma build would start by dropping rectangles and text on the canvas before section frames exist
- a board-like zone is described as a surface but not decomposed into rows, cards, strips, rails, notes, or clusters
- multiple primary elements in the same zone would need to overlap because no structural rows, cards, or groups were defined
- the likely HTML/frontend build would rely on free-positioned blocks instead of a stable section / row / cluster hierarchy

If the layout would become more stable by adding one more structural parent frame or wrapper, do that early instead of fixing drift later.
If two or more elements can be expressed as one stable cluster, card, row, or note group, prefer that structure over separate placements.

### 8. Typography and Color Discipline

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

### 9. Opening-Zone Scale Budget

Lock the scale of the primary opening zone before building.

State:

- target line count for the headline on desktop
- target width of the text column
- whether the opening visual or the headline is the louder element
- what must remain comfortably visible in the first view besides the headline

Reject plans where:

- the headline becomes the entire composition
- supporting copy and CTA are pushed into a cramped leftover corner
- the brand mark becomes visually negligible next to the headline
- the opening zone only works because the headline is huge

Default bar:

- desktop headline should usually read in 2 to 4 lines
- the text block should not consume so much height that the CTA cluster feels trapped at the bottom
- the opening zone must still feel balanced if the headline is reduced by one size step

### 10. Zone Text Line Budget

Lock the intended wrapping behavior for the rest of the surface before building.

For each major zone, define the target line count for:

- zone eyebrow
- zone heading
- supporting copy
- proof points or column titles
- CTA labels

Default bar:

- secondary or detail zone headings should usually land in 1 to 3 lines
- supporting paragraphs should usually land in 1 to 4 lines depending on measure
- proof-point titles should usually stay within 1 to 2 lines
- proof-point body copy should usually stay within 1 to 3 lines
- nav labels and CTA labels should stay on 1 line unless there is a strong reason not to

Reject plans where:

- secondary zones only work because narrow columns force awkward 3-line or 4-line headings
- every proof item wraps the same way, creating a repetitive column rhythm
- body copy is long enough that layout density must rescue it
- labels, chips, or CTA text are expected to wrap by default
- the plan assumes manual line breaks will be inserted to rescue headings, labels, or buttons
- zone titles, labels, or helper lines are likely to collide with frames, rails, or boxed areas
- any bounded text area only works if the text sits right on the edge of its container

If a zone looks better when the copy is shorter or the measure is wider, treat that as the correct fix, not as optional polish.

### 11. Text Fit Discipline

For every bounded text area, also lock fit rules before building.

This includes:

- CTA panels
- support proof items
- detail thread notes
- pills, labels, and badges
- boxed or framed supporting text

Default bar:

- text should keep visible breathing room on all sides
- no important label should touch or nearly touch a frame edge
- no section should depend on three-line mini paragraphs inside small cards or boxes
- secondary zones should feel quieter than the opening zone, not more cramped than the opening zone

Reject plans where:

- text is likely to appear visually outside a box, frame, or panel
- the container only works at one exact line break
- the layout depends on shrinking text too late in Figma to make it fit
- secondary zones inherit the opening zone's drama as oversized text instead of settled rhythm

### 12. Spacing Budget

For every major zone, lock the minimum spacing relationships between text clusters before building.

At minimum, define:

- heading to body gap
- body to primary action gap
- text cluster to nearby object clearance
- safe padding inside bounded copy areas
- breathing corridor between major side-by-side masses

Prefer structural spacing over manual cleanup.

Reject plans where:

- the heading, body, caption, and action are expected to be placed one by one by coordinates
- captions or helper lines are expected to live in leftover space
- the zone only works if text is nudged late in Figma
- the closest visual object can drift into the text area with no reserved clearance
- the design relies on a mathematically small gap that will read as touching, kissing, or visually colliding
- side-by-side text and visual masses have no intentional quiet band between them

If a zone contains a closing cluster, note, proof item, or CTA stack, define it as one cluster with one spacing system rather than as separate floating text layers.

### 13. Width and Measure Strategy

For every major zone, decide whether it should stay narrow, widen, or span the surface more aggressively.

State:

- which zones are intentionally narrow
- which zones should expand horizontally
- the target text measure for long-form reading areas
- the minimum usable width for working, proof, or visual zones

Reject plans where:

- secondary or working zones inherit the opening text measure without reason
- a zone is forced into 3-line or 4-line wrapping simply because it was never allowed to widen
- the page leaves obvious unused horizontal space while text-heavy areas become vertically cramped
- proof objects, rails, or cards collide with copy because the layout under-allocates width

If widening a zone would clearly solve wrapping, overlap, or visual tension, choose widening first instead of shrinking text or stacking more rows.
If a side-by-side zone needs calm, reserve an explicit breathing corridor instead of trusting incidental whitespace.

### 14. Text Cluster Structure

Call out which text-heavy areas must be built as structured clusters rather than loose text placements.

Examples:

- closing CTA cluster
- support copy cluster
- detail copy cluster
- rail note cluster
- inspector note cluster

Default bar:

- prefer auto-layout or equivalent stack structure for text groups
- keep captions, helper text, and actions attached to their parent copy cluster
- reserve space for nearby cards, notes, rails, or screenshots instead of hoping text will miss them
- keep the cluster inside an explicit parent frame, wrapper, or semantic container
- merge elements into one structural cluster whenever they are meant to be read as one unit

Reject plans where:

- a text-heavy zone depends on absolute x/y nudging for routine reading content
- a CTA, caption, or helper line looks likely to become stranded
- the design assumes overlap will be caught only during final polish
- a copy cluster and nearby object are separated only by a gap so small it will likely read as visually touching
- the cluster has no real parent wrapper and only appears grouped because elements were placed near each other
- a heading, label, or button likely depends on a forced manual line break instead of a healthier measure or wider zone

### 15. Review Capture Plan

Before build, define how the artifact will be checked after the first draft.

Default bar:

- take one full-artifact screenshot for overall composition
- take one screenshot per major zone
- take additional screenshots for text-heavy or bounded clusters

Examples of cluster-level crops:

- hero text column
- support copy plus nearby proof object
- detail copy cluster versus decision thread
- final CTA closing cluster

Do not rely on one full-page screenshot for signoff. If overlap, clipping, edge touch, or cramped spacing would only be visible in a section crop, plan to review that crop explicitly.
When the design uses side-by-side masses, plan at least one crop that checks whether a real breathing corridor exists between them.

### 16. Surface/Imagery Strategy

State what kind of visual anchor will carry the artifact.

- real-looking workspace
- editorial crop
- product surface
- annotated timeline
- photography
- data surface
- tool canvas
- focused inspector

If the opening zone would still work with no image or no strong visual plane, the plan is weak.

For app UI, this can be the main workspace material, dominant module, or focused object rather than an actual image.

### 17. Primary Action Stance

Define:

- the main action or commit point
- the emotional tone of that action
- what the final commit should feel like

Reject vague action language that does not conclude the flow or clarify the next step.

### 18. Pass Bar

Write 5 to 8 bullets describing what must be true for the work to pass.

These must be visual and observable.

Good:

- `The first viewport cannot be mistaken for a generic task-management SaaS page.`
- `The opening zone must read as one composition, not two equal columns in negotiation.`
- `Every secondary zone must have a dominant subject, not a row of similar blocks.`
- `The working zone must reveal what the product lets you do, not just what it says.`
- `The commit zone must feel deliberate, not like a stray button.`
- `No text cluster may overlap, visually collide with, or nearly touch a nearby object in section-level review.`
- `Primary reading content must live inside stable structural containers, not loose absolute placements.`

### 19. Build Instruction

End with a short directive paragraph that a builder can execute without reinterpretation.

This is the handoff to Figma/code work.

## Preflight Review

After writing the packet, review it before building.

This review can happen at any of these design-stage checkpoints:

- raw brief
- first direction notes
- locked build packet
- rough wireframe or low-fidelity zone plan

The earlier the review happens, the cheaper the correction.

If subagents are available and the user did not forbid delegation:

- the first build-readiness verdict must come from an independent reviewer subagent, not from the same thread that authored the packet
- use `$frontend-preflight-critic` as the default first reviewer
- pass the packet and bar, not your own conclusion about whether it already passes
- wait for a clear `PASS` or `FAIL` before creating a Figma file or starting visual build work
- if it returns `FAIL`, revise the packet locally and run the preflight again
- route to `$frontend-brand-critic` or `$frontend-composition-critic` as a second opinion only when the main risk is obvious or still unresolved after preflight

If an independent reviewer subagent cannot run, stop and report that the build gate is blocked. Do not substitute a same-thread preflight.

Do not say "the packet is build-ready" from the same pass that authored the packet unless you have already checked that delegation is unavailable or disallowed in the current session.
Do not manufacture a `PASS` block yourself just to satisfy the gate. The gate is satisfied only by an actual critic pass on the current packet.
Same-thread fallback is invalid for this gate. If independence cannot be obtained, the workflow must pause rather than pretending the gate passed.

Do not proceed to build until the packet either:

- passes, or
- has only minor polish issues that do not threaten the main impression

In practice, the safe sequence is:

1. write the packet
2. send it to an independent `$frontend-preflight-critic` reviewer
3. fix the packet if needed
4. only then start Figma or frontend build work

Recommended delegated reviewer frame:

```text
Use the skill /absolute/path/to/SKILL.md.

You are the independent reviewer subagent for this task.
Do not discuss tool availability, delegation, orchestration, or process.
Review the current build packet shown in this thread.

Focus on:
- first impression strength
- generic SaaS risk
- dominant visual plan
- font direction
- hero scale budget
- section line budget
- CTA stance

Return exactly:
1. PASS or FAIL
2. one-sentence verdict
3. remaining P1/P2/P3 issues only
```

In normal use, the parent prompt can stay much shorter than this. A simple handoff such as `Use $frontend-preflight-critic and review the current build packet in this thread before build.` should be sufficient because the reviewer defaults live in the preflight skill itself.

## Relationship To Other Skills

- Use this skill before `$review-refine-loop` when the work is visually sensitive.
- Use this skill alongside `$frontend-skill` when the brief calls for a strong landing page, opening surface, or premium product UI. Compress `$frontend-skill` into the packet instead of jumping straight into composition.
- After a build exists, use the narrow critic skills for targeted review.

If the user explicitly named `$frontend-skill`, that is mandatory, not optional. Use it during packet formation to sharpen the visual thesis, anti-goals, and dominant visual plan rather than skipping it or replacing it with this skill alone.

If the user explicitly named `Figma`, building in Figma is mandatory, not optional. Do not stop at packet generation or review-only output.

## Output Contract

Return the build packet in this order:

1. First Impression
2. Visual Thesis
3. Anti-Goals
4. Surface Mapping
5. Zone Jobs
6. Dominant Visual Plan
7. Typography and Color Discipline
8. Opening-Zone Scale Budget
9. Zone Text Line Budget
10. Text Fit Discipline
11. Surface/Imagery Strategy
12. Primary Action Stance
13. Pass Bar
14. Build Instruction

Do not pad it with generic design commentary.
