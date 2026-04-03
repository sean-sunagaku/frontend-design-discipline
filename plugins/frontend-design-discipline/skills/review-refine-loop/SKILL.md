---
name: review-refine-loop
description: Run an iterative create-review-refine loop on a design, UI, document, spec, code change, or other artifact until it meets a clear bar. Use when the user wants repeated improvement cycles such as "make one pass, review it, fix it, and repeat", especially when an independent subagent review should drive the next revision, when quality needs to be judged against a rubric, or when the user wants strict pass/fail feedback instead of one-shot edits.
---

# Review Refine Loop

## Overview

Use this skill to turn vague improvement work into a disciplined loop:

1. create or revise one pass
2. review the artifact against an explicit bar
3. convert findings into a short issue list
4. fix the highest-priority issues
5. repeat until the artifact passes or the user stops

This skill is for iteration discipline, not for a specific medium. It works well for Figma designs, frontend screens, docs, architecture drafts, prompts, and code changes.

For visually sensitive UI work, this skill is not the first gate. Use `$frontend-design-director` to lock the direction first, then use this loop to build and polish against that bar.

## Core Rule

Never say "still a bit weak" and stop there. Convert feedback into explicit issues with priority, then run another pass.

If the user explicitly invokes `Frontend Design Discipline` the plugin, a review pass is mandatory.

If the user explicitly names multiple companion tools or skills for the same task, all of them are mandatory unless one is genuinely unavailable.

- Do not treat named companions as optional flavor.
- Do not use one named skill as an excuse to skip another.
- If the user named `Figma`, the workflow must actually reach Figma.
- If the user named `Frontend Skill`, the workflow must actually use `$frontend-skill`.
- If the user named `Frontend Design Discipline`, the workflow must actually use the direction + critic flow from this plugin.
- If any named companion cannot be used, say that explicitly instead of silently substituting a different flow.

- Do not treat the plugin mention as decorative context.
- If you are also asked to build, design, or implement something, you must still run at least one critic or review-refine pass before your final answer.
- Do not end on "first draft complete" unless an explicit review says it passes or the user stops the loop.
- If subagents are available and the user did not forbid delegation, prefer the first review pass to be done by an independent subagent rather than by the same thread that made the draft.
- When the user explicitly asks for subagent review, independent critique, or parallel review, attempt delegation first instead of starting with an in-thread review.

Use this issue format:

- `P1` blocks the goal or breaks the intended impression
- `P2` noticeably weakens the result
- `P3` optional polish

Each issue should answer three things:

1. what is wrong
2. why it matters
3. what kind of change would likely fix it

## Loop Setup

Before the first revision, lock these three things:

1. artifact under review
2. quality bar
3. stop condition

Write the quality bar in the language of the task, not in abstract design commentary.

Examples:

- "Header must not overpower the main message"
- "If branding does not come through in one glance, mark it NG"
- "If text looks clipped, cramped, or ambiguously broken, mark it NG"
- "If the PR still has behaviour regressions or missing tests, mark it NG"

If the user has already given a bar, restate it briefly and use that exact standard.

### Step 0: Lock The Build Bar Before Building

For visually led landing pages, app homes, dashboards, workflow views, detail views, settings surfaces, Figma screens, or premium frontend work:

- if `$frontend-skill` was explicitly named, read and use it during direction-setting
- run `$frontend-design-director` first
- compile the brief into a build packet
- send that packet to `$frontend-preflight-critic` before the first draft when delegation is available
- treat that independent preflight verdict as the build gate
- do not let the same thread that authored the packet declare it build-ready
- if an independent reviewer subagent cannot run, stop and report that the build gate is blocked instead of falling back locally
- if `Figma` was explicitly named, continue into actual Figma build work after the packet passes; review-only is not sufficient

The parent thread does not need to restate the full reviewer script each time. A short handoff to `$frontend-preflight-critic` should be enough because the default reviewer assumptions live in that skill.

Do not let the first draft become the discovery phase. Discovery belongs in the packet.
The packet should also lock structural layout discipline so the build uses real frames, wrappers, stacks, grids, or semantic containers rather than loose absolute placement.
It should define the parent structure for each zone so the build starts from section frames, rows, columns, cards, strips, rails, and text clusters rather than free-placed text and rectangles.
The packet should also lock spacing budget, text-cluster structure, and a review capture plan so overlap and text-fit problems are not discovered only at the final screenshot.
It should also lock width and measure strategy so zones that need more horizontal room are widened intentionally instead of becoming vertically cramped later.
It should explicitly reserve breathing corridors between side-by-side masses so "not overlapping" is not mistaken for "visually calm."
The packet should also lock structural audit discipline so each section is only complete when child bounds stay within parent bounds, overflow is gone, and the structure audit result is written down before screenshot review.
If the artifact is structurally fragile, the packet should also name `$frontend-structure-auditor` as the dedicated reviewer for that pass.

