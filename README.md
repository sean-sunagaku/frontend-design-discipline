# frontend-design-discipline

Codex plugin for locking a strong design direction before build, then reviewing
composition, brand signal, copy quality, UI stability, and refinement loops.

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

- `frontend-design-director`
- `frontend-preflight-critic`
- `frontend-brand-critic`
- `frontend-composition-critic`
- `frontend-copy-critic`
- `frontend-zone-fit-critic`
- `frontend-ui-auditor`
- `review-refine-loop`

## Invocation Contract

この plugin は「まず美意識を固定し、そのあと厳しく批評する」ための plugin です。

レビューできるタイミングは build 後だけではありません。

- brief の段階
- build packet の段階
- wireframe / section plan の段階
- 実際の artifact の段階

どの段階でも critic を走らせられるようにして、弱い方向を早く落とすのが前提です。

- まず `frontend-design-director` で build packet を作る
- build 前に `frontend-preflight-critic` で方向そのものを落とす
- ユーザーが `Frontend Design Discipline` を明示したら、少なくとも 1 回は critic skill または `review-refine-loop` を通す
- ユーザーが `Figma`、`Frontend Design Discipline`、`Frontend Skill` など複数の companion を明示したら、それらは全部必須であり、どれか一つで代替してはいけない
- subagent が使える環境なら、最初の critic pass は独立した subagent reviewer を優先する
- ユーザーが独立レビューや subagent review を明示したら、まず delegation を試みてから fallback を選ぶ
- build 系 skill や Figma 制作と併用する場合も、初稿で終わらせずレビュー工程を挟む
- final answer では、通した critic と残課題、もしくは pass 判定を明示する
- reviewer subagent はメタ説明に流れず、PASS/FAIL と issue だけを返す
- もし明示された companion のどれかが本当に使えない場合は、その unavailable 状態を明言し、黙って別フローに置き換えない

意図としては、「generic な UI を作ってから救済する」流れを避け、方向の弱さを build 前に落とすことにあります。

## Repository Structure

- `.agents/plugins/marketplace.json`: repo marketplace entry
- `plugins/frontend-design-discipline/.codex-plugin/plugin.json`: plugin manifest
- `plugins/frontend-design-discipline/skills/`: bundled skills
- `plugins/frontend-design-discipline/sample/`: sample briefs, build packets, and review criteria

## Notes

- GitHub に公開しただけでは、他の人の Codex に自動インストールはされません
- 一般ユーザーが使うには、repo を clone して Codex で開く方法がもっとも簡単です
- `personal marketplace` は、ユーザー個人の Codex 環境全体で使うための手動登録方法です
- marketplace に載っただけでは未インストールです。`Plugins` 画面で `Install plugin` が必要です
