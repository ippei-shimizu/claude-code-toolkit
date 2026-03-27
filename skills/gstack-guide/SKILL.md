---
name: gstack-guide
description: gstack（Claude Code用エンジニアリングツールスイート）の使い方ガイド。gstackのコマンド一覧、開発フロー、インストール方法を参照する。「gstackの使い方」「gstackのコマンド」などで起動する。
---

# gstack 使い方ガイド

gstack は Garry Tan 製の Claude Code 用エンジニアリングツールスイート。AIエージェントに組織的な役割（CEO、EM、QAリード等）を割り当て、開発プロセスを自動化する。

## インストール

### グローバル（全プロジェクト共通）

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
cd ~/.claude/skills/gstack && ./setup
```

### プロジェクトローカル

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git .claude/skills/gstack
cd .claude/skills/gstack && ./setup
```

プロジェクトローカルの場合、`.gitignore` に以下を追加:

```
.claude/skills/gstack/
```

setupで作成されるシンボリックリンク（`autoplan`, `browse`, `qa` 等）も `.gitignore` に追加する。

### 前提条件

- Bun v1.0+（`brew install oven-sh/bun/bun`）
- Git

## 開発フロー

```
Think → Plan → Build → Review → Test → Ship → Reflect
```

```
/office-hours → /plan-ceo-review → /plan-eng-review → 実装 → /review → /qa → /ship
```

## コマンド一覧

### 企画・設計

| コマンド | 役割 | 内容 |
|----------|------|------|
| `/office-hours` | プロダクト思考家 | 要件を再考し実装案を生成。Startup / Builder の2モード |
| `/plan-ceo-review` | CEO | スコープと製品ビジョンを評価。4モード（SCOPE EXPANSION / SELECTIVE / HOLD / REDUCTION） |
| `/plan-eng-review` | EM | アーキテクチャ設計・技術検証 |
| `/plan-design-review` | デザインレビュー | UIデザイン監査（レポートのみ） |
| `/design-review` | デザインレビュー | UIデザイン監査 + 修正ループ |
| `/design-consultation` | デザインコンサル | デザインシステムをゼロから構築。DESIGN.md作成 |
| `/autoplan` | 自動レビュー | CEO → デザイン → EMレビューを自動パイプライン実行 |

### 実装・レビュー

| コマンド | 役割 | 内容 |
|----------|------|------|
| `/review` | スタッフエンジニア | コードレビューと自動修正 |
| `/cso` | セキュリティ責任者 | OWASP Top 10 / STRIDE脅威モデル分析 |
| `/investigate` | デバッガー | 体系的な根本原因分析（4フェーズ） |
| `/codex` | セカンドオピニオン | OpenAI Codex CLIでの独立レビュー |

### テスト・QA

| コマンド | 役割 | 内容 |
|----------|------|------|
| `/qa` | QAリード | ヘッドレスブラウザでテスト実行・バグ修正。3ティア（Quick/Standard/Exhaustive） |
| `/qa-only` | QAリード | テスト実行・レポートのみ（修正なし） |
| `/browse` | QAエンジニア | ヘッドレスブラウザ操作（ページ遷移、スクショ等）~100ms/コマンド |
| `/benchmark` | パフォーマンス | パフォーマンスリグレッション検出。Core Web Vitals追跡 |

### デプロイ・運用

| コマンド | 役割 | 内容 |
|----------|------|------|
| `/ship` | リリースエンジニア | テスト → PR作成 → デプロイ |
| `/land-and-deploy` | リリース | マージ → デプロイ → canary検証 |
| `/canary` | 監視 | デプロイ後の監視ループ |
| `/setup-deploy` | セットアップ | デプロイ設定の初期化 |
| `/document-release` | ドキュメント | リリース後のドキュメント更新 |

### ユーティリティ

| コマンド | 内容 |
|----------|------|
| `/retro` | 振り返り・レトロスペクティブ |
| `/freeze` | 編集をディレクトリにスコープ制限 |
| `/unfreeze` | freeze解除 |
| `/careful` | 破壊的コマンドの安全ガード |
| `/guard` | careful + freeze の最大安全モード |
| `/connect-chrome` | 実ブラウザ接続（Side Panel拡張付き） |
| `/setup-browser-cookies` | ブラウザCookieインポート |
| `/gstack-upgrade` | gstack自体のアップデート |

## 使い方の例

```
# 新機能の企画から始める
/office-hours

# コードレビューを依頼
/review

# ブラウザでQAテスト
/qa

# セキュリティ監査
/cso

# PR作成からデプロイまで一気に
/ship

# 自動パイプライン（CEO→デザイン→EMレビュー）
/autoplan
```

## 管理

- アップデート: `/gstack-upgrade`
- テレメトリ: オプトイン（スキル名と実行時間のみ。コードやプロンプトは送信されない）
- ライセンス: MIT
