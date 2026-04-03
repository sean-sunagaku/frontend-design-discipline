---
name: frontend-preflight-critic
description: Review a proposed UI direction, build packet, or first-view plan before any screen is built. Use when you want to catch generic, weak, or contradictory art direction early and block bad UI before implementation across landing pages, app views, dashboards, and feature screens.
---

# Frontend Preflight Critic

## Overview

Use this skill before the first draft exists.

You are reviewing the proposed direction, not the finished pixels. The goal is to reject weak plans early enough that they never become the artifact.

This skill is the build gate for visually sensitive work. If the direction is not ready, fail it before Figma or frontend implementation begins.

Valid inputs include:

- the raw user brief
- a proposed first-view plan
- a build packet
- a section breakdown
- a wireframe or low-fidelity direction note

Use this skill for application UI as well as landing pages. The same preflight gate should apply to dashboards, editors, workflows, settings, and admin surfaces before implementation begins.

## Default Reviewer Assumptions

Do not require the parent prompt to restate the full review frame every time.

Unless the user explicitly narrows or overrides the scope, assume all of the following by default:

- you are the independent reviewer, not the builder
- the review target is the current build packet or proposed direction shown in the thread
- the focus is:
  - first impression strength
  - generic SaaS risk
  - dominant visual plan
  - structural layout discipline
  - font direction
  - opening-zone scale budget
  - zone line budget
  - width and measure strategy
  - spacing budget and text cluster structure
  - structural audit discipline and section completion criteria
  - structural audit routing to `$frontend-structure-auditor` when tree-level structure is fragile
  - text placement discipline and meaningful line-break handling
  - repeated-row rhythm, divider quietness, and focal emphasis inside sequences
  - primary action stance
- the output must follow the skill's PASS/FAIL contract with remaining issues only

This means a short parent prompt such as:

- `Use $frontend-preflight-critic and review the current build packet in this thread.`
- `Run preflight on this Studio Pulse direction packet before build.`

should already be enough.

## Validation Integrity

This skill only counts when an actual review is performed.

- do not fabricate a preflight result before the review happens
- do not write a synthetic `PASS` or `FAIL` block just to move the workflow forward
- do not create a fake critic transcript with shell output, temp files, or placeholder formatting and present it as the review
- if you are the same thread that authored the packet and no independent reviewer has actually run yet, do not call the result an independent preflight review
- same-thread fallback is not valid for this skill's build-gate verdict
- if an independent reviewer subagent cannot run, report that the build gate is blocked instead of substituting a local review

Only a real critic pass may produce the build-gate verdict.

## What To Check

Inspect these dimensions:

1. first impression strength
2. visual thesis clarity
3. genericity risk
4. strength of the dominant visual plan
5. structural layout discipline
6. typography direction and font fit
7. opening-zone scale budget
8. zone text line budget
9. width and measure strategy
10. spacing budget and text cluster readiness
11. bounded text fit and safe padding
12. zone-job discipline
13. anti-goal usefulness
14. primary action stance clarity
15. review capture plan for section- and cluster-level inspection

Mark it NG if:

- the first viewport could still become a generic SaaS page
- the plan does not name a strong visual anchor
- the packet never says how the major zones will be structurally built
- the likely build path is loose absolute placement instead of frames, wrappers, stacks, or semantic containers
- primary reading content has no declared parent structure
- the likely build path begins with free-placed text and rectangles instead of section frames, rows, cards, strips, rails, or semantic clusters
- a board-like or surface-like zone is described visually but not decomposed into structured children such as rows, cards, notes, rails, or copy groups
- the packet never states the structural audit rules for section completion
- the packet never says which dedicated reviewer will audit tree-level structure when it is fragile
- the packet does not require child bounds to stay within parent bounds after each section
- the packet allows a section to be considered complete even if overflow still exists
- the packet does not require structural audit results before screenshot review
- the packet does not require the final handoff to include both the design and the audit result
- the packet allows bare text nodes instead of explicit frames or clusters
- the packet relies on manual line breaks or awkward rescue breaks for headings, labels, or helper lines
- the font direction is generic, unintentional, or unsupported by the intended mood
- the primary opening-zone plan would likely require an oversized headline to feel important
- the headline would overpower the brand mark, supporting copy, or CTA cluster
- the packet does not reserve a clear left-side inset for the opening copy cluster, so the hero could feel pinned to the edge
- the opening copy cluster is likely to sit too close to the dominant visual plane, rail, or surface boundary even if it does not overlap
- the secondary zones have no explicit line budget and will likely collapse into awkward wrapped columns
- the packet does not say which zones should widen and which should stay narrow
- a text-heavy or working zone is over-constrained to a narrow measure even though the surface clearly wants more horizontal room
- the packet does not say which text-heavy areas must be built as one cluster rather than as separate text placements
- repeated steps, rails, proof rows, or numbered sequences do not define one shared rhythm for number, title, and body starts
- the packet leaves title columns too wide in repeated rows and gives the body no room to breathe
- the packet does not say whether one row should hold slightly more emphasis, so repeated rows may flatten into visual monotony
- divider lines in repeated rows are likely to read louder than the content itself
- heading/body/action spacing is still implied instead of locked as a spacing budget
- the packet never states where the quiet band or breathing corridor should sit between side-by-side masses
- the likely build path depends on manual line breaks in headings, labels, or buttons instead of healthier width, measure, or copy edits
- the planned headings or proof-point titles are likely to overwrap in narrow containers
- bounded copy areas such as CTA panels, proof items, or rail notes are likely to touch edges or break out of their frames
- captions, helper lines, or CTA copy are likely to become stranded because no cluster structure or reserved clearance is defined
- the likely result is not literal overlap but text and objects that will read as kissing, touching, or visually colliding
- the packet treats structure as an implementation afterthought rather than part of the design direction
- the packet allows primary content to float independently when those elements should clearly live inside a frame, row, card, list item, strip, or text cluster
- secondary zones would need tiny late-stage type reductions just to stay inside their boxes
- the direction has no zone-level screenshot or crop review plan, so overlap and edge-touch risk would be discovered too late
- multiple zones sound interchangeable
- anti-goals are too vague to reject bad output
- the plan leans on copy to carry the whole page
- the primary action sounds like filler rather than a conclusion or next step

