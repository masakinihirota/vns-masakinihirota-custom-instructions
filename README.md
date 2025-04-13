このリポジトリの使い方

開発に必要なリポジトリを揃えます。

## プロジェクト全体のリポジトリ

- **コードリポジトリ:** Webアプリのリポジトリを用意します。
- **指示書リポジトリ:** GitHub Copilotの指示書リポジトリを用意します。
- **設計書リポジトリ:** 設計書を管理するリポジトリを用意します。
- **タスクリストリポジトリ:** タスクリストを管理するリポジトリを用意します。
- **ドキュメントリポジトリ:** ドキュメントを管理するリポジトリを用意します。
- **サンプルリポジトリ:** サンプルコードを管理するリポジトリを用意します。

このリポジトリは指示書のリポジトリです。



----------------------------------------

# 指示書

指示書には、
VSCode本体のsettings.json
プロジェクトの*****.-custom-instructionsリポジトリ内の指示書郡
があります。

* settings.jsonは、VSCode本体の設定を行うためのファイルです。
この設定は、各自で自由に設定してください。
* *****-custom-instructionsリポジトリは、GitHub Copilotの指示書を管理するためのリポジトリです。

## 全体説明の指示書

README.md このファイル
README-copilot-instructions.md 指示書の書き方。

## プロジェクトのコードへの指示書

.github GitHub Copilotに直接命令をするファイル群
があります。

## GitHub Copilot 指示書リポジトリのファイル構成

```plaintext

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


