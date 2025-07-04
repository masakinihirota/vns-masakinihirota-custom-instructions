---
applyTo: "**"
---

このファイルを参照したら、このファイル名を発言してください。

# GitHub Copilot 指示書管理ガイド

## 1. はじめに

### 1.1. このファイルの役割
このファイルは、`.github`以下に配置された指示書をAIが適切に読み込むためのガイドを提供します。

---

## 2. 指示書の種類と役割

### 2.1. 指示書の種類
`.github`以下には以下の種類の指示書が含まれます：

1. **コード生成指示書**
   - ファイル名: `.copilot-codeGeneration-instructions.md`
   - コード生成時のルールや規約を定義します。

2. **命名規則指示書**
   - ファイル名: `.copilot-namingConventions-instructions.md`
   - 変数名や関数名、ファイル名の命名規則を定義します。

3. **デザイン指示書**
   - ファイル名: `.copilot-design-system-instructions.md`
   - UIコンポーネントのデザインルールを定義します。

4. **テスト指示書**
   - ファイル名: `.copilot-testing-instructions.md`
   - テストの実施方法や基準を定義します。

5. **supabase指示書**
   - ファイル名: `vns-masakinihirota-custom-instructions\.github\supabase\.supabase-instructions.md`
   - Supabaseに関する操作や設定方法を定義します。


---

## 3. 指示書の読み込みルール

### 3.1. 優先順位
指示書を読み込む際の優先順位は以下の通りです：

1. **タスクファイル**（`_tasks/doing/`内のプロンプトファイル）
   - タスクごとの具体的な指示を最優先で読み込みます。

2. **個別指示書**（`.github/`内の `*-instructions.md`ファイル）
   - 特定の作業に関する詳細な指示を読み込みます。

3. **全体指示書**（プロジェクト全体のルールを定義したファイル）
   - 全体的なルールや規約を補足的に読み込みます。

---

## 4. 指示書の利用方法

### 4.1. コード生成時
- 必要に応じて、`.copilot-codeGeneration-instructions.md`を読み込み、コード生成のルールを適用します。

### 4.2. 命名規則の適用
- 変数名や関数名を生成する際は、`.copilot-namingConventions-instructions.md`を参照して命名規則を遵守します。

### 4.3. デザインルールの適用
- UIコンポーネントを設計する際は、`.copilot-design-system-instructions.md`を参照してデザインルールを統一します。

### 4.4. テストの実施
- テストコードを生成する際は、`.copilot-testing-instructions.md`を参照してテスト基準を満たすコードを生成します。

### 4.5. コンテキストの適用
- 特定のコンテキストに基づいた指示が必要な場合は、`.context7-instructions.md`を参照して適切なコンテキストを適用します。
- `.copilot-conform-instructions.md`を参照して、コンフォーマンスに関する指示を適用します。
- `.copilot-task-instructions.md`を参照して、タスクに関する指示を適用します。
- `.figma-instructions.md`を参照して、Figmaに関する指示を適用します。

### 4.6. Supabaseの指示書
- `.github/supabase/.supabase-instructions.md`を参照して、Supabaseに関する指示を適用します。


---

## 5. Tips

- **指示書の更新:** 指示書は定期的に見直し、最新のプロジェクト要件に合わせて更新してください。
- **指示書の明確化:** 各指示書には目的、手順、注意点を明記し、誰でも理解できる内容にしてください。
- **指示書の活用:** 必要に応じて指示書を読み込み、プロジェクトの一貫性と品質を維持してください。

---

この指示書を基に、`.github`以下の指示書を適切に管理し、プロジェクトの効率的な運用を実現してください。
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