## Output Contract

Return:

1. `PASS` or `FAIL`
2. one sentence describing whether the direction is strong enough to build from
3. remaining `P1` / `P2` / `P3` issues only

Each issue should say:

- what is missing or risky
- why that would produce weak UI
- what kind of design-direction change would fix it

If the direction is not clearly ready, prefer `FAIL`. Do not soften a blocking direction problem into a vague polish note.

Return the review directly. Do not wrap it in setup chatter, capability disclaimers, or process notes.

Do not emit `PASS` unless you have actually reviewed the current packet in this run.
Do not emit the build-gate verdict from the packet-authoring thread.

## Review Discipline

- Judge the plan as if rework after build were expensive.
- Be strict about genericity.
- If a zone cannot be pictured clearly, treat that as a real defect.
- Prefer rejecting a weak direction before implementation over rescuing it later.
- Treat weak font rationale and runaway opening-zone scale as first-order design defects, not polish.
- Treat missing structural layout discipline as a first-order design defect, not as a later implementation task.
- Treat missing parent-child layout structure as a first-order design defect, not as a cosmetic implementation choice.
- Treat plans that begin from floating text and rectangles instead of frames, rows, cards, and clusters as structurally weak.
- Treat missing structural audit rules, section completion criteria, or overflow gates as first-order design defects.
- Treat missing routing to a dedicated structural reviewer as a first-order defect when the build is tree-fragile.
- Treat bare text nodes and accidental line endings as first-order defects when the packet still expects a stable UI build.
- Treat unresolved repeated-row rhythm as a structural defect, not as polish.
- Treat a plan that allows screenshots before structural audit as structurally incomplete.
- Treat any section with overflow as incomplete until the overflow is resolved.
- Treat uncontrolled wrapping and missing line budgets as structural defects, not typography cleanup.
- Treat underused width and obviously over-constrained measures as structural defects, not as polish.
- Treat text-fit risk in secondary zones as a structural defect, not as last-minute cleanup in Figma.
- Treat missing text-cluster structure and missing section-level inspection plans as structural defects, not optional QA.
- Treat missing breathing corridors between side-by-side masses as a structural defect, not as taste.
- Treat a cramped opening copy inset as a structural defect, not as subjective hero polish.
- Treat forced manual line breaks as a structural defect when they are being used to rescue a weak measure.

## Subagent Guardrail

When this skill is used in a delegated reviewer thread:

- do not discuss tool availability, delegation, orchestration, or process
- do not explain whether subagents are possible
- do not answer with a meta refusal
- do not ask the parent thread to decide whether build can start
- assume the independent-reviewer role even when the parent prompt is short
- use the default focus list unless the parent explicitly changes it
- return the review output contract directly

If you did not actually review the packet, return nothing yet and review it first. Never simulate a completed verdict.

If the packet is incomplete, review the available material anyway and call missing pieces a defect.

## Good Findings

- `P1 The opening direction still sounds like text plus a mockup, which will likely collapse into a generic split-screen SaaS layout. Replace it with one dominant visual plane and make the text column secondary to that plane.`
- `P1 The anti-goals do not forbid any concrete failure modes, so the builder still has room to produce a normal feature-card page. Add explicit rejections for card grids, weak hero mockups, and filler dashboard patterns.`
- `P2 The primary action stance is still generic and does not tell the builder how the flow should close emotionally. Define whether the commit should feel calm, decisive, exclusive, or invitational.`
- `P2 The packet still assumes the closing copy and CTA can be placed ad hoc inside the final zone. Define one CTA cluster, its spacing budget, and the screenshot crops that will be used to verify it after the first draft.`
- `P2 The support zone names the left and right masses but never reserves a quiet band between them, so the likely outcome is visual kissing rather than calm separation. Define the breathing corridor explicitly and protect it in the crop review plan.`
- `P2 The opening zone names the text column and visual plane, but it never reserves a real left inset for the copy cluster. Define the minimum inset and the crop that will verify the hero does not feel edge-hugging.`
