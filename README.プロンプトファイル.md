

----------------------------------------
----------------------------------------

README.プロンプトファイル.md



----------------------------------------

# ソース

Customize chat responses in VS Code
https://code.visualstudio.com/docs/copilot/copilot-customization#_prompt-files-experimental

----------------------------------------

Prompt files (experimental)
プロンプトファイル（実験的機能）は、Markdownファイルとしてプロンプトを作成し、チャットで参照できる仕組みです。カスタムインストラクションが既存プロンプトを補足するのに対し、プロンプトファイルは独立したプロンプトとしてワークスペース内に保存・共有できます。これにより、よく使うタスクのテンプレート化、専門知識のコードベースへの蓄積、チーム全体でのAI活用の標準化が可能です。


----------------------------------------

# 指示書について

指示書とプロンプトファイルの2種類がある

## 指示書

`copilot-instructions.md`がベースとなる指示書
`.instructions.md`が👆の指示書に追加の指示書


## 設定項目

コードを書く目的ごとに採用される指示書

### カスタムインストラクション関連

- `chat.promptFiles (Experimental)`: プロンプト・インストラクションファイルの有効化
- `github.copilot.chat.codeGeneration.useInstructionFiles`: `.github/copilot-instructions.md` の指示をCopilotリクエストに追加するか
- `chat.instructionsFilesLocations (Experimental)`: インストラクションファイルの保存場所リスト（相対パス・globパターン対応）

| 設定値例              | 説明                                                                 |
| --------------------- | -------------------------------------------------------------------- |
| ["/path/to/folder"]   | 指定パスでインストラクションファイルを有効化。複数指定可。           |

- `github.copilot.chat.codeGeneration.instructions (Experimental)`: コード生成時に追加する指示セット
- `github.copilot.chat.testGeneration.instructions (Experimental)`: テスト生成時に追加する指示セット
- `github.copilot.chat.reviewSelection.instructions (Preview)`: 選択範囲レビュー用指示セット
- `github.copilot.chat.commitMessageGeneration.instructions (Experimental)`: コミットメッセージ生成用指示セット
- `github.copilot.chat.pullRequestDescriptionGeneration.instructions (Experimental)`: PRタイトル・説明生成用指示セット

### プロンプトファイル関連

- `chat.promptFiles (Experimental)`: プロンプト・インストラクションファイルの有効化
- `chat.promptFilesLocations (Experimental)`: プロンプトファイルの保存場所リスト（相対パス・globパターン対応）

| 設定値例              | 説明                                                                 |
| --------------------- | -------------------------------------------------------------------- |
| ["/path/to/folder"]   | 指定パスでプロンプトファイルを有効化。複数指定可。                   |









## プロンプトファイル

プロンプトファイルは `.prompt.md` という拡張子のMarkdownファイルです。

独立している指示書

## 他の指示書へのリンク

他の指示書を読み込む時に使用します。
相対パスで指定します。

Markdownリンク
[タイトル](相対パス)





----------------------------------------

# Next.jsでAIで使用される拡張子

```
.css
.json
.md
.mjs
.sql
.ts
.tsx
.yaml

```

## プロンプトファイルで適用する拡張子

### Next.js 全部

```
---
applyTo: "**/*.css, **/*.json, **/*.md, **/*.mjs, **/*.sql, **/*.ts, **/*.tsx, **/*.yaml"
---

```

### Next.js コンポーネント

```
---
applyTo: "**/*.json, **/*.ts, **/*.tsx"
---

```


### 全部

```
---
applyTo: "**"
---

```

### 構成

1. **（任意）ヘッダー（Front Matter形式）**

| プロパティ   | 説明                                                                                   |
| ------------ | -------------------------------------------------------------------------------------- |
| mode         | プロンプト実行時のチャットモード（ask, edit, agent）。デフォルトはagent。              |
| tools        | agentモードで利用可能なツール名の配列（例: terminalLastCommand, githubRepo）。         |
| description  | プロンプトの簡単な説明                                                                 |

2. **本文（プロンプト内容）**

チャットでプロンプトを書く形式と同じで、自然言語の指示や追加コンテキスト、他のプロンプトファイルへのリンクも可能です。Markdownの見出しやリスト、コードブロックも利用できます。

他のプロンプトファイルやインストラクションファイルはMarkdownリンク（相対パス）で参照します。パスはプロンプトファイルの場所からの相対パスで記述してください。

プロンプトファイル内では `${variableName}` 形式で変数参照ができます。利用可能な変数例：

- ワークスペース変数: `${workspaceFolder}`, `${workspaceFolderBasename}`
- 選択範囲変数: `${selection}`, `${selectedText}`
- ファイルコンテキスト変数: `${file}`, `${fileBasename}`, `${fileDirname}`, `${fileBasenameNoExtension}`
- 入力変数: `${input:variableName}`, `${input:variableName:placeholder}`（チャット入力から値を渡す）







## 





----------------------------------------

# 変数参照

プロンプトファイル内では、`${variableName}` という形式で変数を参照できます。
例えば、選択中のテキストやワークスペースのパスなどを動的に挿入できます。

