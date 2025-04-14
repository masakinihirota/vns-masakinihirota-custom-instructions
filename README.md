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

# このリポジトリについて

このリポジトリは、GitHub Copilotへの指示書を管理するためのものです。

## このリポジトリについての説明

README.md このファイル
README-copilot-instructions.md 指示書の書き方。
README-development-workflow.md 開発フロー。

# 指示書

指示書には、
* VSCode本体のsettings.json
* プロジェクトの `.github/*****-instructions.md`リポジトリ内の指示書郡があります。

* settings.jsonは、VSCode本体の設定を行うためのファイルです。
この設定は、各自で自由に設定してください。

## GitHub Copilot 指示書リポジトリのファイル構成

このリポジトリは、GitHub Copilotの指示書を管理するためのものです。他のWebアプリのリポジトリと連携して利用します。

指示書リポジトリのファイル構成は以下のようになっています。

```plaintext
指示書
      👇️Webアプリ コードの指示書
├── .github
│   ├── .copilot-codeGeneration-instructions.md
│   ├── .copilot-commit-message-instructions.md
│   ├── .copilot-review-instructions.md
│   ├── .copilot-task-instructions.md
│   ├── .copilot-test-instructions.md
│   ├── .supabase-instructions.md
│   └── copilot-instructions.md
├── README-copilot-instructions.md
├── README-development-workflow.md
└── README.md

```


