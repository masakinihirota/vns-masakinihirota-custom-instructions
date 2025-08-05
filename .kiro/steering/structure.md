# プロジェクト構造

## ルートディレクトリ
```
drm-free-extractor/
├── src/                    # フロントエンドソースコード
├── src-tauri/              # Rustバックエンドソースコード
├── dist/                   # ビルド済みフロントエンド
├── node_modules/           # Node.js依存関係
├── package.json            # フロントエンド設定・依存関係
├── tsconfig.json           # TypeScript設定
├── vite.config.ts          # Vite設定
├── build.ps1               # リリースビルドスクリプト
├── build-debug.ps1         # デバッグビルドスクリプト
└── README.md               # プロジェクトドキュメント
```

## フロントエンド構造（src/）
```
src/
├── api/                    # Tauri APIラッパー
├── assets/                 # 静的リソース
├── components/             # UIコンポーネント
├── styles/                 # スタイルシート
├── types/                  # TypeScript型定義
├── utils/                  # ユーティリティ関数
├── main.ts                 # エントリーポイント
└── styles.css              # グローバルスタイル
```

## バックエンド構造（src-tauri/）
```
src-tauri/
├── src/                    # Rustソースコード
├── capabilities/           # Tauri権限設定
├── icons/                  # アプリケーションアイコン
├── target/                 # Rustビルド出力
├── Cargo.toml              # Rust設定・依存関係
├── tauri.conf.json         # Tauriアプリ設定
└── build.rs                # ビルドスクリプト
```

## 設定ファイルの役割
- **package.json**: フロントエンド依存関係、npm scripts
- **Cargo.toml**: Rust依存関係、最適化設定
- **tsconfig.json**: TypeScript strict mode、ES2020ターゲット
- **vite.config.ts**: 開発サーバー設定（ポート1420）
- **tauri.conf.json**: アプリメタデータ、権限、ビルド設定

## ビルド出力
- **src-tauri/target/release/**: リリース実行ファイル
- **src-tauri/target/release/bundle/**: インストーラー
- **src-tauri/target/debug/**: デバッグ実行ファイル
- **dist/**: フロントエンドビルド出力

## 開発時の注意点
- フロントエンドとバックエンドは独立してビルド可能
- Tauriは固定ポート（1420）を使用
- PowerShellスクリプトでワンクリックビルド対応
