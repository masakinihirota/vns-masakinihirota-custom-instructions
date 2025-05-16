# このリポジトリの使い方

このリポジトリは、GitHub Copilotへの指示書を管理するためのものです。以下に、このリポジトリの構造と使用方法について説明します。

このリポジトリでは
* GitHub Copilotへの指示書ファイル群
* タスク関連のファイル群
を管理しています。


# 指示書

## copilot-instructions.md

VSCodeがGitHub Copilotへの指示を最初に読み込むファイルです。

GitHub Copilotへの起点となる指示書です。
指示書の全体像(指示書のファイル配置)を設定します。
個別の指示書やプロンプトファイル(=実装用のファイル)の場所を指定します。

開発の全体の流れを記載しておきます。

たとえば、開発の全体の背骨であるタスクリストを更新するための方法を決めておきます。

## .github/*

個別の指示書を配置するフォルダです。

```
vns-masakinihirota-custom-instructions
├── .github/
│   ├── supabase/
│   │   ├── .supabase-instructions.md
│   │   ├── code-format-sql.md
│   │   ├── database-create-migration.md
│   │   ├── database-functions.md
│   │   ├── database-rls-policies.md
│   │   ├── declarative-database-schema.md
│   │   ├── edge-functions.md
│   │   ├── nextjs-supabase-auth.md
│   │   └── README.md
│   ├── .context7-instructions.md
│   ├── .copilot-character-instructions.md
│   ├── .copilot-codeGeneration-instructions.md
│   ├── .copilot-commit-message-instructions.md
│   ├── .copilot-review-instructions.md
│   ├── .copilot-task-instructions.md
│   └── .copilot-test-instructions.md

```

個別の指示書の場所を指定します。

## *.prompt.md

プロンプトファイル(=実装用のファイル)の場所を指定します。
プロンプトファイルは、GitHub Copilotが実装を行うための具体的な指示を記載するファイルです。

## task-list.md
タスクリストを管理するためのファイルです。
タスクの状態を管理するために、以下のフォルダを作成しています。
- `todo/`: 未着手のタスクを格納します。
- `doing/`: 現在作業中のタスクを格納します。
- `done/`: 完了したタスクを格納します。
- `archived/`: 完了後、一定期間経過したタスクを保管します.
# README.md

---




# このフォルダの構造

```
vns-masakinihirota-custom-instructions
├── .github
│   ├── supabase
│   │   ├── .supabase-instructions.md
│   │   ├── code-format-sql.md
│   │   ├── database-create-migration.md
│   │   ├── database-functions.md
│   │   ├── database-rls-policies.md
│   │   ├── declarative-database-schema.md
│   │   ├── edge-functions.md
│   │   ├── nextjs-supabase-auth.md
│   │   └── README.md
│   ├── .context7-instructions.md
│   ├── .copilot-character-instructions.md
│   ├── .copilot-codeGeneration-instructions.md
│   ├── .copilot-commit-message-instructions.md
│   ├── .copilot-review-instructions.md
│   ├── .copilot-task-instructions.md
│   └── .copilot-test-instructions.md
├── tasks
│   ├── archived
│   ├── doing
│   ├── done
│   └── todo
├── copilot-instructions.md
├── README.md
└── TASK_LIST.md
```

---

## 各フォルダ、ファイルの役割

- `.github/`: 個別の指示書を格納します。Supabaseやタスク管理、コードレビューなどの指示書が含まれます。
- `tasks/`: タスクの状態ごとにフォルダを分けて管理します。
  - `todo/`: 未着手のタスクを格納します。
  - `doing/`: 現在作業中のタスクを格納します。
  - `done/`: 完了したタスクを格納します。
  - `archived/`: 完了後、一定期間経過したタスクを保管します。
- `copilot-instructions.md`: GitHub Copilotへの全体的な指示書を記載します。
- `TASK_LIST.md`: タスク全体のリストを管理します。

---

## 指示書の構造

`copilot-instructions.md`
このワークスペースでの vns-masakinihirotaプロジェクトを開発するためのGitHub Copilotへの全体の指示書です。

`.github`フォルダ以下にGitHub Copilotへの指示書が格納されています。

`.github/supabase`フォルダ以下にSupabaseに関する指示書が格納されています。Supabaseの機能や設定に関する詳細な指示が含まれています。

---

## このリポジトリの目的

このリポジトリは、GitHub Copilotを活用した効率的な開発をサポートするための指示書を管理します。タスク管理や指示書の作成を通じて、プロジェクトの進行をスムーズに進めることを目指します。
