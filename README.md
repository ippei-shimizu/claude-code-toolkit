# claude-code-toolkit

Claude Code 用の共通スキル・エージェントプラグイン。React / Next.js / React Native 開発のベストプラクティスルール、UI/UX デザインスキル、レビューエージェントを集約したツールキット。

## 概要

このプラグインをプロジェクトに導入すると、Claude Code が以下の知識・能力を自動的に活用できるようになります。

- **React/Next.js パフォーマンス最適化** — Vercel Engineering が推奨する 65 ルール
- **React コンポジションパターン** — スケーラブルなコンポーネント設計の 8 ルール（React 19 対応）
- **React Native/Expo ベストプラクティス** — モバイルアプリ向け 37 ルール
- **UI/UX デザインスキル** — フロントエンド設計、アニメーション、アクセシビリティ、デザインラボ
- **自動レビューエージェント** — パフォーマンス・コンポジション観点の構造化レビュー
- **gstack** — Claude Code 用エンジニアリングツールスイート（サブモジュール）

## インストール

プロジェクトの `.claude/plugins/` にクローン（gstack サブモジュール含む）:

```bash
git clone --recurse-submodules https://github.com/ippei-shimizu/claude-code-toolkit.git .claude/plugins/claude-code-toolkit
cd .claude/plugins/claude-code-toolkit/skills/gstack && ./setup
```

`.gitignore` に追加:

```
.claude/plugins/claude-code-toolkit/
```

## スキル一覧

### React / Next.js / React Native

#### vercel-react-best-practices

Vercel Engineering による React/Next.js パフォーマンス最適化ガイドライン。65 ルールを 8 カテゴリに分類し、影響度順に優先度付け。

| 優先度 | カテゴリ | 影響度 | ルール数 |
|--------|---------|--------|---------|
| 1 | ウォーターフォール排除 | CRITICAL | 5 |
| 2 | バンドルサイズ最適化 | CRITICAL | 5 |
| 3 | サーバーサイドパフォーマンス | HIGH | 9 |
| 4 | クライアントサイドデータフェッチ | MEDIUM-HIGH | 4 |
| 5 | Re-render 最適化 | MEDIUM | 15 |
| 6 | レンダリングパフォーマンス | MEDIUM | 11 |
| 7 | JavaScript パフォーマンス | LOW-MEDIUM | 14 |
| 8 | 高度なパターン | LOW | 3 |

**トリガー**: React/Next.js コードの作成・レビュー・リファクタリング時に自動適用

#### vercel-composition-patterns

React コンポジションパターンガイド。Boolean props の増殖を避け、スケーラブルなコンポーネント API を設計するための 8 ルール。

| 優先度 | カテゴリ | 影響度 | ルール数 |
|--------|---------|--------|---------|
| 1 | コンポーネントアーキテクチャ | HIGH | 2 |
| 2 | 状態管理 | MEDIUM | 3 |
| 3 | 実装パターン | MEDIUM | 2 |
| 4 | React 19 API | MEDIUM | 1 |

**トリガー**: コンポーネント設計・リファクタリング時に自動適用

#### react-native-skills

React Native / Expo ベストプラクティス。モバイルアプリのパフォーマンス・UX 向上のための 37 ルール。

| 優先度 | カテゴリ | 影響度 | ルール数 |
|--------|---------|--------|---------|
| 1 | リストパフォーマンス | CRITICAL | 8 |
| 2 | アニメーション | HIGH | 3 |
| 3 | ナビゲーション | HIGH | 1 |
| 4 | UI パターン | HIGH | 9 |
| 5 | 状態管理 | MEDIUM | 5 |
| 6 | レンダリング | MEDIUM | 2 |
| 7 | Monorepo | MEDIUM | 2 |
| 8 | 設定 | LOW | 3 |

**トリガー**: React Native / Expo コード作業時に自動適用

### UI/UX デザイン

| スキル | 説明 | トリガー |
|--------|------|----------|
| `frontend-design` | 高品質なフロントエンド UI 作成（AI スロップ回避） | UI コンポーネント・ページ作成時 |
| `ui-ux-pro-max` | UI/UX デザイン総合（50 スタイル、21 パレット、50 フォントペアリング、9 スタック対応） | UI/UX デザイン作業時 |
| `design-lab` | 5 つのデザインバリエーション生成・比較ワークフロー | デザイン探索時 |
| `interaction-design` | マイクロインタラクション・モーションデザイン | アニメーション・トランジション実装時 |
| `canvas-design` | ビジュアルアート作成（.png/.pdf） | ポスター・アート作成時 |
| `baseline-ui` | AI スロップ防止の UI ベースライン（Tailwind CSS） | UI 実装時に自動適用 |

### アニメーション・パフォーマンス

| スキル | 説明 | トリガー |
|--------|------|----------|
| `12-principles-of-animation` | Disney 12 原則に基づくアニメーション監査 | アニメーションレビュー時 |
| `fixing-motion-performance` | アニメーションパフォーマンス監査・修正 | アニメーションパフォーマンス改善時 |

### アクセシビリティ・SEO

| スキル | 説明 | トリガー |
|--------|------|----------|
| `fixing-accessibility` | HTML アクセシビリティ問題の監査・修正 | アクセシビリティ修正時 |
| `wcag-audit-patterns` | WCAG 2.2 アクセシビリティ監査 | アクセシビリティ監査時 |
| `web-design-guidelines` | Web Interface Guidelines に基づく UI レビュー | UI レビュー時 |
| `fixing-metadata` | HTML メタデータ（OG, JSON-LD 等）の監査・修正 | メタデータ修正時 |

### ツール

| スキル | 説明 | トリガー |
|--------|------|----------|
| `gstack` | Claude Code 用エンジニアリングツールスイート（サブモジュール） | `/qa`, `/review`, `/ship` 等のスラッシュコマンド |

## エージェント一覧

### react-perf-reviewer

React/Next.js コードをパフォーマンス観点でレビューするサブエージェント。CRITICAL/HIGH 優先で 57 ルールに基づく構造化レポートを日本語で出力。

- **モデル**: Sonnet
- **使用ツール**: Read, Grep, Glob
- **レビュー観点**: ウォーターフォール排除、バンドルサイズ、サーバーサイド最適化、Re-render 最適化など
- **出力**: 重要度別の指摘事項 + 良い実践例を含む Markdown レポート

### composition-reviewer

React コードをコンポジションパターン観点でレビューするサブエージェント。8 ルールに基づく構造化レポートを日本語で出力。

- **モデル**: Sonnet
- **使用ツール**: Read, Grep, Glob
- **レビュー観点**: Boolean props 増殖、Compound Components、状態管理の分離、React 19 API 対応など
- **出力**: 重要度別の指摘事項 + 良い実践例を含む Markdown レポート

## ディレクトリ構成

```
claude-code-toolkit/
├── plugin.json
├── agents/
│   ├── react-perf-reviewer.md
│   └── composition-reviewer.md
└── skills/
    ├── vercel-react-best-practices/   # 65ルール
    ├── vercel-composition-patterns/   # 8ルール
    ├── react-native-skills/           # 37ルール
    ├── frontend-design/
    ├── ui-ux-pro-max/
    ├── design-lab/
    ├── interaction-design/
    ├── canvas-design/
    ├── baseline-ui/
    ├── 12-principles-of-animation/
    ├── fixing-motion-performance/
    ├── fixing-accessibility/
    ├── wcag-audit-patterns/
    ├── web-design-guidelines/
    ├── fixing-metadata/
    └── gstack/                        # サブモジュール
```

## ライセンス

MIT
