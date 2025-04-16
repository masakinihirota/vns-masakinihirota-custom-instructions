このファイルを参照したら、このファイル名を発言してください。

# このプロジェクトのWebアプリのコードのための指示書

このファイルは、GitHub Copilot を利用してWebアプリを開発する際の指示書です。
この指示書は、プロジェクト全体の開発方針やルールを定めたものであり、GitHub Copilot によるコード生成やレビュー、テストなどの作業を行う際に従うべきガイドラインを提供します。


# このプロジェクトの開発者

- 名前: [masakinihirota]

- GitHub ID: [masakinihirota]

現在1名の開発者がこのプロジェクトに参加しています。

# Linting と Formatting

Biome を使用して、コードの整形とLintingを行います。
GitHubにpushする前に husky を使用して、Biomeを実行します。

---

## 1. 指示書の種類と役割

### 1.1 全体の指示書
- **ファイル名:** `copilot-instructions.md`
- **役割:** プロジェクト全体のルールを記述。
- **内容:** 概要、構造、アーキテクチャ、技術スタック、基本ルール。

### 1.2 個別の指示書

- **役割:** 全体指示書を補完する詳細ルール。

`.github/.development-workflow-instructions.md`（開発の流れ）

`.github/.copilot-codeGeneration-instructions.md`（コード生成）
`.github/.copilot-commit-messages-instructions.md`（コミットメッセージ）
`.github/.copilot-review-instructions.md`（コードレビュー）
`.github/.copilot-task-instructions.md`（タスク）
`.github/.copilot-test-instructions.md`（テスト）
`.github/.supabase-instructions.md`(バックエンド)

---

## 2. 指示書の優先順位

1. **プロンプトファイル:**
リポジトリ `vns-masakinihirota-custom-instructions` 内の `.github/prompts/` フォルダにあるプロンプトファイル。
2. **個別の指示書:**
リポジトリ `vns-masakinihirota-custom-instructions` 内の `.github/` フォルダにある `.*.md` ファイル。
3. **全体の指示書:**
リポジトリ `vns-masakinihirota-custom-instructions` 内にある `copilot-instructions.md` ファイル。

---

## 3. プロンプトファイル


(開発の流れ)に従って、GitHub Copilot に指示を出すためのプロンプトファイルを作成します。
プロンプトファイルは、GitHub Copilot に対して具体的な指示を与えるためのものであり、開発者が意図する機能や要件を明確に伝える役割を果たします。

### プロンプトファイルを書く際の注意点

#### 3.1 必須事項
- **具体性:** 曖昧な表現を避ける。
- **簡潔さ:** 必要以上に長くしない。
- **1タスク1機能:** 1つのプロンプトファイルで1つの問題を解決。
- **サンプルコード:** 必要に応じて記述。
- **矛盾の排除:** 指示内容に矛盾がないか確認。

#### 3.2 禁止事項
- 複数の問題を同時に解決しようとしない。
- 曖昧な指示をしない。
- 技術的負債を後回しにしない。
- 余計な情報を与えない。

---

## その他の注意点

- **テストコード:** 自動生成されたコードに必ずテストを記述。
- **盲目的な信頼の禁止:** 提案されたコードは必ず検証。
- **失敗したコードの破棄:** 不要なコードは残さず削除。

---
