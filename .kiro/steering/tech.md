# 技術スタック

## アーキテクチャ
- **フレームワーク**: Tauri v2（Rust + TypeScript）
- **フロントエンド**: Vite + TypeScript + Vanilla JS
- **バックエンド**: Rust（非同期処理にTokio使用）

## 主要ライブラリ

### フロントエンド
- `@tauri-apps/api`: Tauriコア機能
- `@tauri-apps/plugin-opener`: ファイル・URL開く機能
- `vite`: ビルドツール・開発サーバー
- `typescript`: 型安全性確保

### バックエンド（Rust）
- `epub`: ePubファイル解析
- `zip`: アーカイブ処理
- `scraper`: HTML解析・テキスト抽出
- `image`: 画像処理
- `serde/serde_json`: シリアライゼーション
- `tokio`: 非同期ランタイム
- `anyhow/thiserror`: エラーハンドリング
- `chrono`: 日時処理

## ビルドシステム

### 開発環境
```bash
# 開発サーバー起動
pnpm tauri dev

# 依存関係インストール
pnpm install
```

### ビルドコマンド
```bash
# リリースビルド
pnpm tauri build
# または
.\build.ps1

# デバッグビルド
pnpm tauri build --debug
# または
.\build-debug.ps1

# フロントエンドのみビルド
pnpm build
```

### 設定ファイル
- `tsconfig.json`: TypeScript設定（strict mode有効）
- `vite.config.ts`: Vite設定（ポート1420固定）
- `Cargo.toml`: Rust依存関係・最適化設定
- `tauri.conf.json`: Tauriアプリ設定

## 開発要件
- Node.js v18以上
- pnpm
- Rust toolchain
- Tauri CLI
