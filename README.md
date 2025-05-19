# AGENTS.md Collection for OpenAI Codex

このリポジトリは、OpenAI Codex用のAGENTS.mdファイルのコレクションです。各技術スタックに特化したガイドラインを提供し、AIエージェントがプロジェクトの規約や最良慣行に従って動作するように支援します。

## AGENTS.mdとは

AGENTS.mdは、OpenAI Codexのようなソフトウェアエンジニアリング AIエージェントがプロジェクト内で効果的に機能するためのガイドラインファイルです。これは人間開発者向けのREADME.mdに相当するものですが、AIエージェント向けに特化されています。

## 利用可能なAGENTS.mdファイル

### 汎用
- [`AGENTS.md`](./AGENTS.md) - 汎用的なプロジェクトテンプレート

### フロントエンド
- [`nextjs-AGENTS.md`](./nextjs-AGENTS.md) - Next.js + TypeScript + Tailwind CSS
- [`react-AGENTS.md`](./react-AGENTS.md) - React + TypeScript + Vite
- [`vue-AGENTS.md`](./vue-AGENTS.md) - Vue.js 3 + Composition API + TypeScript

### バックエンド
- [`python-AGENTS.md`](./python-AGENTS.md) - Python + Flask + SQLAlchemy
- [`nodejs-AGENTS.md`](./nodejs-AGENTS.md) - Node.js + Express + TypeScript + Prisma

### モバイル
- [`flutter-AGENTS.md`](./flutter-AGENTS.md) - Flutter + Dart + Riverpod

## 使用方法

### 1. ファイルをプロジェクトルートにコピー

適切なAGENTS.mdファイルを選択し、プロジェクトのルートディレクトリに `AGENTS.md` としてコピーします。

```bash
# 例: Next.jsプロジェクトの場合
cp agents-md/nextjs-AGENTS.md /path/to/your/project/AGENTS.md
```

### 2. プロジェクトに合わせてカスタマイズ

AGENTS.mdファイルを開き、プロジェクトの特定の要件に合わせて内容を調整します：

- プロジェクト固有のディレクトリ構造
- 使用する特定のライブラリやツール
- チーム固有のコーディング規約
- デプロイメント手順

### 3. OpenAI Codexで使用

OpenAI Codexがタスクを実行する際、AGENTS.mdファイルはプロジェクトのコンテキストを理解し、適切なガイドラインに従うための指針として使用されます。

## AGENTS.mdの主要セクション

各AGENTS.mdファイルは以下の構造に従っています：

1. **コードベースのナビゲーションとアーキテクチャ** - プロジェクト構造の理解
2. **コードスタイルとフォーマット** - スタイルガイドとフォーマットルール
3. **テストプロトコル** - テスト戦略と実行方法
4. **ビルドプロセスと環境設定** - 開発・本番環境の設定
5. **コミットメッセージ規約** - Git コミットメッセージの形式
6. **プルリクエスト指示** - PR作成時のガイドライン
7. **プロジェクト全般のガイドライン** - ベストプラクティスと推奨事項
8. **レビューチェックリスト** - Codex生成コードのレビューポイント

## カスタマイズのヒント

### スコープの活用

大規模プロジェクトでは、サブディレクトリに特化したAGENTS.mdファイルを配置することができます：

```
project-root/
├── AGENTS.md              # 全体用
├── frontend/
│   └── AGENTS.md          # フロントエンド特化
└── backend/
    └── AGENTS.md          # バックエンド特化
```

### 段階的な導入

はじめは基本的なAGENTS.mdから始めて、チームの経験に基づいて徐々に詳細化していくことを推奨します。

### 定期的な更新

プロジェクトの進化に合わせてAGENTS.mdも更新し、Codexが最新の規約に従うようにします。

## ベストプラクティス

1. **明確性を重視** - 曖昧な表現を避け、具体的で実行可能な指示を記述
2. **簡潔性** - 冗長な説明を避け、要点を簡潔に
3. **実行可能性** - 実際に実行可能なコマンドや手順を提供
4. **一貫性** - プロジェクト内での用語や形式の一貫性を保持
5. **更新性** - 定期的にコンテンツを見直し、プロジェクトの変化に対応

## 貢献

新しい技術スタックのAGENTS.mdファイルや既存ファイルの改善にご協力いただける場合は、プルリクエストをお送りください。

## ライセンス

このリポジトリのコンテンツは [MIT License](./LICENCE) の下で公開されています。

## 参考文献

- [OpenAI Codex Documentation](https://openai.com/index/introducing-codex/)
- [Best Practices for AI Agent Guidelines](https://docs.anthropic.com/claude/docs/how-claude-works)
- [Effective Software Development with AI](https://www.temporal.io/blog/improving-java-sdk-codex-openai)
