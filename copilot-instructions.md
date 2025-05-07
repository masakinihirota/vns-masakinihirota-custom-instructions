このファイルを参照したら、このファイル名を発言してください。

# プロジェクト全体の指示書

このファイルは、GitHub Copilotを利用してWebアプリを開発する際の全体的な指示書です。プロジェクトの開発方針やルールを定め、コード生成やレビュー、テストなどの作業を行う際に従うべきガイドラインを提供します。

---

## 指示書の種類と役割

### 役を演じてください。

Characterを演じるために次のファイルを読み込んでください。
`.github/.copilot-character-instructions.md`

このファイルには、GitHub Copilotに特定の役割を演じさせるための指示が含まれています。
この役割は、プロジェクトの特定のニーズに応じてカスタマイズされており、GitHub Copilotがより適切なコード生成やレビューを行うためのものです。


# プロジェクトメインルール

## ドメイン知識
ユーザーから渡されたファイル内容を分析して適切なドメイン知識のルールを適用してください。
優先順位の指定があれば守ってください。
指示書のファイル名にはそのドメイン知識の名前が含まれています。

### 1. 全体の指示書

このファイルです。
プロジェクト全体の指示のための指示書です。

- **ファイル名:** `copilot-instructions.md`
- **役割:** プロジェクト全体のルールを記述。
- **内容:** 概要、使用する指示書、指示書ファイルの優先順位、ワークフロー。

### 2. 個別の指示書

- **役割:** 特定のタスクや機能に関する詳細な指示書。全体指示書を補完する詳細ルール。

個別の指示書を使用して、特定のタスクや機能に関する詳細な指示を提供します。

これらの個別指示書は、全体指示書のルールを補完し、特定の作業時に優先的に参照してください。

#### ドメイン知識

- **ファイル名:** (ドメイン知識)
  - `.github/.copilot-codeGeneration-instructions.md`（コード生成）
  - `.github/.copilot-commit-message-instructions.md`（コミットメッセージ）
  - `.github/.copilot-review-instructions.md`（コードレビュー）
  - `.github/.copilot-task-instructions.md`（タスク）
  - `.github/.copilot-test-instructions.md`（テスト）
  - `.github/.context7-instructions.md`（コンテキスト）
  - `.github/.figma-instructions.md`（Figma）

  #### Supabase関連
  - `.github/supabase/.supabase-instructions.md`
  - `.github/supabase/code-format-sql.md`
  - `.github/supabase/database-create-migration.md`
  - `.github/supabase/database-functions.md`
  - `.github/supabase/database-rls-policies.md`
  - `.github/supabase/declarative-database-schema.md`
  - `.github/supabase/edge-functions.md`
  - `.github/supabase/nextjs-supabase-auth.md`



### 3. タスクリスト
- **ファイル名:** `TASK_LIST.md`
- **役割:** タスク全体を俯瞰するためのリスト。各タスクの状態（未着手、進行中、完了）を明確にし、リンクを通じて詳細ファイルにアクセスできるようにします。

例:

```markdown
# プロジェクトタスクリスト

- [ ] タスク001：ログインUI実装 (`tasks/todo/task_001_implement_login_ui.prompt.md`)
- [~] タスク002：ユーザーAPI実装 (`tasks/doing/task_002_implement_user_api.prompt.md`)
- [x] タスク003：データベース初期設定 (`tasks/done/task_003_database_setup.prompt.md`)

```

### 4. タスクファイル
- **ファイル名:** `*.prompts.md`
- **役割:** AIに具体的な指示を与えるためのファイル。
- **内容:** 各タスクに対する具体的な指示や要件を記述。

#### タスクファイルのフォーマット

* **役割**: 各タスクファイルは、個別のタスクに関する詳細な実装指示を記述します。
GitHub Copilotはこのファイルに基づいてコード生成などの作業を行います。

