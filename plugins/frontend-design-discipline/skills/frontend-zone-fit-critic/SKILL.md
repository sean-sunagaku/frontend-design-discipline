---
name: frontend-zone-fit-critic
description: Review a frontend section, zone, or screenshot crop for local text fit, overlap, near-collision, breathing room, and width allocation. Use when the overall direction looks right but a text-heavy area may still be cramped, visually colliding, or under-using available horizontal space.
---

# Frontend Zone Fit Critic

## Overview

Use this skill when the question is local, not global.

This reviewer does not ask whether the whole page is beautiful. It asks whether one zone, section, or crop is physically and visually safe.

Use it for:

- hero text columns
- support/detail text zones
- CTA clusters
- rails, notes, captions, and proof items
- side-by-side copy and visual pairs
- app sidebars, inspectors, and action panels

If the full-page composition passes but one area still feels crowded, touching, or one step away from failure, use this skill.

## What To Check

Inspect these failure modes:

1. literal overlap
2. near-overlap or visual kissing
3. edge touch inside bounded areas
4. cramped heading/body/action spacing
5. weak cluster cohesion
6. missing breathing corridor between neighboring masses
7. underused width causing avoidable wrapping or crowding
8. fragile local layout that would likely break after one copy change
9. odd manual line breaks inside the local crop
10. preventable third-line headings inside the local crop

Mark it NG if:

- text overlaps another text block, note, rail, card, or object
- elements do not overlap technically but still read as touching, kissing, or visually colliding
- body copy, caption, and action feel jammed together instead of reading as one calm cluster
- a bounded area only works because the text happens to break at one exact line
- a heading, label, or button in the crop appears manually broken at an unnatural point
- a local heading that should comfortably read in 1 line, or at most 2, spills into a third line because width was under-allocated
- text sits too close to a frame edge, divider, or nearby object
- the obvious fix is to widen the local zone, but the layout instead keeps squeezing text vertically
- the crop shows unused horizontal room while the text wraps into tense multi-line stacks
- the zone would likely fail after a minor copy edit, localization change, or one-size-step type increase

## Preferred Evidence

Trust the tightest crop that reveals the problem.

Best inputs:

- section screenshot
- cluster screenshot
- close crop of copy versus nearby object

Do not rely on a full-page screenshot when a local crop would show the real issue more clearly.

## Output Contract

Return:

1. `PASS` or `FAIL`
2. one sentence saying whether this local zone is safe
3. remaining `P1` / `P2` / `P3` issues only

Each issue must state:

- what is colliding, cramped, or fragile
- why it still fails locally
- whether the right fix is more clearance, a stronger cluster, or more width

## Review Discipline

- Be stricter than a normal visual review.
- Treat "almost touching" as a real issue.
- Prefer widening and re-spacing before shrinking type.
- Prefer widening, regrouping, or shortening before accepting a third line in a heading.
- Prefer healthier measure and grouping before inserting manual line breaks.
- If a cluster only works because the copy is short today, fail it.
- If a side-by-side layout has no calm quiet band, fail it even without literal overlap.

## Subagent Use

When used through a subagent, explicitly instruct the subagent to read this skill.

Recommended prompt shape:

- `Use $frontend-zone-fit-critic at /absolute/path/to/SKILL.md and review this zone crop for overlap, local text fit, breathing room, and width allocation. Return only PASS/FAIL and remaining P1/P2/P3 issues.`
- `Use $frontend-zone-fit-critic at /absolute/path/to/SKILL.md and review this CTA cluster for collision, cramped spacing, and stray elements. Return only PASS/FAIL and remaining P1/P2/P3 issues.`

Default to `reasoning_effort: "medium"` unless the user asks for deeper judgment.

## Good Findings

- `P1 The support copy and proof object do not literally overlap, but the gap is so small that the crop still reads as visually colliding. Increase the breathing corridor or widen the zone.`
- `P1 The CTA cluster is technically inside its panel, but the body and action are too compressed to feel stable. Rebuild it as one calmer stack with more vertical clearance.`
- `P2 The note rail could survive if the zone were wider. Reallocate horizontal room before shrinking type or forcing a harsher break.`

## Not Your Job

- Do not critique the whole art direction unless the local fit problem is caused by it.
- Do not rewrite the entire page when the real issue is one unsafe zone.