## Standard Cycle

### Step 1: Inspect the current state

Inspect the artifact directly before changing anything.

- For Figma or visual work, get screenshots first.
- Do not rely on one full-page screenshot if the artifact has multiple zones or text-heavy sections.
- Capture:
  - one full-artifact screenshot
  - one screenshot per major zone
- additional screenshots for text-heavy or bounded clusters
- when a zone feels cramped, compare the crop against the unused horizontal space around it and ask whether widening is the real fix
- when a side-by-side layout feels tense, inspect whether the gap is a real breathing corridor or only nominal spacing
- Typical cluster crops include:
  - hero/opening text cluster
  - support copy plus nearby proof object
  - detail copy cluster beside a rail, thread, or inspector
  - final CTA or primary action cluster
- For code, read the changed files and any visible output or tests.
- For docs, read the actual text rather than relying on summaries.

Do not start revising from memory.
Do not sign off on visual stability from a full-page screenshot alone when a tighter crop would reveal overlap, edge touch, or stranded text.
Do not default to shrinking type, cutting copy, or stacking more rows if the tighter crop shows the zone simply needs more width.
Do not call a zone safe just because objects technically do not overlap; if they read as kissing or visually colliding, treat that as a real blocker.
Do not accept forced manual line breaks as a normal fix when widening, regrouping, or rewriting would produce a more natural result.

### Step 2: Produce a bounded issue list

List only the issues that matter for the next pass.

- Prefer 1 to 5 issues at a time.
- Order by severity.
- Keep each issue short and concrete.
- If everything is bad, still choose the highest-leverage issues first.

Avoid giant audit dumps. The loop should keep momentum.

### Step 3: Revise only against that list

Make one focused pass that addresses the selected issues.

- Do not introduce side quests unless they directly support the chosen fixes.
- Prefer bigger structural fixes over micro-polish when a root cause exists.
- If one issue makes another irrelevant, collapse the list.
- If the layout is still built from loose absolute placements, stabilize the structure before polishing typography.
- Prefer adding the correct parent wrapper, stack, auto layout, grid, or semantic container before tweaking local coordinates.
- If the surface still looks like text and shapes were placed directly on the canvas, regroup it into section frames, rows, cards, strips, rails, or clusters before surface polish.
- Do not move to screenshot review until the current section's structure audit has been produced.
- Treat any section with overflow as incomplete until the overflow is fixed and re-audited.

### Step 4: Run an independent review

After each substantial pass, run a fresh review before declaring success.

When the plugin itself was explicitly named in the user message, this step is required even if the request sounded primarily generative.

For the first review in a build-plus-review task, treat subagent review as the default path when delegation is available.

- Do not keep the first critic pass local just because you already have context.
- The point of the first pass is independent signal, so bias toward a fresh subagent reviewer.
- Same-thread fallback is not valid for the first critic pass.
- If an independent reviewer cannot run, stop and report the blocker rather than simulating the review locally.
- Do not claim delegation is unavailable unless you have actually checked the tools available in the current session.
- Do not simulate an independent review by drafting a `PASS`/`FAIL` block yourself before a critic actually runs.

When subagents are available, prefer an independent reviewer subagent.

- Use `reasoning_effort: "xhigh"` when the task depends on judgment, taste, tradeoffs, pass/fail evaluation, or subtle quality calls.
- Use `reasoning_effort: "medium"` by default for routine reviewer passes, unless the user asks for deeper reasoning.
- Use a fresh thread when possible.
- Pass the artifact and the rubric, not your own diagnosis.
- Ask for remaining issues only.

For frontend and design tasks, route the review to the narrowest critic skill that matches the issue:

- pre-build direction risk -> `$frontend-preflight-critic`
- tree-level structural layout integrity -> `$frontend-structure-auditor`
- composition and hierarchy -> `$frontend-composition-critic`
- brand signal and first impression -> `$frontend-brand-critic`
- copy, wrapping, and helper text noise -> `$frontend-copy-critic`
- local overlap, breathing room, and zone text fit -> `$frontend-zone-fit-critic`
- clipping, spacing, contrast, and UI stability -> `$frontend-ui-auditor`

