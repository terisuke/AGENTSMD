# AGENTS.md - Node.js Project

## はじめに
このプロジェクトはNode.js、Express、TypeScript、Prismaを使用したバックエンドアプリケーションです。OpenAI Codexは以下のガイドラインに従ってタスクを実行してください。

## 1. コードベースのナビゲーションとアーキテクチャ

### ディレクトリ構造
```
project-root/
├── src/
│   ├── controllers/     # ルートハンドラー
│   ├── services/        # ビジネスロジック
│   ├── repositories/    # データアクセス層
│   ├── middleware/      # Express ミドルウェア
│   ├── models/          # データモデル定義
│   ├── routes/          # ルート定義
│   ├── utils/           # ユーティリティ関数
│   ├── types/           # TypeScript型定義
│   ├── config/          # 設定ファイル
│   ├── validators/      # 入力検証
│   └── app.ts           # Express アプリ設定
├── tests/
│   ├── unit/            # 単体テスト
│   ├── integration/     # 結合テスト
│   └── e2e/             # E2Eテスト
├── prisma/
│   ├── schema.prisma    # データベーススキーマ
│   └── migrations/      # マイグレーション
├── .env.example         # 環境変数テンプレート
└── server.ts            # サーバー起動
```

### アーキテクチャパターン
- レイヤードアーキテクチャ
- Repository Pattern
- Dependency Injection
- Express Router モジュラー構成
- Prisma ORM によるデータアクセス

## 2. コードスタイルとフォーマット

### TypeScript/Node.js
- Prettier でフォーマット
- ESLint + @typescript-eslint で構文チェック
- 厳密な TypeScript 設定（strict: true）
- 命名規則:
  - ファイル名: kebab-case（user-controller.ts）
  - クラス: PascalCase（UserService）
  - 関数・変数: camelCase（getUserById）
  - 定数: UPPER_SNAKE_CASE（DATABASE_URL）
  - インターフェース: PascalCase + I prefix（IUserRepository）

### Express 規則
- 非同期処理は async/await 使用
- エラーハンドリングミドルウェア実装
- 適切な HTTP ステータスコード使用
- RESTful API 設計

### 実行コマンド
```bash
npm run format     # Prettier実行
npm run lint       # ESLint実行
npm run type-check # TypeScriptチェック
```

## 3. テストプロトコル

### テスト構成
- Jest：テストフレームワーク
- Supertest：HTTP テスト
- @testing-library/jest-dom：DOM テスト
- testcontainers：統合テスト用コンテナ

### テスト規則
- 全 API エンドポイントの統合テスト
- サービス層の単体テスト
- リポジトリ層のテスト（モック DB 使用）
- エラーケースのテスト網羅

### 実行コマンド
```bash
npm test           # 全テスト実行
npm run test:unit  # 単体テスト
npm run test:int   # 統合テスト
npm run test:e2e   # E2Eテスト
npm run coverage   # カバレッジ確認
```

## 4. ビルドプロセスと環境設定

### 環境変数
```bash
# データベース
DATABASE_URL=postgresql://username:password@localhost:5432/db_name

# 認証
JWT_SECRET=your-jwt-secret
BCRYPT_ROUNDS=12

# アプリケーション
NODE_ENV=development
PORT=3000
API_VERSION=v1

# 外部サービス
REDIS_URL=redis://localhost:6379
AWS_ACCESS_KEY_ID=your-access-key
```

### 実行コマンド
```bash
# 開発環境
npm run dev        # 開発サーバー起動（ホットリロード）
npm run db:migrate # Prisma マイグレーション実行
npm run db:seed    # データベースシード実行

# 本番環境
npm run build      # TypeScript ビルド
npm run start      # 本番サーバー起動
npm run pm2:start  # PM2による本番起動
```

## 5. コミットメッセージ規約

### フォーマット（Conventional Commits）
```
type(scope): description

feat(auth): implement JWT refresh token
fix(api): resolve user validation error
perf(db): optimize query for user search
security(auth): add rate limiting
refactor(services): extract common database logic
test(controllers): add user CRUD tests
```

