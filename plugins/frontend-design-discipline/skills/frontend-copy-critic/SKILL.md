---
name: frontend-copy-critic
description: Review frontend copy in a screen, landing page, app UI, mock, or Figma frame for clarity, hierarchy, wrapping quality, and message discipline. Use when the user wants strict feedback on whether headlines, labels, helper text, CTA text, and supporting copy read naturally, avoid filler, and support the UI instead of muddying it.
---

# Frontend Copy Critic

## Overview

Use this skill to review UI copy as placed, not as abstract text. Judge whether the words help the interface read faster and more clearly.

If no artifact exists yet, review the planned headline, CTA, and supporting-copy load in the direction packet. Catch vague or bloated messaging before it hardens into the layout.

## What To Check

This skill can be used in two modes:

- artifact review: judge placed copy in the current UI
- direction review: judge the planned headline, CTA, and support-copy load before build

In direction review mode, fail if the message will only work once long supporting text is added.

Inspect:

1. headline clarity
2. CTA wording
3. helper text necessity
4. repeated or bloated explanations
5. wrapping quality and line-break semantics
6. section-by-section line budget discipline

Mark it NG if:

- the message is slower to understand because of the copy
- helper text repeats what the layout already says
- a headline is broad but the CTA does not tell the user what to do
- the headline has to become oversized because the wording lacks precision
- lower-section titles only work because they are allowed to wrap too many lines
- multiple neighboring blocks have similarly awkward wrapping, creating a templated feel
- labels or notes wrap at awkward linguistic points
- Japanese copy feels mechanically wrapped rather than intentionally set
- filler copy weakens the intended hierarchy
- the plan relies on multiple explanatory sentences because the visual direction is too weak

## Output Contract

Return:

1. `PASS` or `FAIL`
2. a one-sentence copy verdict
3. only the remaining copy issues, ordered by severity

Each issue must state:

- the problematic text or text area
- why it fails
- whether it should be shortened, rewritten, moved, or deleted

## Review Discipline

- Review copy in context of the layout.
- Prefer deletion over rewriting when the text is unnecessary.
- Treat awkward line breaks as a real defect.
- If one sentence could be cut with no loss, call that out.
- If a section lacks an explicit line budget, ask for one implicitly by failing uncontrolled wrapping.

## Subagent Use

When used through a subagent, explicitly instruct the subagent to read this skill.

Recommended prompt shape:

- `Use $frontend-copy-critic at /absolute/path/to/SKILL.md and review this artifact for copy clarity, wrapping, helper text noise, and CTA wording. Return only PASS/FAIL and remaining P1/P2/P3 issues.`
- `Use $frontend-copy-critic at /absolute/path/to/SKILL.md and review this proposed headline, CTA, and supporting-copy plan before build. Return only PASS/FAIL and remaining P1/P2/P3 issues.`

Default to `reasoning_effort: "medium"` unless the user asks for deeper judgment.

Sample prompt:

- `/Users/babashunsuke/Repository/frontend-design-discipline/plugins/frontend-design-discipline/skills/frontend-copy-critic/SKILL.md にある $frontend-copy-critic を使って、Studio Pulse のランディングページをコピーの明快さ、折り返し、補助文のノイズ、CTA 文言の観点でレビューしてください。PASS/FAIL と、残っている P1/P2/P3 の issue だけを返してください。`

## Good Findings

- `P1 The CTA says too little to conclude the page. Replace the vague action with a direct product action.`
- `P1 The helper text under the button is not broken technically, but it reads as noise and weakens the close. Remove it or move it out of the CTA cluster.`
- `P2 The paragraph wraps at unnatural phrase boundaries, which makes it feel clipped. Rewrite the sentence or narrow the measure deliberately.`

## Not Your Job

- Do not spend the review on layout except where layout causes copy failure.
- Do not suggest longer copy unless the current version is missing essential meaning.
