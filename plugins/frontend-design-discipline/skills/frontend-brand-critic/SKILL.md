---
name: frontend-brand-critic
description: Review a frontend screen, landing page, app UI, mock, or Figma frame for brand signal, first impression, and emotional fit. Use when the user wants to know whether the interface communicates the intended brand, mood, and product identity quickly, or whether the screen feels generic, contradictory, or aesthetically off-brief.
---

# Frontend Brand Critic

## Overview

Use this skill to judge whether the work communicates the intended brand in one glance. Treat weak brand presence as a product problem, not as optional polish.

If no artifact exists yet, review the proposed direction packet or first-view plan instead of punting. A weak brand plan should be rejected before build, not excused until later.

## What To Check

This skill can be used in two modes:

- artifact review: judge the current pixels or screen
- direction review: judge the proposed brief, packet, or first-view plan before build

In direction review mode, fail early if the proposed visual anchor is too weak to carry the intended identity.

Review these dimensions:

1. Is the brand or product unmistakable in the first screen?
2. Does the tone match the requested mood or product category?
3. Do type, color, imagery, and spacing point in the same direction?
4. Does the screen feel generic or borrowed from a default SaaS pattern?
5. If branding is meant to feel premium, calm, bold, playful, or technical, is that actually visible?

Mark it NG if:

- the brand disappears behind generic UI patterns
- the visual tone contradicts the stated intent
- imagery, typography, and chrome feel like unrelated systems
- the font choice feels like a safe default rather than part of the identity
- the page could belong to almost any product
- supporting elements dilute the intended first impression
- the proposed direction does not name a concrete visual anchor strong enough to carry the brand

## Output Contract

Return:

1. `PASS` or `FAIL`
2. one sentence describing the first impression
3. only the remaining brand issues, ordered by severity

Each issue should say:

- what signal is missing or contradictory
- why the brand impression fails
- what kind of visual change would restore the intended identity

## Review Discipline

- Focus on brand perception, not implementation mechanics.
- Be strict about genericity.
- If the user gave a specific brand bar such as "quiet luxury" or "observatory-like", judge against that exact bar.
- If the bar is missing, infer the likely intended impression from the artifact and call out contradictions.
- In direction review mode, treat vague mood language without a concrete visual plan as a real defect.

## Subagent Use

When used through a subagent, explicitly instruct the subagent to read this skill.

Recommended prompt shape:

- `Use $frontend-brand-critic at /absolute/path/to/SKILL.md and review whether this artifact communicates the intended brand and first impression. Return only PASS/FAIL and remaining P1/P2/P3 issues.`
- `Use $frontend-brand-critic at /absolute/path/to/SKILL.md and review whether this proposed direction packet would produce a distinct brand impression before anything is built. Return only PASS/FAIL and remaining P1/P2/P3 issues.`

Default to `reasoning_effort: "medium"` unless the user asks for deeper judgment.

Sample prompt:

- `/Users/babashunsuke/Repository/frontend-design-discipline/plugins/frontend-design-discipline/skills/frontend-brand-critic/SKILL.md にある $frontend-brand-critic を使って、Studio Pulse のランディングページが静かで精密で運用的なブランドを一目で伝えられているかレビューしてください。PASS/FAIL と、残っている P1/P2/P3 の issue だけを返してください。`

## Good Findings

- `P1 The page still reads as generic B2B SaaS rather than a distinct product. Reduce default card language and make the brand voice carry more of the first viewport.`
- `P1 The dark palette suggests restraint, but the accent usage is too busy to feel premium. Narrow the accent role and let the base surfaces carry the tone.`
- `P2 The headline says one thing while the imagery says another. Align the visual anchor with the actual product promise.`

## Not Your Job

- Do not spend the review on clipping or spacing unless those flaws materially damage the brand impression.
- Do not optimize for your personal taste. Judge against the intended identity.