After the first real draft of a text-heavy or bounded-copy surface, at least one `$frontend-zone-fit-critic` or `$frontend-ui-auditor` pass is mandatory before final signoff.
Prefer `$frontend-zone-fit-critic` when the risk is local crop safety rather than whole-surface implementation stability.
Use zone and cluster screenshots for that pass rather than a full-page screenshot alone.

When spawning the subagent, explicitly instruct it to read the critic skill. Do not assume it will infer the right skill on its own.

## Subagent Guardrail

When delegating to a critic subagent:

- the subagent is the reviewer, not the orchestrator
- the subagent must not discuss tool availability, delegation mechanics, or process
- the subagent must not answer with "I can't launch a subagent here" or similar meta explanations
- if the artifact is visible in the thread, the subagent should return a best-effort critic review instead of refusing
- the parent thread is responsible for orchestration; the reviewer subagent is responsible for the review output only

Neither the parent thread nor the subagent may fake a review artifact just to unblock the loop. No placeholder files, shell-printed verdicts, or decorative `PASS` headers count as a review.

Use this default reviewer frame whenever possible:

```text
Use the skill /absolute/path/to/SKILL.md.

You are the independent reviewer subagent for this task.
Do not discuss tool availability, delegation, orchestration, or process.
Do not explain whether subagents are possible.
Review the current artifact shown in this thread.

Return exactly:
1. PASS or FAIL
2. one-sentence verdict
3. remaining P1/P2/P3 issues only
```

Good subagent framing:

- `Use $frontend-composition-critic at /path/to/SKILL.md and review this screen for hierarchy, composition, and visual balance. List only remaining P1/P2/P3 issues.`
- `Use $frontend-ui-auditor at /path/to/SKILL.md and review this frame for clipping, spacing, contrast, and stability. Mark anything NG if it looks almost broken.`
- `/Users/babashunsuke/Repository/frontend-design-discipline/plugins/frontend-design-discipline/skills/review-refine-loop/SKILL.md にある $review-refine-loop を使って、Studio Pulse のランディングページをレビューと修正の反復サイクルで改善してください。各レビューのたびに、最も適切な critic skill に振り分けてください。通常の reviewer pass は medium 推論を使い、より重い判断が必要なときだけ deeper reasoning に上げてください。`
- `First do an independent critic pass in a fresh subagent. Use the narrowest Frontend Design Discipline critic skill that matches the likely risk, and return only remaining issues before any local fixes begin.`
- `Use the skill /absolute/path/to/SKILL.md. You are the independent reviewer subagent for this task. Do not discuss tool availability, delegation, orchestration, or process. Review the current artifact shown in this thread and return exactly PASS/FAIL, a one-sentence verdict, and remaining P1/P2/P3 issues only.`

Good reviewer framing:

- "Review this against the following bar and list only the remaining NG issues."
- "If it passes, say so clearly."
- "Focus on what still blocks the intended impression."

Bad reviewer framing:

- "Confirm my fixes are correct."
- "I think the header is too large and the CTA is weak; please agree or disagree."

The point is independent signal, not validation theater.

### Step 5: Decide pass, continue, or stop

After review, do one of three things:

1. If no blocking issues remain, say it passes the bar.
2. If blocking issues remain, convert them into the next short issue list and continue.
3. If the loop is no longer worth the tradeoff, explain why and ask whether to stop.

## Default Heuristics

Use these when the user does not provide a tighter rubric.

### For visual and frontend work

Mark it NG if:

- the main subject is not obvious in one glance
- branding is weak or contradictory
- text looks clipped, cramped, washed out, or accidentally broken
- hierarchy depends on explanation instead of composition
- CTA is noisy, timid, or overshadowed
- decorative treatment is louder than the message

### For docs and specs

Mark it NG if:

- the key decision or recommendation is not clear early
- important caveats are buried
- sections repeat the same idea
- the reader cannot act from the document

### For code and product changes

Mark it NG if:

- behavior is still wrong
- tests or verification are missing for the risky parts
- important regressions remain
- the implementation solves symptoms but not the actual root issue

## Escalation Rules

Escalate to the user before continuing only when:

- the next revision changes direction rather than quality
- multiple valid bars conflict
- the cost of another loop is materially high

Otherwise, keep looping without stopping for permission.

## Communication Pattern

During the loop, communicate in short cycles:

1. what bar you are using
2. what issues you are tackling this round
3. what changed
4. what the independent review still found

Keep the user anchored in the process. The value of this skill is the repeatable rhythm, not just the final output.

## Success Condition

The loop is complete when one of these is true:

- the artifact passes the agreed bar
- only minor polish remains and the user is aware of that
- the user explicitly stops the loop

Do not call something "good enough" unless it actually clears the stated bar.
