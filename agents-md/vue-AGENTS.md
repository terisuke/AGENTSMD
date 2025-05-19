# AGENTS.md - Vue.js Project

## はじめに
このプロジェクトはVue.js 3、Composition API、TypeScript、Viteを使用しています。OpenAI Codexは以下のガイドラインに従ってタスクを実行してください。

## 1. コードベースのナビゲーションとアーキテクチャ

### ディレクトリ構造
```
project-root/
├── src/
│   ├── components/
│   │   ├── base/        # 基本UIコンポーネント
│   │   └── feature/     # 機能別コンポーネント
│   ├── composables/     # Composition API再利用ロジック
│   ├── stores/          # Pinia ストア
│   ├── router/          # Vue Router設定
│   ├── services/        # API通信サービス
│   ├── types/           # TypeScript型定義
│   ├── utils/           # ユーティリティ関数
│   ├── styles/          # グローバルスタイル
│   ├── App.vue          # メインアプリコンポーネント
│   └── main.ts          # エントリーポイント
├── public/              # 静的ファイル
└── tests/
    ├── unit/            # 単体テスト
    └── e2e/             # E2Eテスト
```

### アーキテクチャパターン
- Composition API 優先使用
- Single File Components (.vue)
- Pinia による状態管理
- Vue Router による SPA ルーティング
- Composables による再利用ロジック抽出

## 2. コードスタイルとフォーマット

### Vue.js スタイル（Vue Style Guide準拠）
- Prettier でフォーマット
- ESLint + @vue/typescript-recommended で構文チェック
- 命名規則:
  - コンポーネント: PascalCase（UserProfile.vue）
  - ファイル名: PascalCase（UserProfile.vue）
  - Props: camelCase（userName）
  - イベント: kebab-case（@update-user）
  - Composables: useXxx（useUserData）

### Vue Template 規則
- v-for には key 必須
- v-if と v-for の同時使用避ける
- イベントハンドラーは明示的
- slot の適切な活用

### 実行コマンド
```bash
npm run format     # Prettier実行
npm run lint       # ESLint実行
npm run type-check # TypeScriptチェック
```

## 3. テストプロトコル

### テスト構成
- Vitest：テストランナー
- Vue Test Utils：Vue コンポーネントテスト
- Testing Library：ユーザー中心テスト
- Playwright：E2Eテスト

### テスト規則
- 全 public コンポーネントにテスト作成
- Composables の単体テスト実装
- Pinia ストアのテスト作成
- 重要なユーザーフローの E2E テスト

### 実行コマンド
```bash
npm test           # 全テスト実行
npm run test:unit  # 単体テスト
npm run test:e2e   # E2Eテスト
npm run coverage   # カバレッジ確認
```

## 4. ビルドプロセスと環境設定

### 環境変数
- `.env` ファイルで管理
- `VITE_` プレフィックス必須
- 環境別設定ファイル（.env.development, .env.production）

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

feat(auth): implement user login with composables
fix(router): resolve navigation guard issue
style(components): update button variants
refactor(stores): optimize user store actions
test(composables): add useUserData tests
docs(guide): update composables usage
```

## 6. プルリクエスト（PR）指示

### PRタイトル形式
- `[feat] Add shopping cart with Pinia`
- `[fix] Resolve reactive data update issue`

### PR説明テンプレート
```markdown
## 変更内容
- 実装・修正された機能の詳細

## スクリーンショット/動画
- UI変更がある場合は必須
- Composition API の Reactivity 動作確認

## パフォーマンス影響
- リアクティブシステムへの影響
- メモリ使用量の変化

## チェックリスト
- [ ] Composition API 適切使用確認
- [ ] Reactivity 動作確認
- [ ] TypeScript型チェック通過
- [ ] Vue DevTools での確認
- [ ] スロットとプロパティのテスト

## Breaking Changes
- [ ] API 変更あり
- [ ] Props/Events 変更あり

## Closes
- Fixes #issue_number
```

## 7. プロジェクト全般のガイドライン

### Vue.js 3 ベストプラクティス
- Composition API 優先使用
- `<script setup>` 記法の活用
- ref/reactive の適切な使い分け
- computed の無駄な再計算防止
- watchEffect/watch の適切な使用

### Reactivity システム
- ref（プリミティブ値）
- reactive（オブジェクト）
- readonly（読み取り専用）
- toRefs（reactive から ref への変換）
- unref（ref 値の展開）

### パフォーマンス最適化
- v-memo による条件メモ化
- KeepAlive による状態保持
- 非同期コンポーネント（defineAsyncComponent）
- lazy loading ルート設定
- Pinia での selectory アクセス

### 状態管理（Pinia）
- ストアの適切な分割
- getters の活用
- actions による状態変更
- store subscription の使用

### ルーティング（Vue Router）
- 名前付きルート使用
- ナビゲーションガードの実装
- ルートメタ情報の活用
- 動的ルート設定

### TypeScript統合
- defineComponent with TypeScript
- Props の型定義
- emit の型定義
- Template refs の型付け

## 8. レビューチェックリスト（Codex PR用）

### Vue.js 特有の確認事項
- [ ] Composition API が適切に使用されている
- [ ] リアクティブな参照が正しく設定されている
- [ ] v-model の使用が適切
- [ ] カスタムイベントが適切に emit されている

### Template 品質
- [ ] 適切な key 属性設定
- [ ] v-if/v-show の使い分け
- [ ] スロットの活用
- [ ] 条件分岐とループの最適化

### Composition API
- [ ] setup関数の適切な構成
- [ ] ref/reactive の適切な使い分け
- [ ] computed/watch の効率的な使用
- [ ] lifecycle hooks の適切な配置

### Pinia（状態管理）
- [ ] ストア設計の妥当性
- [ ] getters の効率的な実装
- [ ] actions の副作用管理
- [ ] ストア間の依存関係

### TypeScript
- [ ] Props/emit の型定義
- [ ] Composables の型安全性
- [ ] Template refs の型付け
- [ ] 未使用の型・変数削除

### パフォーマンス
- [ ] 不要な再レンダリング防止
- [ ] computed の無効な依存関係確認
- [ ] メモリリークの可能性確認
- [ ] 大きなリストの仮想化検討

### アクセシビリティ
- [ ] セマンティックHTML使用
- [ ] ARIA属性の適切な設定
- [ ] フォーカス管理
- [ ] キーボードナビゲーション
