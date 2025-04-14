このファイルを参照したら、このファイル名を発言してください。

GitHub Copilot
Webアプリの開発方針

# このプロジェクトのWebアプリのコードのための指示書

このファイルは、GitHub Copilot を利用してWebアプリを開発する際の指示書です。
この指示書は、プロジェクト全体の開発方針やルールを定めたものであり、GitHub Copilot によるコード生成やレビュー、テストなどの作業を行う際に従うべきガイドラインを提供します。

## 1. 指示書の全体像と優先順位

開発プロセスでは、複数の指示書ファイルを参照します。

### 指示書のファイル構成

```
vns-masakinihirota-custom-instructions
└── .github
    ├── prompts        (プロンプトファイル)
    │   ├── completes # (実装を終えたプロンプトファイル)
    │   └── [プロンプトファイル].prompt.md # (実装中のプロンプトファイル)
    ├── .copilot-codeGeneration-instructions.md # コード生成指示 (個別の指示書)
    ├── .copilot-commit-message-instructions.md # コミットメッセージ指示 (個別の指示書)
    ├── .copilot-review-instructions.md       # レビュー指示 (個別の指示書)
    ├── .copilot-task-instructions.md         # タスク指示 (個別の指示書)
    ├── .copilot-test-instructions.md         # テスト指示 (個別の指示書)
    ├── .supabase-instructions.md             # Supabase連携指示 (個別の指示書)
    └── copilot-instructions.md               # このファイル (全体指示)


vns-masakinihirota-design-task-list
├──_task-list-template.md          # タスクリストのテンプレート
├──_task-list.md                       # タスクリスト
└── [プロンプトファイル].prompt.md # 実装予定のプロンプトファイル

```

設計書から
タスクリストを作り
タスクリストからプロンプトファイル(=詳細な情報を入力した実装書)
を作成します。

実装時には
プロンプトファイルを

```
vns-masakinihirota-custom-instructions
└── .github
    └── prompts        (プロンプトファイル)

```

に移動して実装の作業を行います。







