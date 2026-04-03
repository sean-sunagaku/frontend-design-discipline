# frontend-design-discipline

Codex plugin for focused frontend review skills around composition, brand signal,
copy quality, UI stability, and iterative review-refine loops.

## What This Repo Is

このリポジトリは、Codex plugin を `repo marketplace` 形式で配布するための公開リポジトリです。

GitHub に公開されていても、現時点では GitHub URL をそのまま `install` する方式ではなく、
Codex が読める marketplace 経由で使う前提です。

## How To Use

### Option 1: Clone this repo and use it as a repo marketplace

いちばん分かりやすい使い方です。

```bash
git clone https://github.com/sean-sunagaku/frontend-design-discipline.git
cd frontend-design-discipline
```

その後、このリポジトリを Codex で開いてください。

Codex は repo 内の `.agents/plugins/marketplace.json` を読み、
`plugins/frontend-design-discipline/` にある plugin を認識します。

### Option 2: Register it in your personal marketplace

複数のリポジトリから共通で使いたい場合は、各自の `personal marketplace` に登録できます。

`personal marketplace` は次の場所です。

```text
~/.agents/plugins/marketplace.json
```

この方法では、各ユーザーが自分のローカル環境に plugin 実体を配置し、
`marketplace.json` からそのローカルパスを参照する必要があります。

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

- `.agents/plugins/marketplace.json`: repo marketplace entry
- `plugins/frontend-design-discipline/.codex-plugin/plugin.json`: plugin manifest
- `plugins/frontend-design-discipline/skills/`: bundled skills
- `plugins/frontend-design-discipline/sample/`: sample briefs and review criteria

## Notes

- GitHub に公開しただけでは、他の人の Codex に自動インストールはされません
- 一般ユーザーが使うには、repo を clone して Codex で開く方法がもっとも簡単です
- `personal marketplace` は、ユーザー個人の Codex 環境全体で使うための手動登録方法です
