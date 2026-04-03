# frontend-design-discipline

Codex plugin for focused frontend review skills around composition, brand signal,
copy quality, UI stability, and iterative review-refine loops.

## Install

Codex の対話画面で次を実行します。

```text
/install-plugin https://github.com/sean-sunagaku/frontend-design-discipline
```

## Included Plugin

このリポジトリには次の plugin が含まれています。

- `frontend-design-discipline`

plugin 本体は `plugins/frontend-design-discipline/` にあります。

## Included Skills

- `frontend-brand-critic`
- `frontend-composition-critic`
- `frontend-copy-critic`
- `frontend-ui-auditor`
- `review-refine-loop`

## Repository Structure

- `.agents/plugins/marketplace.json`: GitHub install 用の marketplace entry
- `plugins/frontend-design-discipline/.codex-plugin/plugin.json`: plugin manifest
- `plugins/frontend-design-discipline/skills/`: bundled skills
- `plugins/frontend-design-discipline/sample/`: sample briefs and review criteria
