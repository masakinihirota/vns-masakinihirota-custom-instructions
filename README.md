# GitHub Copilot 指示書リポジトリ

このリポジトリは、GitHub Copilotの指示書を管理するためのものです。他のWebアプリのリポジトリと連携して利用します。

---

## 利用方法

### 初期設定
1. **設計書の確認:** 設計書を確認し、プロジェクトの全体像を把握します。
2. **テンプレートの確認:** Webアプリのテンプレートを確認します。
3. **環境変数の設定:** 環境変数を手動で設定します。
4. **ソース整形ツールの設定:** BiomeやPrettierを設定します。
5. **タスクの確認:** タスクリストを確認します（初期状態では空）。
6. **メモリーバンクの確認:** メモリーバンクを確認します（初期状態では空）。
7. **指示書の確認:** GitHub Copilotがどの指示書を読み込んでいるか、ルールをどのように認識しているかを確認します。

---

## 複数リポジトリの統合方法

複数のGitリポジトリを共通のGitHub Copilotルールで利用するために、**VS Codeのワークスペース**を使用します。

### ワークスペースの作成手順
1. **VS Codeを起動**し、「ファイル」→「ワークスペースをフォルダーに追加...」を選択。
2. 指示書リポジトリとコードリポジトリを追加。
3. 「ワークスペースを名前を付けて保存...」でワークスペースファイルを保存（例: `my-project.code-workspace`）。
4. ワークスペースを開き、GitHub Copilotに指示書を読ませてコード生成を指示。

---

## リポジトリ構成

以下のリポジトリをVS Codeワークスペースで統合します。

1. **指示書リポジトリ:** `vns-masakinihirota-custom-instructions`（このリポジトリ）
2. **Webアプリリポジトリ:** `vns-masakinihirota`
3. **設計書リポジトリ:** `vns-masakinihirota-design`
4. **タスクリストリポジトリ:** `vns-masakinihirota-design-task-list`
5. **公開ドキュメントリポジトリ:** `vns-masakinihirota-doc`

---

## 指示書の種類

### 1. 全体の指示書
- **ファイル名:** `.github/copilot-instructions.md`
- **役割:** プロジェクト全体のルールを記述。

### 2. 個別の指示書
- **例:** `.copilot-codeGeneration-instructions.md`（コード生成）、`.copilot-test-instructions.md`（テスト）。
- **役割:** 全体指示書を補完する詳細ルール。

### 3. プロンプトファイル
- **フォルダ:** `.github/prompts/`
- **役割:** 1タスク1機能の詳細な実装指示を記述。

---

## 確認・チェック・範囲

### 確認
- **指示書ファイルの存在確認:** GitHub Copilotがどの指示書を読み込むか確認。

### チェック
- **重複チェック:** 指示書内で同じ指示が重複していないか確認。
- **無効チェック:** 古い情報や無効な指示がないか確認。

### 範囲
- 指示書が長くなりすぎないように分割を検討（例: 機能ごと、担当者ごと、指示の種類ごと）。

---

## 注意点

1. **タスク分解:** 設計書からタスクを分解し、タスクリストに登録。
2. **メモリーバンク:** 開発の記録を残し、GitHub Copilotに継続的なコンテキストを提供。
3. **指示書の更新:** プロジェクトの進行に応じて指示書を更新。
4. **セキュリティ:** 環境変数や機密情報は`.gitignore`で管理。

---

## 参考リンク
- [VSCode(ネイティブ)にMCPを設定してSupabaseを操作する](https://qiita.com/masakinihirota/items/b5ae692191d197eb5ad7)
- [Clineが記憶喪失にならないようにMemory Bankを使う](https://qiita.com/reoring/items/0c359cc4323bf89965a1)
- [クライン メモリー バンク | クライン](https://docs.cline.bot/improving-your-prompting-skills/cline-memory-bank)
- [GitHub Copilot AgentモードでもMemory Bankを使えるようにしてみる](https://qiita.com/getty104/items/68bfdd8e24ab5afbc676)








