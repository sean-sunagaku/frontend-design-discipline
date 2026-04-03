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

plugin が一覧に見えたあと、最後に Codex の `Plugins` 画面で
`Frontend Design Discipline` を選び、`Install plugin` を実行してください。

### Option 2: Register it in your personal marketplace

複数のリポジトリから共通で使いたい場合は、各自の `personal marketplace` に登録できます。

`personal marketplace` は次の場所です。

```text
~/.agents/plugins/marketplace.json
```

この方法では、各ユーザーが自分のローカル環境に plugin 実体を配置し、
`marketplace.json` からそのローカルパスを参照する必要があります。

実際には、たとえば次のような配置を作ります。

```text
~/.agents/plugins/marketplace.json
~/plugins/frontend-design-discipline/
```

`~/.agents/plugins/marketplace.json` の例:

```json
{
  "name": "my-plugins",
  "interface": {
    "displayName": "My Plugins"
  },
  "plugins": [
    {
      "name": "frontend-design-discipline",
      "source": {
        "source": "local",
        "path": "./plugins/frontend-design-discipline"
      },
      "policy": {
        "installation": "AVAILABLE",
        "authentication": "ON_INSTALL"
      },
      "category": "Productivity"
    }
  ]
}
```

この例では、Codex は `~/.agents/plugins/marketplace.json` を読み、
そこから `~/plugins/frontend-design-discipline` を参照します。

この状態ではまだ「一覧に表示される」だけです。
実際に使うには、Codex の `Plugins` 画面で `Frontend Design Discipline` を選び、
`Install plugin` を実行する必要があります。

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

## Invocation Contract

この plugin は「作るための装飾」ではなく、「レビュー工程を強制するための plugin」として使うのが基本です。

- ユーザーが `Frontend Design Discipline` を明示したら、少なくとも 1 回は critic skill または `review-refine-loop` を通す
- subagent が使える環境なら、最初の critic pass は独立した subagent reviewer を優先する
- ユーザーが独立レビューや subagent review を明示したら、まず delegation を試みてから fallback を選ぶ
- build 系 skill や Figma 制作と併用する場合も、初稿で終わらせずレビュー工程を挟む
- final answer では、通した critic と残課題、もしくは pass 判定を明示する
- reviewer subagent はメタ説明に流れず、PASS/FAIL と issue だけを返す

意図としては、「plugin が見えていたのにレビューを飛ばした」「独立レビューに出さず自己診断だけで終えた」「reviewer subagent がメタ会話に逃げた」を防ぐことにあります。

## Repository Structure

- `.agents/plugins/marketplace.json`: repo marketplace entry
- `plugins/frontend-design-discipline/.codex-plugin/plugin.json`: plugin manifest
- `plugins/frontend-design-discipline/skills/`: bundled skills
- `plugins/frontend-design-discipline/sample/`: sample briefs and review criteria

## Notes

- GitHub に公開しただけでは、他の人の Codex に自動インストールはされません
- 一般ユーザーが使うには、repo を clone して Codex で開く方法がもっとも簡単です
- `personal marketplace` は、ユーザー個人の Codex 環境全体で使うための手動登録方法です
- marketplace に載っただけでは未インストールです。`Plugins` 画面で `Install plugin` が必要です
