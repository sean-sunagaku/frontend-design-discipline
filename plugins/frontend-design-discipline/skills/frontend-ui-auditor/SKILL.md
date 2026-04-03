---
name: frontend-ui-auditor
description: Audit a frontend screen, landing page, dashboard, workflow view, app UI, mock, or Figma frame for readability, spacing, clipping, contrast, responsiveness, and implementation-level fit. Use when the user wants a strict pass/fail review of whether text is visible, UI elements fit their containers, spacing feels stable, and the interface would likely survive real browser rendering across common breakpoints.
---

# Frontend UI Auditor

## Overview

Use this skill when the question is not "is the idea good?" but "will this UI hold up in reality?" Review visible stability, readability, and fit.

If the problem is highly local, such as one section crop, one CTA cluster, or one note rail that may be touching or cramped, prefer `$frontend-zone-fit-critic`.

If no artifact exists yet, review the proposed layout structure for likely fragility. If the plan already looks breakpoint-fragile, text-heavy, or edge-hugging, fail it before implementation.

## What To Check

This skill can be used in two modes:

- artifact review: judge the visible screen for stability
- direction review: judge the proposed structure for likely spacing, breakpoint, and density failures before build

In direction review mode, fail if the plan already reads as brittle or edge-hugging.

For artifact review, do not sign off from one full-page screenshot alone when the surface contains multiple zones or text-heavy areas.

Default inspection order:

1. full artifact screenshot for overall stability
2. one screenshot per major zone
3. extra screenshots for text-heavy or bounded clusters

Examples of cluster-level crops:

- hero text column
- support copy versus nearby proof object
- detail copy cluster beside a rail or thread
- final CTA cluster

Inspect these failure modes:

1. clipped, cramped, washed-out, or low-contrast text
2. awkward or ambiguous line breaks
3. spacing that feels accidental or fragile
4. elements too close to edges, dividers, or neighboring blocks
5. text fit inside bounded areas such as cards, rails, panels, or buttons
6. text clusters that are visually detached, stranded, or assembled with fragile spacing
7. underused horizontal space that creates avoidable wrapping, crowding, or overlap
8. missing breathing room between side-by-side masses
9. likely breakpoint failures at common desktop and mobile widths

Default widths to reason through:

- 1440px
- 1024px
- 768px
- 390px

Mark it NG if:

- text looks cut off or almost cut off
- content technically fits but still reads as broken
- a full-page view looks acceptable but a zone or cluster crop reveals overlap, collision, or cramped spacing
- bounded areas such as cards, mockups, and rails look one line away from failure
- text appears to slip outside a frame, box, pill, or button, even slightly
- text and nearby objects do not overlap technically but still read as touching, kissing, or visually colliding
- secondary-zone text only fits because the box is overfilled and visually tense
- a major heading that should read in 1 line, or at most 2, has drifted into a third line because the zone was never widened enough
- headings, body copy, captions, and actions do not read as one stable cluster
- a CTA, caption, or helper line feels stranded rather than attached to a clear parent cluster
- the obvious fix is to widen the zone, column, or cluster area, but the layout instead keeps squeezing text vertically
- the screen keeps large amounts of empty horizontal space while text-heavy areas wrap, collide, or crowd each other
- side-by-side masses have no calm breathing corridor between them, so the layout reads crowded even with nominal spacing
- contrast is too weak for routine reading
- headline scale is so aggressive that the opening-zone balance depends on luck
- secondary-zone text blocks rely on narrow columns and overwrapping to fit
- the layout depends on luck rather than resilient spacing
- the proposed structure would obviously become fragile at common breakpoints

## Output Contract

Return:

1. `PASS` or `FAIL`
2. a one-sentence UI stability verdict
3. remaining issues only, ordered by severity

Each issue must explain:

- what is visibly or structurally risky
- why it would fail in real use
- what fix would stabilize it

## Review Discipline

- Be strict about "looks broken" even if the text is technically present.
- Treat almost-failing layouts as failures.
- Separate readability issues from brand or composition issues unless they overlap directly.
- When screenshots are available, trust the pixels first.
- When both full-page and section crops exist, trust the tighter crop for overlap and spacing calls.
- If a box looks like it needs one more line of padding or one less line of text, fail it now rather than calling it acceptable.
- If a text-heavy zone only becomes readable after mentally separating pieces, fail it and ask for a more stable cluster.
- If widening the available measure would clearly stabilize the zone, prefer that fix before shrinking type or forcing additional rows.
- If a heading has fallen into a preventable third line, prefer widening, rewriting, or regrouping before accepting it as stable.
- If the gap is technically present but still reads as tense or kissing, fail it and ask for a clearer breathing corridor.

## Subagent Use

When used through a subagent, explicitly instruct the subagent to read this skill.

Recommended prompt shape:

- `Use $frontend-ui-auditor at /absolute/path/to/SKILL.md and review this artifact for clipping, spacing, contrast, and UI stability. Return only PASS/FAIL and remaining P1/P2/P3 issues.`
- `Use $frontend-ui-auditor at /absolute/path/to/SKILL.md and review this artifact zone by zone for clipping, overlap, spacing, text fit, and UI stability. Return only PASS/FAIL and remaining P1/P2/P3 issues.`
- `Use $frontend-ui-auditor at /absolute/path/to/SKILL.md and review this proposed layout structure for clipping risk, spacing fragility, breakpoint risk, and UI stability before build. Return only PASS/FAIL and remaining P1/P2/P3 issues.`

Default to `reasoning_effort: "medium"` unless the user asks for deeper judgment.

Sample prompt:

- `/Users/babashunsuke/Repository/frontend-design-discipline/plugins/frontend-design-discipline/skills/frontend-ui-auditor/SKILL.md にある $frontend-ui-auditor を使って、Studio Pulse のランディングページを見切れ、余白、コントラスト、UI 安定性の観点でレビューしてください。PASS/FAIL と、残っている P1/P2/P3 の issue だけを返してください。`

## Good Findings

- `P1 Supporting text is not clipped, but it sits so close to the edge that it reads as broken. Increase container padding or shorten the copy.`
- `P1 The right rail is readable on desktop but too fragile for narrower widths. Reduce copy load or reflow the structure before implementation.`
- `P1 The final CTA looks acceptable in the full-page view, but the section crop shows the body and action cluster colliding with nearby elements. Rebuild the closing cluster as one stacked unit and reserve more clearance.`
- `P1 The copy and proof object do not overlap, but the gap is so small that the section still reads as visually colliding. Increase the breathing corridor or widen the zone before trying smaller type changes.`
- `P2 Contrast in the idle state is too low for routine scanning. Raise value contrast without changing the whole palette.`

## Not Your Job

- Do not use this skill for abstract brand critique.
- Do not propose sweeping art-direction changes unless the current UI is impossible to stabilize otherwise.