## 6. プルリクエスト（PR）指示

### PRタイトル形式
- `[feat] Add user authentication with JWT`
- `[fix] Resolve database connection pooling issue`

### PR説明テンプレート
```markdown
## 変更内容
- API エンドポイントの追加・修正
- データベーススキーマの変更

## API ドキュメント
- [ ] Swagger/OpenAPI 仕様更新
- エンドポイント: `POST /api/v1/users`
- リクエスト・レスポンス例

## データベース変更
- [ ] Prisma マイグレーション作成済み
- [ ] 既存データへの影響確認済み
- [ ] ロールバック手順確認済み

## セキュリティチェック
- [ ] 入力値検証実装
- [ ] 認証・認可確認
- [ ] SQL インジェクション対策
- [ ] レート制限実装

## パフォーマンステスト
- [ ] 負荷テスト実施
- [ ] メモリリークチェック
- [ ] データベースクエリ最適化

## チェックリスト
- [ ] 全テスト通過
- [ ] 型チェック通過
- [ ] リンタエラー解消
- [ ] エラーログ確認
- [ ] ドキュメント更新

## Closes
- Fixes #issue_number
```

## 7. プロジェクト全般のガイドライン

### Express.js ベストプラクティス
- Express Router による機能分割
- ミドルウェアチェーンの適切な実装
- エラーハンドリングミドルウェア設置
- セキュリティミドルウェア（helmet, cors）
- 適切なHTTPステータスコード返却

### データベース（Prisma）
- Prisma Client による型安全なクエリ
- データベーススキーマ管理
- マイグレーション履歴管理
- コネクションプール設定
- リレーション設計の最適化

### 認証・認可
- JWT による stateless 認証
- Refresh token による長期認証
- Role-based access control (RBAC)
- Rate limiting 実装
- CORS 設定

### セキュリティ
- 入力値検証（Joi, Zod）
- SQL injection 対策（Prisma ORM）
- XSS 対策（helmet）
- CSRF 対策
- HTTPSの強制

### エラーハンドリング
- 中央集権的エラーハンドリング
- カスタム例外クラス定義
- 適切なログ出力（winston）
- エラーレスポンスの統一
- Sentry などの外部監視ツール連携

### パフォーマンス
- Redis によるキャッシュ戦略
- データベースクエリ最適化
- 圧縮ミドルウェア使用
- 非同期処理の最適化
- メモリ使用量監視

## 8. レビューチェックリスト（Codex PR用）

### Node.js/Express 特有の確認事項
- [ ] 非同期処理が適切に実装されている
- [ ] エラーハンドリングが実装されている
- [ ] ミドルウェアが適切な順序で配置されている
- [ ] HTTPステータスコードが適切

### TypeScript
- [ ] 適切な型定義がされている
- [ ] any 型を避けて型安全性を保っている
- [ ] インターフェース設計が適切
- [ ] ジェネリクスが効果的に使われている

### データベース（Prisma）
- [ ] Prisma スキーマが適切に設計されている
- [ ] N+1 問題を回避している
- [ ] トランザクション処理が適切
- [ ] インデックスが適切に設定されている

### セキュリティ
- [ ] 入力値検証が実装されている
- [ ] 認証・認可が適切に実装されている
- [ ] 機密情報の適切な管理
- [ ] セキュリティヘッダーの設定

### API 設計
- [ ] RESTful な設計になっている
- [ ] 適切なHTTPメソッドを使用
- [ ] エラーレスポンスが統一されている
- [ ] API バージョニング対応

### テスト
- [ ] 主要な業務ロジックのテストがある
- [ ] API エンドポイントの統合テスト
- [ ] エラーケースのテスト
- [ ] モック・スタブが適切に使用されている

### パフォーマンス
- [ ] 効率的なデータベースクエリ
- [ ] 適切なキャッシュ戦略
- [ ] メモリリークの防止
- [ ] 適切な非同期処理
