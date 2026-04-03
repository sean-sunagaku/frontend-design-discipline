---
name: frontend-ui-auditor
description: Audit a frontend screen, landing page, dashboard, workflow view, app UI, mock, or Figma frame for readability, spacing, clipping, contrast, responsiveness, and implementation-level fit. Use when the user wants a strict pass/fail review of whether text is visible, UI elements fit their containers, spacing feels stable, and the interface would likely survive real browser rendering across common breakpoints.
---

# Frontend UI Auditor

## Overview

Use this skill when the question is not "is the idea good?" but "will this UI hold up in reality?" Review visible stability, readability, and fit.

If no artifact exists yet, review the proposed layout structure for likely fragility. If the plan already looks breakpoint-fragile, text-heavy, or edge-hugging, fail it before implementation.

## What To Check

This skill can be used in two modes:

- artifact review: judge the visible screen for stability
- direction review: judge the proposed structure for likely spacing, breakpoint, and density failures before build

In direction review mode, fail if the plan already reads as brittle or edge-hugging.

Inspect these failure modes:

1. clipped, cramped, washed-out, or low-contrast text
2. awkward or ambiguous line breaks
3. spacing that feels accidental or fragile
4. elements too close to edges, dividers, or neighboring blocks
5. text fit inside bounded areas such as cards, rails, panels, or buttons
6. likely breakpoint failures at common desktop and mobile widths

Default widths to reason through:

- 1440px
- 1024px
- 768px
- 390px

Mark it NG if:

- text looks cut off or almost cut off
- content technically fits but still reads as broken
- bounded areas such as cards, mockups, and rails look one line away from failure
- text appears to slip outside a frame, box, pill, or button, even slightly
- secondary-zone text only fits because the box is overfilled and visually tense
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
- If a box looks like it needs one more line of padding or one less line of text, fail it now rather than calling it acceptable.

## Subagent Use

When used through a subagent, explicitly instruct the subagent to read this skill.

Recommended prompt shape:

- `Use $frontend-ui-auditor at /absolute/path/to/SKILL.md and review this artifact for clipping, spacing, contrast, and UI stability. Return only PASS/FAIL and remaining P1/P2/P3 issues.`
- `Use $frontend-ui-auditor at /absolute/path/to/SKILL.md and review this proposed layout structure for clipping risk, spacing fragility, breakpoint risk, and UI stability before build. Return only PASS/FAIL and remaining P1/P2/P3 issues.`

Default to `reasoning_effort: "medium"` unless the user asks for deeper judgment.

Sample prompt:

- `/Users/babashunsuke/Repository/frontend-design-discipline/plugins/frontend-design-discipline/skills/frontend-ui-auditor/SKILL.md にある $frontend-ui-auditor を使って、Studio Pulse のランディングページを見切れ、余白、コントラスト、UI 安定性の観点でレビューしてください。PASS/FAIL と、残っている P1/P2/P3 の issue だけを返してください。`

## Good Findings

- `P1 Supporting text is not clipped, but it sits so close to the edge that it reads as broken. Increase container padding or shorten the copy.`
- `P1 The right rail is readable on desktop but too fragile for narrower widths. Reduce copy load or reflow the structure before implementation.`
- `P2 Contrast in the idle state is too low for routine scanning. Raise value contrast without changing the whole palette.`

## Not Your Job

- Do not use this skill for abstract brand critique.
- Do not propose sweeping art-direction changes unless the current UI is impossible to stabilize otherwise.