* **ファイル名**: 以下の命名規則に従います。
    * **フォーマット**: `[YYYYMMDD]-[タスクID]-[タスク名]-[タスクの種類].prompt.md`
        * `[YYYYMMDD]`: 作成日 (例: `20250416`)
        * `[タスクID]`: `_task-list.md` で割り当てられた一意のID (例: `001`)
        * `[タスク名]`: タスクの内容がわかる簡潔な名前 (例: `loginFeature`)
        * `[タスクの種類]`: 以下のいずれかのキーワードを使用します。
            * `feat`: 機能開発
            * `fix`: バグ修正
            * `test`: テスト関連
            * `doc`: ドキュメント関連
            * `refactor`: リファクタリング
            * `style`: スタイル調整
    * **プロンプトファイルの例**: `20250416-001-loginFeature-feat.prompt.md`

タスクファイルを生成後は`tasks/todo/`に保存してください。


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
生成されたコードは「vns-masakinihirota」リポジトリに出力して完成したアプリを作成します。
Gitのブランチは「dev」ブランチを使用します。

プロンプトファイルを使って、GitHub Copilotにコードを生成させます。
Webアプリを実装するうえで、プロンプトファイルが最も優先度が高いです。
プロンプトファイルだけでは足りない指示は、.github/.*****-instructions.mdファイルを参照してください。
copilot-instructions.mdに全体の指示が書かれています。

huskyを使用して、コミット時に `pnpm check` を実行します。
huskyを使用して、プッシュ時に `pnpm run build` を実行します。buildに失敗した場合はpushを中止します。



6. **コードレビュー:** 生成されたコードをレビューし、必要に応じて修正を行います。

7. **テスト実施:** 実装されたコードのユニットテスト、統合テスト、E2Eテストなどを実施し、動作確認を行います。

8. **デプロイ:** テストに合格したコードを本番環境にデプロイします。

9. **フィードバック収集:** ユーザーからのフィードバックを収集し、改善点を洗い出します。

10. **改善サイクル:** 収集したフィードバックをもとに設計書を更新し、必要に応じて新たなタスクを作成します。

---

## 指示書の優先順位

1. **タスクファイル:** `tasks/doing`フォルダ内のファイル。
2. **個別の指示書:** `.github/`フォルダ内のファイル。
3. **全体の指示書:** `copilot-instructions.md`。

---

## 開発フロー

1. **設計書作成:** `vns-masakinihirota-design`で全体構想と設計を作成。
2. **タスク分解:** 設計書を元にタスクを具体化し、`tasks/todo/`に登録。
3. **コード生成:** GitHub Copilotを使用してコードを生成。
4. **コードレビュー:** 生成されたコードをレビューし、必要に応じて修正。
5. **テスト:** ユニットテスト、統合テスト、E2Eテストを実施。
6. **デプロイ:** テスト合格後、本番環境にデプロイ。
7. **フィードバック:** ユーザーからのフィードバックを収集し、改善点を洗い出す。
8. **改善サイクル:** フィードバックを元に設計書を更新し、新たなタスクを作成。

---

## タスク管理の流れ

1. **タスク作成**: 新しいタスクを`tasks/todo/`に保存します。ファイル名には作成日や内容を含めると管理がしやすくなります。
   - 例: `20240416-001-loginFeature-feat.prompt.md`

2. **タスク進行**: 作業中のタスクを`tasks/doing/`に移動し、`TASK_LIST.md`に進行中として記載します。

3. **タスク完了**: 完了したタスクを`tasks/done/`に移動し、`TASK_LIST.md`を更新します。

4. **タスクアーカイブ**: 古いタスクを`tasks/archived/`に移動して整理します。

## 注意事項

- タスク詳細ファイルを移動した際は、`TASK_LIST.md`のリンクを忘れずに更新してください。
- 必要に応じて、`blocked/`や`waiting_for_review/`フォルダを追加して柔軟に対応してください。

---

## このリポジトリの目的

GitHub Copilotを活用した効率的な開発をサポートするため、指示書やタスク管理を通じてプロジェクトの進行をスムーズに進めることを目指します。

---

## 使用するツール

MCP（Model Context Protocol）を使用します。
Context7
Figma MCP
Supabase MCP
GitHub MCP



---

## 注意事項

- **テストコード:** 自動生成されたコードには必ずテストを記述。
- **盲目的な信頼の禁止:** 提案されたコードは必ず検証。
- **失敗したコードの破棄:** 不要なコードは残さず削除。
タスク詳細ファイルを移動した際は、TASK_LIST.mdのリンクを忘れずに更新してください。
