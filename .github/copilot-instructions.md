このファイルを参照したら、このファイル名を発言してください。

VS Codeでチャット応答をカスタマイズする
https://code.visualstudio.com/docs/copilot/copilot-customization#_prompt-files-experimental

# プロジェクト全体の指示書

このファイルは、masakinihirota Webアプリ開発のための全体指示書です。開発方針・ルール・ワークフロー・運用方法を明確にし、誰でも迷わず開発できることを目指します。

---

## 1. 指示書の種類と優先順位

1. **タスクファイル**（`_tasks/doing/`内のプロンプトファイル）
2. **個別指示書**（`.github/`内の `*-instructions.md`ファイル）
3. **全体指示書**（本ファイル）

> タスクファイルが最優先。足りない場合は個別指示書、さらに全体指示書の順で参照してください。

---

## 2. 指示書の役割

- **全体指示書（本ファイル）**: プロジェクト全体のルール・開発フロー・運用方法を記載
- **個別指示書**: コード生成・レビュー・テスト・コミットメッセージ等、特定作業の詳細ルール
- **タスクファイル**: 各タスクの具体的な実装指示

---

## 3. 参照ファイル・用語集

- 設計書: `vns-masakinihirota-design/`
- タスクリスト: `TASK_LIST.md`
- タスク詳細: `_tasks/`配下
- 用語集: `vns-masakinihirota-doc/用語.md`

---

## 4. 開発フロー

1. **設計書作成**: `vns-masakinihirota-design`で全体構想・設計を作成
2. **タスク分解**: 設計内容をタスク化し`_tasks/todo/`に登録
3. **タスク進行**: `_tasks/doing/`へ移動し、`TASK_LIST.md`を更新
4. **コード生成**: タスクファイルを元にGitHub Copilotでコード生成
5. **コードレビュー**: レビュー・修正
6. **テスト**: ユニット・統合・E2Eテスト
7. **デプロイ**: テスト合格後に本番環境へ
8. **フィードバック・改善**: ユーザーの声を反映し設計・タスクを更新

> タスクが進まない場合や不明点は、`blocked/`や`waiting_for_review/`フォルダを活用し、必ず`TASK_LIST.md`を更新してください。

---

## 5. タスク管理ルール

- 新規タスクは`_tasks/todo/`に作成し、進行時は`doing/`、完了時は`done/`、古いものは`archived/`へ
- ファイル名は`YYYYMMDD-タスクID-タスク名-種類.prompt.md`形式
- タスク移動時は`TASK_LIST.md`のリンクも必ず更新
- 必要に応じて`blocked/`や`waiting_for_review/`も利用

---

## 6. コーディング・運用ルール

- **盲目的な信頼禁止**: 提案コードは必ず検証
- **不要コードの削除**: 失敗・不要なコードは残さず削除
- **コミット/プッシュ時の自動チェック**: huskyで`pnpm check`（コミット時）、`pnpm run build`（プッシュ時）を実行。build失敗時はpush中止
- **セキュリティ・品質重視**: APIキーや秘密情報は環境変数で管理。エラー時は意味のあるメッセージと段階的なデバッグ手順を記載

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

- タスクが進まない・不明点がある場合は、`blocked/`や`waiting_for_review/`に移動し、`TASK_LIST.md`に理由を明記
- 指示書や設計書に不明点がある場合は、必ずチームに相談

---

## 10. Tips（運用のコツ）

- セクションごとに「目的」「手順」「注意点」を明記すると迷いが減ります
- 定期的な見直し・アップデートを忘れずに
- 新規参加者や初学者にも分かりやすい表現を心がけましょう
- GitHub 関連の操作はすべて GitHub MCP を使用すること。

---

## 11. デザインルール

UIなどを作る時は、
`.copilot-design-system-instructions.md`
を読み込んでデザインのルールを統一してください。
