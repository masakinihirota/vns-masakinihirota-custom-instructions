---
applyTo: "**"
---

このファイルを参照したら、このファイル名を発言してください。

# GitHub Copilot 指示書管理ガイド

## 1. はじめに

このcopilot-instructions.mdは、GitHub Copilotがプロジェクトの指示書を適切に読み込むためのガイドです。
このガイドに従うことで、プロジェクトの一貫性と品質を保ちながら、効率的な開発を実現します。

どのタイミングでどの指示書を読み込むかの指示書の管理をしています。


### 1.1. このファイルの役割
このファイルは、`.github`以下に配置された指示書をAIが適切に読み込むためのガイドを提供します。

---

## 2. 指示書の種類と役割

### 2.1. 指示書の種類
`.github`以下には以下の種類の指示書が含まれます：
1. **コード生成指示書**
   - ファイル名: `.copilot-codeGeneration-instructions.md`
   - コード生成時のルールや規約を定義します。

2. **コミットの指示書**
   - ファイル名: `.copilot-commit-message-instructions.md`
   - コミットメッセージの書き方やルールを定義します。

3. **デザイン指示書**
   - ファイル名: `.copilot-design-system-instructions.md`
   - UIコンポーネントのデザインルールを定義します。

4. **命名規則指示書**
   - ファイル名: `.copilot-namingConventions-instructions.md`
   - 変数名や関数名、ファイル名の命名規則を定義します。

5. **レビューの指示書**
   - ファイル名: `.copilot-review-instructions.md`
   - コードレビューのルールや手順を定義します。

6. **タスク指示書**
   - ファイル名: `.copilot-task-instructions.md`
   - タスクの進行方法や管理ルールを定義します。

7. **テスト指示書**
   - ファイル名: `.copilot-testing-instructions.md`
   - テストの実施方法や基準を定義します。



### 個別の指示書

conformライブラリの指示書
 **conformの指示書**
   - ファイル名: `.copilot-conform-instructions.md`
   - コードのコンフォーマンスに関する指示を定義します。

 **supabase指示書**
   - ファイル名: `vns-masakinihirota-custom-instructions\.github\supabase\.supabase-instructions.md`
   - Supabaseに関する操作や設定方法を定義します。

### キャラクターの指示書
   - ファイル名: `.copilot-character-instructions.md`
   - AIのキャラクターや振る舞いを定義します。

### MCPの指示書
 **コンテキスト指示書**
   - ファイル名: `.context7-instructions.md`
   最新のコード情報を読み込むMCPです。

### その他の指示書
 ドキュメントの指示書
   - ファイル名: `.copilot-documentation-instructions.md`
   実装後や開発後に、それらの機能に関するドキュメントを作成する際のルールやフォーマットを定義します。



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

