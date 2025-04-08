

----------------------------------------
----------------------------------------



ワークスペースに

```terminal
touch .vscode/settings.json

```


----------------------------------------

#

VSCodeの設定には2種類あります。

VSCode本体のsettings.json
	主に、個人で使う

ワークスペースごとのsettings.json
	主に、チームで同じ設定を使う。





## 優先度

1. ワークスペース
2. 本体



## ワークスペースの設定

1．`.vscode/settings.json`

ワークスペースに登録したリポジトリのルートに作成します。

2．👇ワークスペース設定のファイルに登録できます。

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
		// ワークスペース専用の設定をここに書く
	}
}

```

※ほかに、チームで共有する共通の拡張機能を登録できます。



## 参考

VSCodeにおけるsettings.jsonの優先度について / Cursorも対応 #初心者 - Qiita
https://qiita.com/tatsuyayamakawa/items/df7e5b1b0d7c336af124



