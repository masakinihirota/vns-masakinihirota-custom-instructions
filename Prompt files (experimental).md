Prompt files (experimental)
プロンプトファイル（実験的機能）は、Markdownファイルとしてプロンプトを作成し、チャットで参照できる仕組みです。カスタムインストラクションが既存プロンプトを補足するのに対し、プロンプトファイルは独立したプロンプトとしてワークスペース内に保存・共有できます。これにより、よく使うタスクのテンプレート化、専門知識のコードベースへの蓄積、チーム全体でのAI活用の標準化が可能です。

VS Codeでは、プロンプトファイルに2種類のスコープがあります。

- **ワークスペースプロンプトファイル**: ワークスペース内のみで利用でき、`.github/prompts` フォルダに保存されます。
- **ユーザープロンプトファイル**: 複数ワークスペースで利用でき、現在のVS Codeプロファイルに保存されます。

**主なユースケース例:**

- コード生成: ReactフォームやAPIモックなど、コンポーネントやテスト、マイグレーション用の再利用可能なプロンプトを作成
- ドメイン知識共有: セキュリティ対策やコンプライアンスチェックなど、専門知識をプロンプトとして共有
- チームコラボレーション: 設計パターンやガイドラインをドキュメント化し、仕様やドキュメントへの参照を含める
- オンボーディング: 複雑な手順やプロジェクト固有のパターンを段階的にガイド

---

## プロンプトファイルの構造

プロンプトファイルは `.prompt.md` という拡張子のMarkdownファイルです。

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

---

## プロンプトファイル例

**Reactフォーム生成用プロンプト例:**

```markdown
---
mode: 'agent'
tools: ['githubRepo', 'codebase']
description: '新しいReactフォームコンポーネントを生成'
---
あなたの目標は、#githubRepo contoso/react-templates のテンプレートをもとに新しいReactフォームコンポーネントを生成することです。

フォーム名やフィールドが指定されていない場合は、質問してください。

要件:
* フォームデザインシステムのコンポーネントを使用: [design-system/Form.md](../docs/design-system/Form.md)
* フォーム状態管理には `react-hook-form` を使用
* フォームデータのTypeScript型を必ず定義
* registerを使ったアンコントロールドコンポーネントを推奨
* 不要な再レンダリングを防ぐため `defaultValues` を活用
* バリデーションには `yup` を使用
* バリデーションスキーマは別ファイルで再利用可能に
* TypeScript型で型安全性を担保
* UXに配慮したバリデーションルールをカスタマイズ
```

**REST APIセキュリティレビュー用プロンプト例:**

```markdown
---
mode: 'edit'
description: 'REST APIのセキュリティレビューを実施'
---
REST APIのセキュリティレビューを行ってください:

* すべてのエンドポイントが認証・認可で保護されているか確認
* ユーザー入力のバリデーションとデータのサニタイズ
* レートリミットやスロットリングの実装
* セキュリティイベントのログ記録と監視
```

**Tip:**
API仕様やドキュメントなど、追加のコンテキストファイルをMarkdownリンクで参照すると、Copilotがより正確に理解できます。

---

## ワークスペースプロンプトファイルの作成

ワークスペースプロンプトファイルは、ワークスペース内でのみ利用可能です。
デフォルトでは `.github/prompts` ディレクトリに配置します。`chat.promptFilesLocations` 設定で追加の保存場所も指定できます。

**作成手順:**

1. コマンドパレット（Ctrl+Shift+P）で「Chat: New Prompt File」を実行
2. プロンプトファイルの保存場所を選択
3. ファイル名を入力
4. Markdown形式でプロンプト内容を記述

または、直接 `prompts` フォルダに `.prompt.md` ファイルを作成してもOKです。

プロンプトファイル内では、他のワークスペースファイルをMarkdownリンク（例: `[index](../index.ts)`）や `#index.ts` 参照でリンクできます。他の `.prompt.md` ファイルやインストラクションファイルも同様に参照可能です。

---

## ユーザープロンプトファイルの作成

ユーザープロンプトファイルは、ユーザープロファイルに保存され、複数ワークスペースで再利用できます。

**作成手順:**

1. コマンドパレットで「Chat: New Prompt File」を実行
2. 保存場所に「User Data Folder」を選択
3. ファイル名を入力
4. Markdown形式でプロンプト内容を記述

他のユーザープロンプトファイルやインストラクションファイルも参照できます。

---

## ユーザープロンプトファイルの同期

VS CodeのSettings Sync機能で、ユーザープロンプトファイルを複数デバイス間で同期できます。

**同期手順:**

1. Settings Syncを有効化
2. コマンドパレットで「Settings Sync: Configure」を実行
3. 「Prompts and Instructions」を同期対象に追加

---

## チャットでプロンプトファイルを使う

- コマンドパレットで「Chat: Run Prompt」を実行し、プロンプトファイルを選択
- チャットビューで `/プロンプトファイル名` を入力
    - 例: `/create-react-form` や `/create-react-form: formName=MyForm`
- エディタでプロンプトファイルを開き、タイトルバーの再生ボタンを押す
    - 現在のチャットセッションで実行、または新規セッションで実行を選択可能

---

## 設定項目

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

---

### Tips

- プロンプトファイルはMarkdownで柔軟に記述できるので、見出しやリスト、コードブロックを活用して分かりやすく整理しましょう。
- 他のファイルやプロンプトへのリンクを積極的に使うことで、AIにより多くの文脈を与えられます。
- チームでプロンプトファイルを共有することで、ナレッジの属人化を防ぎ、開発効率が向上します。

困ったときは、どんな小さなことでも質問してください！一緒に成長していきましょう。
