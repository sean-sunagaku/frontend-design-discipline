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
  - font direction
  - opening-zone scale budget
  - zone line budget
  - width and measure strategy
  - spacing budget and text cluster structure
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
5. typography direction and font fit
6. opening-zone scale budget
7. zone text line budget
8. width and measure strategy
9. spacing budget and text cluster readiness
10. bounded text fit and safe padding
11. zone-job discipline
12. anti-goal usefulness
13. primary action stance clarity
14. review capture plan for section- and cluster-level inspection

Mark it NG if:

- the first viewport could still become a generic SaaS page
- the plan does not name a strong visual anchor
- the font direction is generic, unintentional, or unsupported by the intended mood
- the primary opening-zone plan would likely require an oversized headline to feel important
- the headline would overpower the brand mark, supporting copy, or CTA cluster
- the secondary zones have no explicit line budget and will likely collapse into awkward wrapped columns
- the packet does not say which zones should widen and which should stay narrow
- a text-heavy or working zone is over-constrained to a narrow measure even though the surface clearly wants more horizontal room
- the packet does not say which text-heavy areas must be built as one cluster rather than as separate text placements
- heading/body/action spacing is still implied instead of locked as a spacing budget
- the packet never states where the quiet band or breathing corridor should sit between side-by-side masses
- the planned headings or proof-point titles are likely to overwrap in narrow containers
- bounded copy areas such as CTA panels, proof items, or rail notes are likely to touch edges or break out of their frames
- captions, helper lines, or CTA copy are likely to become stranded because no cluster structure or reserved clearance is defined
- the likely result is not literal overlap but text and objects that will read as kissing, touching, or visually colliding
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
- Treat uncontrolled wrapping and missing line budgets as structural defects, not typography cleanup.
- Treat underused width and obviously over-constrained measures as structural defects, not as polish.
- Treat text-fit risk in secondary zones as a structural defect, not as last-minute cleanup in Figma.
- Treat missing text-cluster structure and missing section-level inspection plans as structural defects, not optional QA.
- Treat missing breathing corridors between side-by-side masses as a structural defect, not as taste.

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