利用可能な変数一覧:

- **ワークスペース変数**
  - `${workspaceFolder}`: ワークスペースのフルパス
  - `${workspaceFolderBasename}`: ワークスペースフォルダ名

- **選択範囲変数**
  - `${selection}`: 現在選択中のテキスト
  - `${selectedText}`: 選択されたテキスト

- **ファイルコンテキスト変数**
  - `${file}`: 現在のファイルのフルパス
  - `${fileBasename}`: ファイル名（拡張子付き）
  - `${fileDirname}`: ファイルのディレクトリ名
  - `${fileBasenameNoExtension}`: ファイル名（拡張子なし）

- **入力変数**
  - `${input:variableName}`: チャット入力欄から値を受け取る
  - `${input:variableName:placeholder}`: プレースホルダー付きで値を受け取る

これらの変数を活用することで、柔軟かつ再利用性の高いプロンプトを作成できます。







## 





## 





----------------------------------------

# プロンプトファイル例

```

---
mode: 'agent'
tools: ['githubRepo', 'codebase']
description: 'Generate a new React form component'
---
Your goal is to generate a new React form component based on the templates in #githubRepo contoso/react-templates.

Ask for the form name and fields if not provided.

Requirements for the form:
* Use form design system components: [design-system/Form.md](../docs/design-system/Form.md)
* Use `react-hook-form` for form state management:
* Always define TypeScript types for your form data
* Prefer *uncontrolled* components using register
* Use `defaultValues` to prevent unnecessary rerenders
* Use `yup` for validation:
* Create reusable validation schemas in separate files
* Use TypeScript types to ensure type safety
* Customize UX-friendly validation rules


```






## 日本語

```markdown
---
mode: 'agent'
tools: ['githubRepo', 'codebase']
description: '新しいReactフォームコンポーネントを生成します'
---
あなたの目標は、#githubRepo contoso/react-templates のテンプレートをもとに新しいReactフォームコンポーネントを生成することです。

フォーム名やフィールドが指定されていない場合は、必ず質問してください。

フォームの要件:
* フォームデザインシステムコンポーネントを使用: [design-system/Form.md](../docs/design-system/Form.md)
* フォーム状態管理には `react-hook-form` を使用
* フォームデータのTypeScript型を必ず定義
* registerを使ったアンコントロールドコンポーネントを推奨
* 不要な再レンダリングを防ぐため `defaultValues` を使用
* バリデーションには `yup` を使用
* 再利用可能なバリデーションスキーマは別ファイルで管理
* 型安全性を担保するためTypeScript型を活用
* UXに配慮したバリデーションルールをカスタマイズ

```



----------------------------------------

# サンプル2

```

---
mode: 'edit'
description: 'Perform a REST API security review'
---
Perform a REST API security review:

* Ensure all endpoints are protected by authentication and authorization
* Validate all user inputs and sanitize data
* Implement rate limiting and throttling
* Implement logging and monitoring for security events

```



## 





## 





----------------------------------------

# 具体例

```

ファイル構造ツリー
ワークスペース関連ファイル
/ (ワークスペースのルートフォルダ)
├── .github/
│   ├── copilot-instructions.md  <-- ワークスペース全体のカスタム命令。全てのチャットリクエストに自動適用。Visual Studio や GitHub.com でも検出される。
│   ├── instructions/           <-- ワークスペース内の特定タスク用命令ファイルのデフォルト格納場所。
│   │   ├── general.instructions.md   <-- 例: 汎用的なコーディング規約命令。
│   │   └── [目的].instructions.md   <-- 例: 特定の目的のための命令ファイル。
│   │                                    └> 同じフォルダ内の他の `.instructions.md` ファイルをMarkdownリンクで参照可能。
│   └── prompts/                <-- ワークスペース内のスタンドアロンプロンプトファイルのデフォルト格納場所。
│       ├── create-react-form.prompt.md  <-- 例: Reactフォーム生成用のプロンプトファイル。
│       └── [目的].prompt.md       <-- 例: 特定の目的のためのプロンプトファイル。
│                                    └> 同じフォルダ内の他の `.prompt.md` や `.instructions.md` をMarkdownリンクで参照可能 。
│                                    └> API仕様書など、他のコンテキストファイルも参照可能。
└── .vscode/                    <-- VS Code 設定フォルダ (一般的な場所)
    └── settings.json           <-- VS Code の設定ファイル。
                                    └> ここで直接カスタム命令を記述するか、
                                       **ワークスペース内にある `.instructions.md` ファイルなどを参照可能**。
                                    └> `chat.instructionsFilesLocations` や `chat.promptFilesLocations` で、上記以外のカスタムフォルダを指示ファイル/プロンプトファイルの場所として追加可能。


```





## 





## 





----------------------------------------

# 





## 





## 





----------------------------------------

# 





## 





## 





----------------------------------------

# 





## 





## 





----------------------------------------

# 





## 





## 





----------------------------------------

# 





## 





## 





----------------------------------------
----------------------------------------


