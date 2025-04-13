このリポジトリの使い方

開発に必要なリポジトリを揃えます。

## プロジェクト全体のリポジトリ

- **コードリポジトリ:** Webアプリのリポジトリを用意します。
- **指示書リポジトリ:** GitHub Copilotの指示書リポジトリを用意します。
- **設計書リポジトリ:** 設計書を管理するリポジトリを用意します。
- **タスクリストリポジトリ:** タスクリストを管理するリポジトリを用意します。
- **ドキュメントリポジトリ:** ドキュメントを管理するリポジトリを用意します。
- **サンプルリポジトリ:** サンプルコードを管理するリポジトリを用意します。

それぞれのリポジトリを用意します。

このリポジトリは指示書のリポジトリです。



----------------------------------------

指示書には、VSCode本体のsettings.jsonにGitHub Copilot個人で使うための指示書を書けます。
この設定は、各自で自由に設定してください。

このプロジェクト全体の指示書は
vns-masakinihirota-custom-instructionsリポジトリ内に作成します。



### 全体説明

README.md このファイル
README-copilot-instructions.md 指示書の書き方。
README-settings.json.md

### プロジェクトのコードへの指示書

.github GitHub Copilotに直接命令をするファイル群
があります。



VSCodeのワークスペース機能を使って複数のリポジトリをまとめて管理します。
GitHub Copilotはワークスペース内のファイルを見ています。

## ワークスペースの設定

VSCodeを開き、それぞれのリポジトリを登録します。

## 複数リポジトリをVSCodeのワークスペースで管理

複数のGitリポジトリを共通のGitHub Copilotルールで利用するために、**VS Codeのワークスペース**を使用します。

### ワークスペースの作成手順
1. **VS Codeを起動**し、「ファイル」→「ワークスペースをフォルダーに追加...」を選択。
2. 指示書リポジトリとコードリポジトリを追加。
3. 「ワークスペースを名前を付けて保存...」でワークスペースファイルを保存（例: `my-project.code-workspace`）。
4. ワークスペースを開き、GitHub Copilotに指示書を読ませてコード生成を指示。

👇ワークスペース設定のファイルに登録できます。

```[ワークスペース名].code-workspace
{
	"folders": [
		{
			"path": "リポジトリ名1"
		},
		{
			"path": "リポジトリ名2"
		}
	],
	"settings": {
		// ワークスペース専用の設定を書けます。
	}
}

```

ワークスペースの設定ファイルを
ワークスペースに登録したリポジトリのルートに置きます。

※ほかに、チームで共有する共通の拡張機能を登録できます。



# GitHub Copilot 指示書リポジトリのファイル群

このリポジトリは、GitHub Copilotの指示書を管理するためのものです。他のWebアプリのリポジトリと連携して利用します。

指示書リポジトリのファイル構成は以下のようになっています。

```plaintext
指示書
      👇️アプリコードの指示書
├── .github
│   ├── _memory-bank
│   ├── prompts
│   │   ├── completes
│   │   ├── 20250401-000-template.prompt.md
│   │   ├── 20250401-001-user-authentication-feat.prompt.md
│   │   └── 20250401-002-user-profile.prompt.md
│   ├── .copilot-codeGeneration-instructions.md
│   ├── .copilot-commit-message-instructions.md
│   ├── .copilot-review-instructions.md
│   ├── .copilot-task-instructions.md
│   ├── .copilot-test-instructions.md
│   ├── .supabase-instructions.md
│   └── copilot-instructions.md
│   👇️アプリコード以外の指示書
├── Next.js Supabase Rules.md
├── README-copilot-instructions.md
├── README-settings.json.md
└── README.md

```



## 利用手順

VSCodeのワークスペースを利用して、この指示書のリポジトリと、Webアプリのリポジトリ等をまとめます。

設計書をもとに、タスクリストを作成します。
タスクリストをもとに、指示書(プロンプトファイル)を作成します。
プロンプトファイルをもとに、GitHub Copilotに指示書を読ませて、コード生成を指示します。
GitHub Copilotが生成したコードをもとに、テストコードを作成します。

1. **設計書の用意:** 設計書を確認し、プロジェクトの全体像を把握します。
2. **テンプレートの用意:** Webアプリのテンプレートを用意します。
3. **環境変数の設定:** 環境変数を手動で設定します。
4. **ソース整形ツールの設定:** BiomeやPrettierを設定します。
5. **タスクの確認:** タスクリストを確認します（初期状態を空にします）。
6. **メモリーバンクの確認:** メモリーバンクを確認します（初期状態を空にします）。
7. **指示書の確認:** GitHub Copilotがどの指示書を読み込んでいるか、ルールをどのように認識しているかを確認します。



