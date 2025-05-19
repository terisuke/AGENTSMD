# AGENTS.md - Next.js Project

## はじめに
このプロジェクトはNext.js、TypeScript、Tailwind CSSを使用しています。OpenAI Codexは以下のガイドラインに従ってタスクを実行してください。

## 1. コードベースのナビゲーションとアーキテクチャ

### ディレクトリ構造（App Router）
```
project-root/
├── app/
│   ├── (auth)/          # ルートグループ
│   ├── api/             # API Routes
│   ├── globals.css      # グローバルスタイル
│   ├── layout.tsx       # ルートレイアウト
│   └── page.tsx         # ホームページ
├── components/
│   ├── ui/              # 再利用可能UIコンポーネント
│   └── features/        # 機能別コンポーネント
├── lib/
│   ├── utils.ts         # ユーティリティ関数
│   └── validations.ts   # Zodスキーマ
├── public/              # 静的ファイル
└── types/               # TypeScript型定義
```

### アーキテクチャパターン
- App Router を使用（Server Components基本）
- コンポーネント設計: Atomic Design
- 状態管理: React Context + Zustand（必要時）
- スタイリング: Tailwind CSS + shadcn/ui

## 2. コードスタイルとフォーマット

### TypeScript/JavaScript
- Prettier でフォーマット
- ESLint で構文チェック
- TypeScript Strict モード有効
- 命名規則:
  - ファイル名: kebab-case（auth-form.tsx）
  - コンポーネント: PascalCase（AuthForm）
  - 関数・変数: camelCase（getUserData）
  - 定数: UPPER_SNAKE_CASE（API_BASE_URL）

### 実行コマンド
```bash
npm run format     # Prettier実行
npm run lint       # ESLint実行
npm run type-check # TypeScriptチェック
```

## 3. テストプロトコル

### テスト構成
- Jest + Testing Library（コンポーネントテスト）
- Playwright（E2Eテスト）
- Vitest（軽量ユニットテスト）

### テスト規則
- 新しいコンポーネントにはテストを必須作成
- Public APIに対する結合テスト
- 重要なユーザーフローのE2Eテスト

### 実行コマンド
```bash
npm test           # 全テスト実行
npm run test:watch # ウォッチモード
npm run test:e2e   # E2Eテスト
npm run coverage   # カバレッジ確認
```

## 4. ビルドプロセスと環境設定

### 環境変数
- `.env.local` ファイルで管理
- `NEXT_PUBLIC_` プレフィックス（クライアント側）
- `DATABASE_URL`, `NEXTAUTH_SECRET`など

### 実行コマンド
```bash
npm run dev        # 開発サーバー起動
npm run build      # 本番ビルド
npm run start      # 本番サーバー起動
npm run analyze    # バンドルサイズ分析
```

## 5. コミットメッセージ規約

### フォーマット（Conventional Commits）
```
type(scope): description

feat(auth): add OAuth login with Google
fix(ui): resolve mobile navigation issue
style(components): update button variants
refactor(api): optimize user data fetching
test(auth): add login form unit tests
docs(readme): update installation guide
```

## 6. プルリクエスト（PR）指示

### PRタイトル形式
- `[feat] Add user authentication flow`
- `[fix] Resolve hydration mismatch error`

### PR説明テンプレート
```markdown
## 変更内容
- 概要説明

## 変更理由
- なぜこの変更が必要か

## スクリーンショット
- UI変更の場合は必須

## テスト
- 実施したテスト内容
- 動作確認環境

## チェックリスト
- [ ] テストが通ることを確認
- [ ]型エラーがないことを確認
- [ ] レスポンシブ対応確認
- [ ] パフォーマンステスト実施

## Closes
- Fixes #issue_number
```

## 7. プロジェクト全般のガイドライン

### Next.js ベストプラクティス
- Server Components を優先使用
- `'use client'` は必要最小限で使用
- 画像は `next/image` を使用（最適化）
- 動的インポートでコード分割実装
- Suspense使用でローディング状態管理

### パフォーマンス
- Core Web Vitals の最適化
- 不要な `useEffect`, `useState` の最小化
- メモ化（useMemo, useCallback）の適切な使用
- 画像最適化（WebP, lazy loading）

### セキュリティ
- CSRFプロテクション実装
- 適切な認証・認可
- 環境変数での機密情報管理
- XSS対策（適切なサニタイゼーション）

### UI/UX
- モバイルファースト設計
- アクセシビリティ（ARIA属性）
- ローディング・エラー状態の適切な実装
- Tailwind Utility Classes の統一的使用

## 8. レビューチェックリスト（Codex PR用）

### Next.js 特有の確認事項
- [ ] Server/Client Components の適切な使い分け
- [ ] App Router の規約に準拠
- [ ] メタデータ（SEO）が適切に設定されている
- [ ] Next.js の最適化機能を活用している

### TypeScript
- [ ] 型定義が適切に行われている
- [ ] `any` 型の使用を避けている
- [ ] 未使用のインポートが残っていない

### スタイリング
- [ ] Tailwind の utility classes を使用
- [ ] レスポンシブデザインが実装されている
- [ ] カスタムCSSが最小限に抑えられている

### パフォーマンス
- [ ] 不要な再レンダリングが発生していない
- [ ] 適切なキーがリストアイテムに設定されている
- [ ] 画像が最適化されている
- [ ] バンドルサイズが適切
