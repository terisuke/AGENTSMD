# AGENTS.md - Flutter Project

## はじめに
このプロジェクトはFlutter、Dart、Riverpodを使用したクロスプラットフォームアプリです。OpenAI Codexは以下のガイドラインに従ってタスクを実行してください。

## 1. コードベースのナビゲーションとアーキテクチャ

### ディレクトリ構造
```
project-root/
├── lib/
│   ├── core/
│   │   ├── constants/   # 定数定義
│   │   ├── errors/      # エラークラス
│   │   ├── utils/       # ユーティリティ
│   │   └── themes/      # テーマ設定
│   ├── data/
│   │   ├── models/      # データモデル
│   │   ├── repositories/ # リポジトリ実装
│   │   └── services/    # 外部API通信
│   ├── domain/
│   │   ├── entities/    # ビジネスエンティティ
│   │   ├── repositories/ # リポジトリインターフェース
│   │   └── usecases/    # ユースケース
│   ├── presentation/
│   │   ├── pages/       # 画面ウィジェット
│   │   ├── widgets/     # 再利用可能ウィジェット
│   │   └── providers/   # Riverpod プロバイダー
│   └── main.dart        # アプリエントリーポイント
├── test/
│   ├── unit/            # 単体テスト
│   ├── widget/          # ウィジェットテスト
│   └── integration/     # 統合テスト
├── assets/
│   ├── images/          # 画像アセット
│   ├── icons/           # アイコン
│   └── fonts/           # フォント
└── pubspec.yaml         # 依存関係設定
```

### アーキテクチャパターン
- Clean Architecture
- MVVM パターン
- Repository パターン
- Riverpod による状態管理
- Feature-First ディレクトリ構成

## 2. コードスタイルとフォーマット

### Dart スタイル（Effective Dart準拠）
- dart format でフォーマット
- dart analyze でリント実行
- 命名規則:
  - クラス: PascalCase（UserRepository）
  - ファイル名: snake_case（user_repository.dart）
  - 関数・変数: camelCase（getUserData）
  - 定数: lowerCamelCase（defaultPadding）
  - プライベート: \_underscore（\_privateMethod）

### Flutter Widget 規則
- Stateless Widget 優先使用
- const コンストラクタの活用
- SingleChildScrollView の適切な使用
- SafeArea の考慮

### 実行コマンド
```bash
dart format .          # Dartフォーマット
dart analyze          # 静的解析
flutter pub get       # 依存関係取得
```

## 3. テストプロトコル

### テスト構成
- flutter_test：フレームワーク標準
- mockito：モック作成
- golden_toolkit：UI テスト
- integration_test：統合テスト

### テスト規則
- 全 public メソッドの単体テスト
- 重要な UI ウィジェットのテスト
- ユースケースの中心的なテスト
- Golden test による UI 回帰テスト

### 実行コマンド
```bash
flutter test           # 全テスト実行
flutter test --coverage # カバレッジ測定
flutter test integration_test/ # 統合テスト
flutter test test/widget/ # ウィジェットテスト
```

## 4. ビルドプロセスと環境設定

### 環境設定
- .env ファイルで管理（flutter_dotenv）
- flavor による環境分割
- 設定ファイル（config/app_config.dart）

### 実行コマンド
```bash
# 開発環境
flutter run            # デバッグモードで起動
flutter run --release  # リリースモードで起動
flutter run -d chrome  # Web版で起動

# ビルド
flutter build apk      # Android APK
flutter build ios      # iOS Build
flutter build web      # Web Build
```

## 5. コミットメッセージ規約

### フォーマット（Conventional Commits）
```
type(scope): description

feat(auth): implement biometric login
fix(ui): resolve overflow issue on small screens
style(widgets): update button theme consistency  
refactor(state): migrate to Riverpod 2.0
test(models): add user model serialization tests
docs(readme): update installation instructions
```

## 6. プルリクエスト（PR）指示

### PRタイトル形式
- `[feat] Add push notification support`
- `[fix] Resolve keyboard overlap issue`

### PR説明テンプレート
```markdown
## 変更内容
- 実装・修正された機能の詳細
- UI/UX の変更点

## スクリーンショット
- iOS/Android での表示確認
- Web（該当する場合）
- 異なる画面サイズでの確認

## テスト
- 実施した動作テスト
- 対象プラットフォーム確認
- パフォーマンステスト

## 破壊的変更
- [ ] 既存 API の変更あり
- [ ] データモデルの変更あり

## チェックリスト
- [ ] Android でのテスト完了
- [ ] iOS でのテスト完了  
- [ ] 単体テスト通過
- [ ] アクセシビリティ確認
- [ ] パフォーマンス確認

## Closes
- Fixes #issue_number
```

## 7. プロジェクト全般のガイドライン

### Flutter ベストプラクティス
- Widget の適切な分割
- const コンストラクタ使用
- build メソッドの軽量化
- Key の適切な使用
- MediaQuery の効率的使用

### Riverpod 状態管理
- Provider の適切な粒度
- StateProvider/StateNotifierProvider の使い分け
- ref.watch/ref.read の使い分け
- autodispose の活用
- familyProvider による引数渡し

### パフォーマンス最適化
- 不要な rebuild 防止
- ListView.builder の使用
- RepaintBoundary の活用
- Image キャッシュ戦略
- AnimationController の適切な dispose

### データ管理
- JSON シリアル化（json_annotation）
- Hive/Shared Preferences での永続化
- Repository パターンによる抽象化
- エラーハンドリング戦略

### UI/UX
- Material Design / Cupertino 準拠
- レスポンシブデザイン
- Dark mode 対応
- アクセシビリティ（Semantics）
- 適切なローディング表示

## 8. レビューチェックリスト（Codex PR用）

### Flutter 特有の確認事項
- [ ] Widget tree が適切に構成されている
- [ ] メモリリークが発生していない
- [ ] build メソッドが効率的に記述されている
- [ ] 適切な Key が設定されている

### Dart 言語
- [ ] null safety が適切に実装されている
- [ ] async/await が正しく使われている
- [ ] Stream の適切な使用
- [ ] Extension methods の活用

### Riverpod 状態管理
- [ ] Provider が適切に設計されている
- [ ] 状態の依存関係が正しい
- [ ] autodispose が適切に使われている
- [ ] ref.invalidate の適切な使用

### UI/レスポンシブ
- [ ] 異なる画面サイズで正常動作
- [ ] オーバーフローが発生していない
- [ ] 適切な padding/margin 設定
- [ ] SafeArea が考慮されている

### パフォーマンス
- [ ] 不要な rebuild が発生していない
- [ ] 重い処理が isolate で実行されている
- [ ] 画像が適切に最適化されている
- [ ] アニメーションが滑らか

### テスト
- [ ] Widget の主要な機能にテスト
- [ ] ユースケースにテスト
- [ ] Golden test の更新
- [ ] Edge case のテスト

### アクセシビリティ
- [ ] Semantics が適切に設定されている
- [ ] ボタンに十分なタップ面積
- [ ] コントラスト比が適切
- [ ] スクリーンリーダー対応

### プラットフォーム別
- [ ] Android Material Design 準拠
- [ ] iOS Cupertino Design 準拠
- [ ] プラットフォーム間の一貫性
- [ ] ネイティブ機能の適切な使用
