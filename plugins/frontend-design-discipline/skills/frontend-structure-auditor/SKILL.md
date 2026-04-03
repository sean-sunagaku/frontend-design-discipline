---
name: frontend-structure-auditor
description: Review frame hierarchy, containment, auto layout, overflow, and structural fit before or after a UI build. Use when the question is whether the layout itself is built in a correct, stable shape rather than whether the visuals are merely attractive.
---

# Frontend Structure Auditor

## Overview

Use this skill when the main question is structural: are the right parent frames in place, is content clustered correctly, and do sections stay inside their bounds without relying on luck?

It is the dedicated reviewer for structure-first UI work. Use it when the screen should be built from real frames, wrappers, rows, columns, cards, rails, and clusters instead of loose placements that only look correct in one screenshot.
It also catches bare text layers and awkwardly ended lines when they should have been framed, grouped, widened, or rewritten instead.

## Core Rule

If the surface only works because items were nudged by coordinates, the structure is wrong.

## What To Check

Inspect these dimensions:

1. explicit parent structure for each major section or zone
2. real frames, stacks, rows, columns, cards, and clusters instead of floating text
3. text-containing parents defaulting to `HUG`
4. growing rows or cards using `AUTO` on the counter axis
5. absolute positioning used only for decoration or controlled overlays
6. `child bounds <= parent bounds` after each section
7. no overflow, clipping, or cut-off content
8. screenshot review happening only after the structural audit is written down
9. a breathing corridor between side-by-side masses when the surface needs calm separation
10. width widened before text is squeezed when the layout is clearly under-measured
11. text layers living inside explicit parent frames or clusters instead of standing alone
12. line endings that read naturally instead of stopping at an accidental phrase boundary

## Mark it NG if

- meaningful text has no stable parent frame
- a text layer appears as a loose standalone node instead of living inside a frame or cluster
- a text cluster is fixed-height when it clearly needs breathing room
- a row or card that should grow with copy is not using `AUTO`
- a section depends on manual x/y placement to look correct
- overflow, clipping, or cut-off content remains in any section
- a cluster only looks grouped because elements are nearby
- a board, rail, or surface is described visually but not decomposed into rows, cards, rails, notes, or clusters
- the likely build path starts from free-placed text and rectangles instead of section frames and nested clusters
- the layout needs a wrapper, row, or column but the packet has not named one
- side-by-side masses have no protected breathing corridor
- a heading, label, or helper line ends with an accidental-looking short line instead of a meaningful break
- the obvious fix is a structural wrapper or wider parent frame, but the plan still pushes text to fit by luck

## Output Contract

Return:

1. `PASS` or `FAIL`
2. one sentence describing whether the structure is stable enough to build from
3. remaining `P1` / `P2` / `P3` issues only

Each issue should say:

- what is structurally wrong
- why it would break or weaken the UI
- what kind of structural change would likely fix it

## Review Discipline

- Treat missing parent-child hierarchy as a first-order defect.
- Treat fixed-height text clusters as a first-order defect.
- Treat standalone text nodes as a first-order defect unless they are clearly decorative.
- Treat overflow as incomplete structure, not polish.
- Treat meaningful absolute positioning as a defect unless it is purely decorative.
- Treat a "looks okay" screenshot as insufficient if the tree itself is fragile.
- Prefer a wrapper, stack, row, column, or cluster before local coordinate tweaks.
- If widening the zone would clearly solve the problem, prefer widening over squeezing text.
- If a line ends awkwardly, prefer a wider measure, better cluster, or rewrite over a manual break.
- If the section needs a crop to prove it is safe, review the crop, not just the full page.

## Subagent Use

When delegated, explicitly instruct the subagent to read this skill.

Recommended prompt shape:

- `Use $frontend-structure-auditor at /absolute/path/to/SKILL.md and review this section for frame hierarchy, containment, overflow, auto layout, and structural fit. Return only PASS/FAIL plus remaining issues.`
- `Use $frontend-structure-auditor at /absolute/path/to/SKILL.md and review this section for frame hierarchy, text placement, containment, overflow, auto layout, and meaningful line breaks. Return only PASS/FAIL plus remaining issues.`
- `Use $frontend-structure-auditor at /absolute/path/to/SKILL.md and review this build packet for structural layout discipline before build. Return only PASS/FAIL plus remaining issues.`

Good findings:

- `P1 The section still depends on floating text and shapes, so the UI will be fragile in real build output. Add a wrapper frame and rebuild the text cluster inside it.`
- `P1 The heading is sitting as a standalone text node instead of living inside a frame or cluster. Wrap it explicitly so the layout can be reasoned about and resized safely.`
- `P1 The CTA cluster is fixed-height even though the copy is likely to wrap, so the section will fail as soon as content changes. Switch the cluster to HUG and let the action row size naturally.`
- `P2 The line ending looks accidental rather than intentional. Widen the cluster or rewrite the copy so the break reads as meaningful instead of rescued.`
- `P2 The side-by-side zones have no quiet band between them, which makes the structure feel tense even when the pixels do not overlap. Reserve a breathing corridor and widen the parent frame if needed.`

## Not Your Job

- Do not replace `$frontend-composition-critic` when the problem is visual balance rather than structure.
- Do not replace `$frontend-zone-fit-critic` when the problem is local overlap only.
- Do not debate taste; judge whether the layout is structurally stable enough to survive implementation.
