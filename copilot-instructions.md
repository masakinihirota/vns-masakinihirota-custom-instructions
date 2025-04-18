このファイルを参照したら、このファイル名を発言してください。


# プロジェクト全体の指示書

このファイルは、GitHub Copilot を利用してWebアプリを開発する際の指示書です。
プロジェクト全体の開発方針やルールを定めたものであり、GitHub Copilot によるコード生成やレビュー、テストなどの作業を行う際に従うべきガイドラインを提供します。

## 1. 指示書の種類と役割

これらの指示書を参照してください。

### 1.1 全体の指示書
- **ファイル名:** `copilot-instructions.md`
- **役割:** プロジェクト全体のルールを記述。
- **内容:** 概要、使用する指示書、指示書ファイルの優先順位の決定、ワークフロー。

全体の指示書は1つのみです。

### 1.2 使用する個別の指示書

- **ファイル名:**
`.github/.copilot-codeGeneration-instructions.md`（コード生成）
`.github/.copilot-commit-messages-instructions.md`（コミットメッセージ）
`.github/.copilot-review-instructions.md`（コードレビュー）
`.github/.copilot-task-instructions.md`（タスク）
`.github/.copilot-test-instructions.md`（テスト）
`.github/.supabase-instructions.md`(Supabase)
`.github/.context7-instructions.md`(コンテキスト)
`.github/.figma-instructions.md`(Figma)

- **役割:**
特定のタスクや機能に関する詳細な指示書。
全体指示書を補完する詳細ルール。

#### 1.2.1 個別の指示書の例
- **例:** `.github/.copilot-example.instructions.md`

### 1.3 使用するプロンプトファイル
- **ファイル名:** `prompts/*.md`
- **役割:** AIに具体的な指示を与えるためのファイル。
- **内容:** 各タスクに対する具体的な指示や要件を記述。
- **内容:** プロンプトファイルは、GitHub Copilot に対して具体的な指示を与えるためのものであり、開発者が意図する機能や要件を明確に伝える役割を果たします。
例えば、特定のAPIエンドポイントを実装するための指示や、特定のデータベースクエリを生成するための指示などが含まれます。

#### 1.3.1 プロンプトファイルの例
- **例:** `prompts/example.prompt.md`



---

## 2. 指示書の優先順位

この順番通りに指示書を参照してください。

1. **プロンプトファイル:**
リポジトリ `vns-masakinihirota-custom-instructions` 内の `prompts/`フォルダにあるプロンプトファイル(例: example.prompt.md)。

2. **個別の指示書:**
リポジトリ `vns-masakinihirota-custom-instructions` 内の `.github/` フォルダにある `.*.md` ファイル。
3. **全体の指示書:**
リポジトリ `vns-masakinihirota-custom-instructions` 内にある `copilot-instructions.md` ファイル。



---

## 3. プロンプトファイル

プロンプトファイルは、GitHub Copilot に対して具体的な指示を与えるためのファイルです。
プロンプトファイルは、開発者が意図する機能や要件を明確に伝える役割を果たします。
例えば、特定のAPIエンドポイントを実装するための指示や、特定のデータベースクエリを生成するための指示などが含まれます。

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

#### 3.3 使用しないプロンプトファイル

プロンプトファイルは
* 実装前
* 実装中
* 実装後
の3つの状態に分けて管理します。

実装中以外のプロンプトファイルを無視するようにします。
この確実にするために、
実装前のプロンプトファイルは`task-list/`フォルダに置いておきます。
実装中のプロンプトファイルは`prompts/`フォルダに置いておきます。
実装後のプロンプトファイルは`completes/`フォルダに置いておきます。



## 4 使用するツール

MCP（Microsoft Copilot）を使用します。
Figma MCP
Supabase MCP
GitHub Copilot MCP


---

## 5. 開発フロー

1. **設計書作成:** vns-masakinihirota-design で全体構想と設計を作成します。

2. **タスク分解:** 設計書の内容を元に、各機能や要件を具体的なタスクに落とし込みます。
   - 各タスクは1つの機能や要件に対応させる
   - 適切な粒度で分割し、進捗管理を容易にする
   - 機能の重要度に基づいて優先順位を設定する

3. **タスクリスト登録:** 分解したタスクをtask-listフォルダにファイルを作成して保存します。
タスクリストはこのプロジェクトの進捗を管理するためにも使用します。

4. **プロンプトファイル作成:** 各タスクについて、GitHub Copilotへの詳細な実装指示を含むプロンプトファイルを作成します。
プロンプトファイルはGitHub Copilotが理解しやすい形式で設計意図を伝えます。
作成したプロンプトファイルは「vns-masakinihirota-custom-instructions」リポジトリの `task-list/` フォルダに格納します。

5. **コード生成:** GitHub Copilotを使用して、プロンプトファイルに基づきコードを生成します。
すべての工程は「vns-masakinihirota-custom-instructions」リポジトリの指示書に従って進めます。
生成されたコードは「vns-masakinihirota」リポジトリに格納します。

6. **コードレビュー:** 生成されたコードをレビューし、必要に応じて修正を行います。

7. **テスト実施:** 実装されたコードのユニットテスト、統合テスト、E2Eテストなどを実施し、動作確認を行います。

8. **デプロイ:** テストに合格したコードを本番環境にデプロイします。

9. **フィードバック収集:** ユーザーからのフィードバックを収集し、改善点を洗い出します。

10. **改善サイクル:** 収集したフィードバックをもとに設計書を更新し、必要に応じて新たなタスクを作成します。



---

## その他の注意点

- **テストコード:** 自動生成されたコードに必ずテストを記述。
- **盲目的な信頼の禁止:** 提案されたコードは必ず検証。
- **失敗したコードの破棄:** 不要なコードは残さず削除。
