---
name: frontend-composition-critic
description: Review a frontend screen, landing page, dashboard, workflow view, app UI, mock, or Figma frame for composition, hierarchy, balance, and zone structure. Use when the user wants an independent design critic focused on whether the main subject is obvious, whether layout reads directionally instead of as generic cards or columns, or whether visual weight, spacing, and primary action placement feel resolved.
---

# Frontend Composition Critic

## Overview

Use this skill as a reviewer, not a builder. Inspect the artifact, decide whether the composition works, and return only the issues that still matter.

Prefer screenshots or direct visual artifacts over descriptions. If the work is code, inspect the rendered result when possible.

If no artifact exists yet, review the proposed first-view composition and zone plan. If the plan would likely collapse into a generic split-screen or card-led layout, fail it before build.

## What To Check

This skill can be used in two modes:

- artifact review: judge the current layout or screen
- direction review: judge the proposed opening composition, zone flow, or first-view plan before build

In direction review mode, fail if the builder could still reasonably produce a generic split-screen or card-led page from the plan.

Focus on these questions:

1. Is the main subject obvious in one glance?
2. Does the artifact have one dominant idea per major zone?
3. Does the layout read as composition rather than a row of interchangeable cards?
4. Does visual weight feel balanced left-to-right and top-to-bottom?
5. Does the primary action sit in a clear hierarchy?

Mark it NG if any of these patterns appear:

- a generic card grid as the first impression
- side-by-side blocks that behave like comparison columns without intent
- decorative treatment louder than the message
- an opening headline so large that it crushes supporting copy, CTA, or the visual anchor
- secondary zones whose wrapped headings create interchangeable column blocks
- secondary zones whose boxed items become cramped text containers rather than calm compositional units
- zone titles or action panels that visually break their intended frame because the type block is too tall or too wide
- zones that feel locally styled but globally uncomposed
- obvious imbalance, drifting alignment, accidental emptiness, or crowded edges
- the proposed opening zone does not clearly name one dominant visual plane

## Output Contract

Return:

1. `PASS` or `FAIL`
2. a one-sentence verdict
3. remaining issues only, ordered as `P1`, `P2`, `P3`

Each issue must state:

- what is wrong
- why it matters for composition
- what kind of change would fix it

If it passes, say why it passes in one short paragraph and optionally include one polish suggestion.

## Review Discipline

- Default to 1 to 5 issues.
- Prefer structural observations over style trivia.
- Do not praise and critique in the same bullet.
- Do not say "a bit weak" without naming the broken hierarchy.

## Subagent Use

When used through a subagent, explicitly instruct the subagent to read this skill.

Recommended prompt shape:

- `Use $frontend-composition-critic at /absolute/path/to/SKILL.md and review this artifact for hierarchy, composition, and visual balance. Return only PASS/FAIL and remaining P1/P2/P3 issues.`
- `Use $frontend-composition-critic at /absolute/path/to/SKILL.md and review this proposed first-view plan for hierarchy, composition, and visual balance before build. Return only PASS/FAIL and remaining P1/P2/P3 issues.`

Default to `reasoning_effort: "medium"` unless the user asks for deeper judgment.

Sample prompt:

- `/Users/babashunsuke/Repository/frontend-design-discipline/plugins/frontend-design-discipline/skills/frontend-composition-critic/SKILL.md にある $frontend-composition-critic を使って、Studio Pulse のランディングページを階層、構図、視覚バランスの観点でレビューしてください。PASS/FAIL と、残っている P1/P2/P3 の issue だけを返してください。`

## Good Findings

- `P1 Header block dominates the screen more than the product message, so the first glance lands on chrome instead of the subject. Reduce header scale and reclaim space for the opening zone.`
- `P1 Feature area reads like three interchangeable cards rather than a directional story. Recompose it into a staggered or editorial layout.`
- `P2 The primary action sits in the page but does not conclude the hierarchy. Increase positional clarity or reduce nearby competing elements.`

## Not Your Job

- Do not rewrite the whole page.
- Do not drift into copy critique unless the wording directly breaks hierarchy.
- Do not focus on implementation details unless they visibly break composition.
