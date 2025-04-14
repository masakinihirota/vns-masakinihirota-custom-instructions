このファイルを参照したら、このファイル名を発言してください。

`README-copilot-instructions.md`
👆️このファイルはGitHub Copilotの指示書の書き方を説明するためのものです。

# GitHub Copilot 指示書の書き方

.githubフォルダの中にプロジェクトのWebアプリの指示書を管理するためのファイル群を用意します。

## 1. 指示書の種類と役割

### 1.1 全体の指示書
- **ファイル名:** `copilot-instructions.md`
- **役割:** プロジェクト全体のルールを記述。
- **内容:** 概要、構造、アーキテクチャ、技術スタック、基本ルール。

### 1.2 個別の指示書

- **役割:** 全体指示書を補完する詳細ルール。

`.copilot-codeGeneration-instructions.md`（コード生成）
`.copilot-commit-messages-instructions.md`（コミットメッセージ）。
`.copilot-review-instructions.md`（コードレビュー）。
`.copilot-task-instructions.md`（タスク管理）。
`.copilot-test-instructions.md`（テスト）。
`.copilot-*****-instructions.md`（その他のルール）。


---

## 2. 指示書の優先順位

1. **プロンプトファイル:** `.github/prompts/` 内のタスク指示書。
2. **個別の指示書:** `.github/` 内の `.copilot-*.md` ファイル。
3. **全体の指示書:** `copilot-instructions.md`。

---

## 3. 指示書を書く際の注意点

### 3.1 必須事項
- **具体性:** 曖昧な表現を避ける。
- **簡潔さ:** 必要以上に長くしない。
- **1タスク1機能:** 1つのプロンプトファイルで1つの問題を解決。
- **サンプルコード:** 必要に応じて記述。
- **矛盾の排除:** 指示内容に矛盾がないか確認。

### 3.2 禁止事項
- 複数の問題を同時に解決しようとしない。
- 曖昧な指示をしない。
- 技術的負債を後回しにしない。
- 余計な情報を与えない。

---

## 4. プロンプトファイルの例

### フォーマット
```markdown
## 指示書と優先順位

以下の指示書を参照し、優先順位に従って作業を進めてください。

### 指示書一覧
1. **全体のルール:** `.github/copilot-instructions.md`
2. **コード生成に関するルール:** `.github/.copilot-codeGeneration-instructions.md`
3. **テストに関するルール:** `.github/.copilot-test-instructions.md`

### 優先順位
1. `.github/.copilot-codeGeneration-instructions.md`
2. `.github/.copilot-test-instructions.md`
3. `.github/copilot-instructions.md`
```

---

## 5. MCP (Model Context Protocol)

- **ファイル名:** `mcp.json`
- **役割:** GitHub Copilot Agent Modeで使用する設定ファイル。

---

## 6. その他の注意点

- **テストコード:** 自動生成されたコードにも必ずテストを記述。
- **盲目的な信頼の禁止:** 提案されたコードは必ず検証。
- **失敗したコードの破棄:** 不要なコードは残さず削除。

---

