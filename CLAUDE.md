# atena-studio

<!-- このリポジトリのルールの正本。AGENTS.md（Codex 用）はここを指すだけ -->

## 概要

名簿 CSV から宛名ラベル・受講票・名札・見積書などをブラウザだけで作る帳票ツール（public）。サーバー不要、データはブラウザの外に送らない。
機能と今後の展開は README.md、設計は DESIGN.md、予定は ROADMAP.md。

## よく使うコマンド

| 用途 | コマンド |
|---|---|
| install | `（未定）` |
| dev | `（未定）` |
| lint | `（未定）` |
| test | `（未定）` |
| build | `（未定）` |

## レーン

`full`（正本は `tasks/current.md` の1行目。基準は `~/Projects/ai-dev-harness/policies/lanes.md`）

## 共通ルール

作業の前に `~/Projects/ai-dev-harness/bin/preflight` を実行し、`~/Projects/ai-dev-harness/policies/` を読むこと。

- git-flow.md：ブランチ → PR → CI・レビュー → テストが通れば AI がマージ
- agents.md：役割、1 Issue = 1 Agent = 1 Branch = 1 Worktree（`~/Projects/atena-studio.wt/<branch>/`）、交代の順番
- lanes.md：full / solo
- secrets.md：鍵の値は表示しない。`.env*` は .gitignore

## 完了の定義

- [ ] build・lint・test が通る
- [ ] `tasks/current.md` を更新した（現状／やり残し／次の1手）
- [ ] PR を作り、CI が通った
- [ ] full は、実装者と別の AI のレビューでラベル `qa-pass`（UI の変更ありは `ux-pass` も）が付いた。付かないうちはマージしない

## このリポジトリ固有のルール

- **main のルートがそのまま GitHub Pages で公開される**（legacy ビルド、source は main の `/`）。main に入った時点で本番。main への直接 push はしない（`.github/direct-push-allow` は空）
- `.nojekyll` がないので、ルートの Markdown（この CLAUDE.md など）も Pages でページとして公開される。public リポジトリなので中身は元から公開だが、鍵や個人情報は書かない
- public なので、コミットは noreply アドレス（REPOS.md の置き場所のルール）
