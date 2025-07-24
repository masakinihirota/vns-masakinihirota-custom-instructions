---
applyTo: "**"
---

このファイルを参照したら、このファイル名を発言してください。

VS Code でチャット応答をカスタマイズする
https://code.visualstudio.com/docs/copilot/copilot-customization#_prompt-files-experimental

## 1. はじめに
このファイルは、GitHub Copilotがプロジェクトの指示書を適切に読み込むためのガイドです。
プロジェクトの一貫性と品質を保ちながら、効率的な開発を実現します。

このファイルは、masakinihirota Web アプリ開発のための全体指示書です。開発方針・ルール・ワークフロー・運用方法を明確にし、誰でも迷わず開発できることを目指します。

---

## 2. 指示書の種類と役割

### 2.1. 指示書一覧
以下はプロジェクト内で使用される指示書の種類です：

1. **コード生成指示書**
   - ファイル名: `.copilot-codeGeneration-instructions.md`
   - コード生成時のルールや規約を定義します。

2. **コミット指示書**
   - ファイル名: `.copilot-commit-message-instructions.md`
   - コミットメッセージの書き方やルールを定義します。

3. **デザイン指示書**
   - ファイル名: `.copilot-design-system-instructions.md`
   - UIコンポーネントのデザインルールを定義します。

4. **命名規則指示書**
   - ファイル名: `.copilot-namingConventions-instructions.md`
   - 変数名や関数名、ファイル名の命名規則を定義します。

5. **レビュー指示書**
   - ファイル名: `.copilot-review-instructions.md`
   - コードレビューのルールや手順を定義します。

6. **タスク指示書**
   - ファイル名: `.copilot-task-instructions.md`
   - タスクの進行方法や管理ルールを定義します。

7. **テスト指示書**
   - ファイル名: `.copilot-testing-instructions.md`
   - テストの実施方法や基準を定義します。

8. **その他の指示書**
   - **ドキュメント指示書**: `.copilot-document-instructions.md`
   - **Figma指示書**: `.figma-instructions.md`

### 2.2. 個別指示書
- **conform指示書**: `.copilot-conform-instructions.md`
- **Supabase指示書**: `supabase/.supabase-instructions.md`
- **設計指示書**: `vns-masakinihirota-design/_design-instructions.md`
- **キャラクター指示書**: `.copilot-character-instructions.md`
- **コンテキスト指示書**: `.context7-instructions.md`

---

## 3. 指示書の読み込みルール

### 3.1. 優先順位
指示書を読み込む際の優先順位は以下の通りです：
1. **タスクファイル**（`_tasks/doing/`内のプロンプトファイル）
2. **個別指示書**（`.github/`内の `*-instructions.md`ファイル）
3. **全体指示書**（プロジェクト全体のルールを定義したファイル）

---

## 3. 参照ファイル・用語集

- 設計書: `vns-masakinihirota-design/`
- タスクリスト: `tasks.md`
- タスク詳細: `_tasks/`配下
- 用語集: `vns-masakinihirota-doc/用語.md`

---

## 4. 開発フロー

1. **設計書作成**: `vns-masakinihirota-design`で全体構想・設計を作成
2. **タスク分解**: 設計内容をタスク化し`_tasks/todo/`に登録
3. **タスク進行**: `_tasks/doing/`へ移動し、`tasks.md`を更新
4. **コード生成**: タスクファイルを元に GitHub Copilot でコード生成
5. **コードレビュー**: レビュー・修正
6. **テスト**: ユニット・統合・E2E テスト
7. **デプロイ**: テスト合格後に本番環境へ
8. **フィードバック・改善**: ユーザーの声を反映し設計・タスクを更新

> タスクが進まない場合や不明点は、`blocked/`や`waiting_for_review/`フォルダを活用し、必ず`tasks.md`を更新してください。

---

## 5. タスク管理ルール

- 新規タスクは`_tasks/todo/`に作成し、進行時は`doing/`、完了時は`done/`、古いものは`archived/`へ
- ファイル名は`YYYYMMDD-タスクID-タスク名-種類.prompt.md`形式
- タスク移動時は`tasks.md`のリンクも必ず更新
- 必要に応じて`blocked/`や`waiting_for_review/`も利用

---

## 6. コーディング・運用ルール

- **盲目的な信頼禁止**: 提案コードは必ず検証
- **不要コードの削除**: 失敗・不要なコードは残さず削除
- **コミット/プッシュ時の自動チェック**: husky で`pnpm check`（コミット時）、`pnpm run build`（プッシュ時）を実行。build 失敗時は push 中止
- **セキュリティ・品質重視**: API キーや秘密情報は環境変数で管理。エラー時は意味のあるメッセージと段階的なデバッグ手順を記載

---

## 7. 使用ツール

- MCP（Model Context Protocol）

"playwright"
"mcp-installer"
"Framelink Figma MCP"
"fetch"
"supabase"
"Postgres(LOCAL-supabase)"
"sequential-thinking"
"server-postgres"
"context7"
"file-system"
"mcp-server-time"
"@buger/docs-mcp"
"@smithery-ai/fetch"

---

## 8. 指示書の運用・更新

- 新規参加者は本ファイルと`README.md`を最初に読むこと

---

## 9. 例外・エラー時の対応

- タスクが進まない・不明点がある場合は、`blocked/`や`waiting_for_review/`に移動し、`tasks.md`に理由を明記
- 指示書や設計書に不明点がある場合は、必ずチームに相談

---

## 10. Tips（運用のコツ）

- セクションごとに「目的」「手順」「注意点」を明記すると迷いが減ります
- 定期的な見直し・アップデートを忘れずに
- 新規参加者や初学者にも分かりやすい表現を心がけましょう
- GitHub 関連の操作はすべて GitHub MCP を使用すること。

---

## 11. デザインルール

UI などを作る時は、
`.copilot-design-system-instructions.md`
を読み込んでデザインのルールを統一してください。
