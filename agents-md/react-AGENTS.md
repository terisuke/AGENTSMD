# AGENTS.md - React Project

## はじめに
このプロジェクトはReact、TypeScript、Viteを使用したモダンなフロントエンドアプリケーションです。OpenAI Codexは以下のガイドラインに従ってタスクを実行してください。

## 1. コードベースのナビゲーションとアーキテクチャ

### ディレクトリ構造
```
project-root/
├── src/
│   ├── components/
│   │   ├── ui/          # 再利用可能UIコンポーネント
│   │   └── features/    # 機能別コンポーネント
│   ├── hooks/           # カスタムフック
│   ├── services/        # API通信・外部サービス
│   ├── store/           # 状態管理（Zustand/Redux）
│   ├── types/           # TypeScript型定義
│   ├── utils/           # ユーティリティ関数
│   ├── styles/          # グローバルスタイル
│   ├── App.tsx          # メインアプリコンポーネント
│   └── main.tsx         # エントリーポイント
├── public/              # 静的ファイル
└── tests/
    ├── __mocks__/       # モックファイル
    └── setup.ts         # テスト設定
```

### アーキテクチャパターン
- 関数コンポーネント + フック
- コンポーネント合成パターン
- カスタムフックによるロジック抽出
- Context API + Zustand による状態管理

## 2. コードスタイルとフォーマット

### TypeScript/JavaScript
- Prettier でフォーマット
- ESLint + @typescript-eslint で構文チェック
- 厳密な TypeScript 設定
- 命名規則:
  - コンポーネント: PascalCase（UserProfile）
  - ファイル名: kebab-case（user-profile.tsx）
  - 関数・変数: camelCase（getUserData）
  - 定数: UPPER_SNAKE_CASE（API_ENDPOINTS）
  - フック: useXxx（useUserData）

### React 規則
- 関数コンポーネント優先
- デストラクチャリング活用
- 条件付きレンダリングの適切な実装
- JSX内での適切な key 属性設定

### 実行コマンド
```bash
npm run format     # Prettier実行
npm run lint       # ESLint実行
npm run type-check # TypeScriptチェック
```

## 3. テストプロトコル

### テスト構成
- Vitest：テストランナー
- React Testing Library：コンポーネントテスト
- MSW (Mock Service Worker)：API モック
- Playwright：E2Eテスト

### テスト規則
- 全 public コンポーネントにテスト作成
- ユーザーの操作フローを重視したテスト
- カスタムフックの単体テスト実装
- 重要なユーザーシナリオの E2E テスト

### 実行コマンド
```bash
npm test           # 全テスト実行
npm run test:watch # ウォッチモード
npm run test:ui    # Vitest UI
npm run test:e2e   # E2Eテスト
npm run coverage   # カバレッジ確認
```

## 4. ビルドプロセスと環境設定

### 環境変数
- `.env` ファイルで管理
- `VITE_` プレフィックス必須（Vite）
- 環境別設定（development/production）

### 実行コマンド
```bash
npm run dev        # 開発サーバー起動
npm run build      # 本番ビルド
npm run preview    # ビルド結果プレビュー
npm run analyze    # バンドルサイズ分析
```

## 5. コミットメッセージ規約

### フォーマット（Conventional Commits）
```
type(scope): description

feat(auth): add user login form
fix(ui): resolve button hover state issue
style(components): update spacing consistency
refactor(hooks): optimize useUserData performance
test(auth): add login form validation tests
docs(readme): update component usage examples
```

## 6. プルリクエスト（PR）指示

### PRタイトル形式
- `[feat] Add shopping cart functionality`
- `[fix] Resolve mobile navigation issue`

### PR説明テンプレート
```markdown
## 変更内容
- 実装・修正された機能の詳細

## スクリーンショット/動画
- UI変更の場合は必須
- Before/After の比較

## テスト
- 実施したテスト内容
- カバレッジ変化

## Lighthouse スコア（該当する場合）
- パフォーマンス
- アクセシビリティ
- ベストプラクティス
- SEO

## チェックリスト
- [ ] テスト通過確認
- [ ] 型エラー解消確認
- [ ] レスポンシブ対応確認
- [ ] アクセシビリティ確認
- [ ] ブラウザ互換性確認

## Breaking Changes
- [ ] 破壊的変更あり（詳細説明）

## Closes
- Fixes #issue_number
```

## 7. プロジェクト全般のガイドライン

### React ベストプラクティス
- 関数コンポーネント優先使用
- Hooks の rules 遵守
- 適切な依存配列設定（useEffect, useMemo, useCallback）
- コンポーネントの責務分離
- prop drilling 回避（Context/状態管理ライブラリ）

### パフォーマンス最適化
- React.memo による不要な再レンダリング防止
- useMemo/useCallback の適切な使用
- lazy loading（React.lazy）の実装
- バーチャルスクロール（長いリスト）
- 画像最適化とlazyロード

### 状態管理
- ローカル状態優先（useState）
- 複雑な状態は useReducer
- グローバル状態は Context API または Zustand
- サーバー状態は React Query/SWR

### アクセシビリティ
- セマンティックHTML使用
- ARIA属性の適切な設定
- キーボードナビゲーション対応
- スクリーンリーダー対応
- 色のコントラスト比遵守

### エラーハンドリング
- Error Boundary 実装
- 非同期エラーの適切なハンドリング
- ユーザーフレンドリーなエラーメッセージ
- フォールバック UI 提供

## 8. レビューチェックリスト（Codex PR用）

### React 特有の確認事項
- [ ] Hooks の依存配列が適切に設定されている
- [ ] 不要な再レンダリングが発生していない
- [ ] key prop がリストアイテムに設定されている
- [ ] useEffect のクリーンアップが実装されている

### TypeScript
- [ ] 適切な型定義がされている
- [ ] any 型の使用を避けている
- [ ] Props の型が適切に定義されている
- [ ] 未使用の import が削除されている

### パフォーマンス
- [ ] 高頻度で実行される処理の最適化
- [ ] 不要な状態の分割・統合
- [ ] 重いコンポーネントの遅延読み込み
- [ ] バンドルサイズが適切

### アクセシビリティ
- [ ] 適切な見出しレベル（h1-h6）の使用
- [ ] フォーカス管理の実装
- [ ] 色以外の視覚的手がかりの提供
- [ ] 適切な alt 属性の設定

### テスト
- [ ] ユーザー主導のテストアプローチ
- [ ] エッジケースのテスト
- [ ] モックの適切な使用
- [ ] 非同期処理のテスト方法

### CSS/スタイリング
- [ ] レスポンシブデザインの実装
- [ ] CSS-in-JS の適切な使用
- [ ] スタイルの一貫性
- [ ] 不要なスタイルの削除
