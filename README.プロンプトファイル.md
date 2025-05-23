Customize chat responses in VS Code
https://code.visualstudio.com/docs/copilot/copilot-customization#_prompt-files-experimental

## Markdownリンク
他の指示書を読み込む時に使用します。

[タイトル](相対パス)

他の指示書を相対パスで指定します。

---

プロンプトファイルは独立しているファイルです。

`copilot-instructions.md`がベースとなる指示書
`.instructions.md`が追加の指示書

プロンプトファイル
`.prompt.md`が独立している指示書


内容

プロンプトファイル

```
---
applyTo: "**"
---

典型的な読み込む指示書のMarkdownリンク群

指示

``


---

変数参照

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

---

Prompt file examples

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



---



### 翻訳

$SELECTION_PLACEHOLDER$ に適した書き換え済みMarkdownコンテンツは以下の通りです。

---

## VS Codeでチャット応答をカスタマイズする
https://code.visualstudio.com/docs/copilot/copilot-customization#_prompt-files-experimental

### Markdownリンク
他の指示書を読み込む際に使用します。

- 書式: `[タイトル](相対パス)`
- 他の指示書を相対パスで指定してください。

---

プロンプトファイルは独立したファイルです。

- `copilot-instructions.md`: 基本となる指示書
- `.instructions.md`: 追加の指示書
- `.prompt.md`: 独立した指示書

---

#### 変数参照

プロンプトファイル内では `${variableName}` 形式で変数を参照できます。
例: 選択中のテキストやワークスペースのパスなどを動的に挿入できます。

**利用可能な変数一覧:**

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

これらの変数を活用することで、柔軟で再利用性の高いプロンプトを作成できます。

---

#### プロンプトファイル例

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

---



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

Markdown リンクを使用して API 仕様やドキュメントなどの追加のコンテキスト ファイルを参照し、Copilot にさらに完全な情報を提供します。



