---
name: frontend-preflight-critic
description: Review a proposed UI direction, build packet, or first-view plan before any screen is built. Use when you want to catch generic, weak, or contradictory art direction early and block bad UI before implementation.
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
  - hero scale budget
  - section line budget
  - CTA stance
- the output must follow the skill's PASS/FAIL contract with remaining issues only

This means a short parent prompt such as:

- `Use $frontend-preflight-critic and review the current build packet in this thread.`
- `Run preflight on this Studio Pulse direction packet before build.`

should already be enough.

## What To Check

Inspect these dimensions:

1. first impression strength
2. visual thesis clarity
3. genericity risk
4. strength of the dominant visual plan
5. typography direction and font fit
6. hero scale budget
7. section text line budget
8. section-job discipline
9. anti-goal usefulness
10. CTA stance clarity

Mark it NG if:

- the first viewport could still become a generic SaaS page
- the plan does not name a strong visual anchor
- the font direction is generic, unintentional, or unsupported by the intended mood
- the hero plan would likely require an oversized headline to feel important
- the headline would overpower the brand mark, supporting copy, or CTA cluster
- the lower sections have no explicit line budget and will likely collapse into awkward wrapped columns
- the planned headings or proof-point titles are likely to overwrap in narrow containers
- multiple sections sound interchangeable
- anti-goals are too vague to reject bad output
- the plan leans on copy to carry the whole page
- the CTA sounds like filler rather than a conclusion

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

## Review Discipline

- Judge the plan as if rework after build were expensive.
- Be strict about genericity.
- If a section cannot be pictured clearly, treat that as a real defect.
- Prefer rejecting a weak direction before implementation over rescuing it later.
- Treat weak font rationale and runaway hero scale as first-order design defects, not polish.
- Treat uncontrolled wrapping and missing line budgets as structural defects, not typography cleanup.

## Subagent Guardrail

When this skill is used in a delegated reviewer thread:

- do not discuss tool availability, delegation, orchestration, or process
- do not explain whether subagents are possible
- do not answer with a meta refusal
- do not ask the parent thread to decide whether build can start
- assume the independent-reviewer role even when the parent prompt is short
- use the default focus list unless the parent explicitly changes it
- return the review output contract directly

If the packet is incomplete, review the available material anyway and call missing pieces a defect.

## Good Findings

- `P1 The hero direction still sounds like text plus a mockup, which will likely collapse into a generic split-screen SaaS layout. Replace it with one dominant visual plane and make the text column secondary to that plane.`
- `P1 The anti-goals do not forbid any concrete failure modes, so the builder still has room to produce a normal feature-card page. Add explicit rejections for card grids, weak hero mockups, and filler dashboard patterns.`
- `P2 The CTA stance is still generic and does not tell the builder how the page should close emotionally. Define whether the close should feel calm, decisive, exclusive, or invitational.`
