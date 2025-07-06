git worktree機能を使ってAIで並列開発を行います。

# 開発中のdevブランチがあるメインのリポジトリで実行

```terminal
git worktree add ../task1 -b task1  # task1用のワークツリーとブランチを作成
git worktree add ../task2 -b task2  # task2用のワークツリーとブランチを作成
git worktree add ../task3 -b task3  # task3用のワークツリーとブランチを作成

```

# .env環境ファイルのコピー

作業ディレクトリごとに環境変数を設定する必要がある場合、`.env` ファイルをコピーして設定します。

```terminal
cp .env ../task1/.env
cp .env ../task2/.env
cp .env ../task3/.env

```

各ディレクトリの `.env` ファイルを編集し、必要な環境変数を設定してください。

その他のgitで追跡していないファイルで、開発に必要なファイルもコピーします。

---

# VSCodeのワークスペースに追加

作業ディレクトリを効率的に管理するために、VSCodeのワークスペースに追加します。

### 手順:
1. **VSCodeを開く**:
   - VSCodeを起動します。

2. **ワークスペースにフォルダを追加**:
   - メニューの「ファイル」 > 「フォルダを追加...」を選択し、以下の作業ディレクトリを追加します。
     - `../task1`
     - `../task2`
     - `../task3`

3. **ワークスペースを保存**:
   - メニューの「ファイル」 > 「名前を付けてワークスペースを保存...」を選択し、ワークスペースを保存します。


<!-- ここではAIでの並列開発をするので、複数のワークスペースを開きます。 -->
VSCodeのウィンドウを複製し、それぞれのタスク用のワークスペースを開きます。

task1, task2, task3のそれぞれのタスク用にVSCodeのウィンドウを開きます。
これは設計や指示書、ドキュメントは共有して、Webアプリ部分はそれぞれのgit worktreeのブランチを使用して並列開発を行います。
なので それぞれのワークスペースを保存する手順を書いてください。

インストールはその後です。

4. **ターミナルでコマンドを実行**:
   - VSCode内のターミナルを使用して、以下のコマンドを実行します。

```terminal
pnpm install
pnpm dev

```

これにより、すべての作業ディレクトリで依存関係のインストールと開発環境の起動が効率的に行えます。

---

# ワークスペースの保存手順 (1ワークスペースに1つのWebアプリのソースコード)

作業ディレクトリごとにVSCodeのワークスペースを保存する際、1つのワークスペースには1つのWebアプリのソースコードのみを含めるようにしてください。

### 手順:
1. **VSCodeを開く**:
   - VSCodeを起動します。

2. **それぞれの作業ディレクトリを開く**:
   - メニューの「ファイル」 > 「フォルダを開く...」を選択し、以下の作業ディレクトリを開きます。
     - `../task1`
     - `../task2`
     - `../task3`

3. **ワークスペースを保存**:
   - メニューの「ファイル」 > 「名前を付けてワークスペースを保存...」を選択し、各作業ディレクトリごとにワークスペースを保存します。
     - `task1.code-workspace`
     - `task2.code-workspace`
     - `task3.code-workspace`

4. **複数のウィンドウを開く**:
   - VSCodeのウィンドウを複製し、それぞれのワークスペースを開きます。

5. **設計や指示書の共有**:
   - 設計や指示書、ドキュメントは別のワークスペースで管理し、Webアプリ部分はそれぞれのブランチに対応するワークスペースで管理します。

これにより、各タスク用の作業ディレクトリを独立して管理できます。

---

# ワークスペースの設定手順 (AIで並列開発を行うための構成)

以下の手順に従って、VSCodeのワークスペースを設定し、AIで並列開発を効率的に行えるようにします。

### 手順:
1. **VSCodeを開く**:
   - VSCodeを起動します。

2. **ワークスペースにフォルダを追加**:
   - メニューの「ファイル」 > 「フォルダを追加...」を選択し、以下のフォルダを追加します。

#### ワークスペース1 (task1用):

```json
"folders": [
    {
        "name": "vns-masakinihirota-custom-instructions",
        "path": "vns-masakinihirota-custom-instructions"
    },
    {
        "name": "vns-masakinihirota-design",
        "path": "vns-masakinihirota-design"
    },
    {
        "name": "vns-masakinihirota-doc",
        "path": "vns-masakinihirota-doc"
    },
    {
        "name": "vns-masakinihirota-sample",
        "path": "vns-masakinihirota-sample"
    },
    {
        "name": "task1",
        "path": "task1"
    }
]

```

#### ワークスペース2 (task2用):

```json
"folders": [
    {
        "name": "vns-masakinihirota-custom-instructions",
        "path": "vns-masakinihirota-custom-instructions"
    },
    {
        "name": "vns-masakinihirota-design",
        "path": "vns-masakinihirota-design"
    },
    {
        "name": "vns-masakinihirota-doc",
        "path": "vns-masakinihirota-doc"
    },
    {
        "name": "vns-masakinihirota-sample",
        "path": "vns-masakinihirota-sample"
    },
    {
        "name": "task2",
        "path": "task2"
    }
]

```

3. **ワークスペースを保存**:
   - メニューの「ファイル」 > 「名前を付けてワークスペースを保存...」を選択し、以下の名前で保存します。
     - `task1.code-workspace`
     - `task2.code-workspace`

4. **複数のウィンドウを開く**:
   - VSCodeのウィンドウを複製し、それぞれのワークスペースを開きます。

これにより、各タスク用の作業ディレクトリを独立して管理し、設計や指示書を共有しながら並列開発が可能になります。

---

# 注意事項

- **作業ディレクトリの独立性**: 各作業ディレクトリは独立しているため、ブランチ間での変更が衝突しないように注意してください。
- **環境変数の管理**: `.env` ファイルに機密情報が含まれる場合は、漏洩しないように十分注意してください。
- **依存関係の整合性**: すべての作業ディレクトリで依存関係が正しくインストールされていることを確認してください。
- **ワークスペースの管理**: ワークスペースに追加することで、複数の作業ディレクトリを1つのVSCodeインスタンスで管理できます。
- **ターミナルの活用**: VSCodeのターミナルを使用することで、コマンドの実行が簡単になります。



# 素早くworktreeを切り替え

例

```terminal
alias wt1="cd C:/src/___masakinihirota/task1"
alias wt2="cd C:/src/___masakinihirota/task2"
alias wt3="cd C:/src/___masakinihirota/task3"

```
