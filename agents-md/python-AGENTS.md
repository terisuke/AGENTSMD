# AGENTS.md - Python Project

## はじめに
このプロジェクトはPythonを使用しており、Flask、SQLAlchemy、pytestを主要技術として採用しています。OpenAI Codexは以下のガイドラインに従ってタスクを実行してください。

## 1. コードベースのナビゲーションとアーキテクチャ

### ディレクトリ構造（src-layout）
```
project-root/
├── src/
│   └── your_package_name/
│       ├── __init__.py
│       ├── models/        # データモデル
│       ├── views/         # ビューロジック（Blueprints）
│       ├── services/      # ビジネスロジック
│       ├── utils/         # ユーティリティ関数
│       └── config.py      # 設定
├── tests/               # テストファイル
│   ├── unit/           # 単体テスト
│   ├── integration/    # 結合テスト
│   └── fixtures/       # テストデータ
├── migrations/         # データベースマイグレーション
├── requirements.txt    # 依存関係
├── pyproject.toml     # プロジェクト設定
└── .env.example       # 環境変数テンプレート
```

### アーキテクチャパターン
- Flask Application Factory Pattern
- Blueprint による機能分離
- Repository Pattern (Data Access Layer)
- Service Layer による業務ロジック分離
- Dependency Injection 活用

## 2. コードスタイルとフォーマット

### Python スタイル（PEP 8準拠）
- Black：自動フォーマット（88文字制限）
- isort：import文の整理
- 命名規則:
  - 関数・変数: snake_case（get_user_data）
  - クラス: PascalCase（UserService）
  - 定数: UPPER_SNAKE_CASE（DATABASE_URL）
  - プライベート: _underscore_prefix

### 型ヒント
- 全ての関数でパラメータ・戻り値に型ヒント必須
- `typing` モジュールからインポート
- `Optional[Type]` を使用（`Type | None`より優先）
- カスタム型は `types.py` で定義

### 実行コマンド
```bash
black .                # Black フォーマット
isort .                # import 整理
flake8 .               # リンター実行
mypy src/              # 型チェック
```

## 3. テストプロトコル

### テスト構成
- pytest：テストフレームワーク
- pytest-cov：カバレッジ測定
- pytest-mock：モック機能
- factory_boy：テストデータ生成

### テスト規則
- 全ての public API にテスト必須
- カバレッジ 90% 以上維持
- ファイル名: `test_*.py` または `*_test.py`
- テスト関数: `test_*` プレフィックス

### 実行コマンド
```bash
pytest                 # 全テスト実行
pytest -v              # 詳細表示
pytest --cov=src       # カバレッジ測定
pytest -x              # 最初の失敗で停止
pytest -k test_name    # 特定テスト実行
```

## 4. ビルドプロセスと環境設定

### 仮想環境
- `python -m venv venv` で作成
- `pip install -r requirements.txt` で依存関係インストール
- `pip install -e .` で開発モードインストール

### 環境変数
```bash
FLASK_APP=src.app:create_app
FLASK_ENV=development
DATABASE_URL=sqlite:///app.db
SECRET_KEY=your-secret-key
SQLALCHEMY_DATABASE_URI=sqlite:///app.db
```

### 実行コマンド
```bash
# 開発環境
flask run              # 開発サーバー起動
flask init-db          # データベース初期化
flask db migrate       # マイグレーション作成
flask db upgrade       # マイグレーション適用

# 本番環境
gunicorn "src.app:create_app()" # 本番サーバー起動
```

## 5. コミットメッセージ規約

### フォーマット（Conventional Commits）
```
type(scope): description

feat(auth): implement JWT authentication
fix(models): resolve user relationship issue
docs(api): update endpoint documentation
refactor(services): optimize user data queries
test(auth): add login integration tests
chore(deps): update Flask to 2.3.0
```

## 6. プルリクエスト（PR）指示

### PRタイトル形式
- `[feat] Implement user registration API`
- `[fix] Resolve database connection pooling issue`

### PR説明テンプレート
```markdown
## 変更内容
- 実装・修正された機能の説明

## 変更理由
- 変更の背景・動機

## テスト方法
- ローカルでの検証手順
- 自動テスト結果

## データベース変更
- [ ] マイグレーションファイル更新
- [ ] 既存データへの影響確認

## 破壊的変更
- [ ] API の破壊的変更あり
- [ ] 設定変更が必要

## チェックリスト
- [ ] 全テスト通過
- [ ] 型チェック通過
- [ ] Black フォーマット適用
- [ ] ドキュメント更新

## Closes
- Fixes #issue_number
```

## 7. プロジェクト全般のガイドライン

### Flask ベストプラクティス
- Application Factory Pattern 使用
- Blueprint による機能分離
- 適切な設定管理（Config クラス）
- Flask-SQLAlchemy による ORM 使用
- Flask-Migrate によるマイグレーション管理

### データベース
- SQLAlchemy ORM 使用
- モデルは `models/` ディレクトリで管理
- 適切なリレーション定義
- インデックス設定によるパフォーマンス最適化
- トランザクション管理

### セキュリティ
- Flask-Login による認証
- CSRF プロテクション実装
- パスワードハッシュ化（bcrypt）
- SQL インジェクション対策（ORM使用）
- 適切な CORS 設定

### パフォーマンス
- データベースクエリ最適化
- 適切なキャッシュ戦略（Flask-Caching）
- ページネーション実装
- 非同期処理（Celery使用検討）

### エラーハンドリング
- カスタム例外クラス定義
- 適切な HTTP ステータスコード返却
- ログ記録（logging モジュール）
- エラーレスポンス統一

## 8. レビューチェックリスト（Codex PR用）

### Python 特有の確認事項
- [ ] 型ヒントが適切に設定されている
- [ ] docstring が Google スタイルで記述されている
- [ ] `if __name__ == "__main__":` パターン使用
- [ ] 例外処理が適切に実装されている

### Flask 特有の確認事項
- [ ] Blueprint の適切な使用
- [ ] リクエスト検証が実装されている
- [ ] 適切な HTTP メソッド使用
- [ ] セキュリティヘッダーが設定されている

### データベース
- [ ] SQLAlchemy モデルが適切に定義されている
- [ ] マイグレーションファイルが含まれている
- [ ] 外部キー制約が適切に設定されている
- [ ] N+1 問題の回避ができている

### セキュリティ
- [ ] 入力値検証が実装されている
- [ ] 認証・認可が適切に実装されている
- [ ] パスワードが平文で保存されていない
- [ ] 機密情報が環境変数で管理されている

### テスト
- [ ] 重要な業務ロジックにテストがある
- [ ] モックが適切に使用されている
- [ ] エッジケースがテストされている
- [ ] テストが独立して実行可能
