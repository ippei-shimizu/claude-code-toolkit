# claude-code-toolkit

Claude Code 用の共通スキル・エージェントプラグイン。プロジェクト横断で使える汎用的なツールを集約。

## インストール

プロジェクトの `.claude/plugins/` にクローン:

```bash
git clone https://github.com/ippei-shimizu/claude-code-toolkit.git .claude/plugins/claude-code-toolkit
```

`.gitignore` に追加:

```
.claude/plugins/claude-code-toolkit/
```

## 含まれるコンポーネント

### スキル

| スキル | 説明 | トリガー |
|--------|------|----------|
| `vercel-react-best-practices` | Vercel Engineering によるReact/Next.jsパフォーマンス最適化（65ルール） | React/Next.jsコード作業時に自動適用 |
| `vercel-composition-patterns` | Reactコンポジションパターン（8ルール、React 19対応） | コンポーネント設計・リファクタリング時に自動適用 |
| `react-native-skills` | React Native/Expoベストプラクティス | モバイルアプリ開発時に自動適用 |
| `gstack-guide` | gstack使い方ガイド（全コマンド一覧・開発フロー） | 「gstackの使い方」「gstackのコマンド」 |

### エージェント

| エージェント | 説明 |
|-------------|------|
| `react-perf-reviewer` | Reactコードをパフォーマンス観点でレビュー（CRITICAL/HIGH優先、57ルール） |
| `composition-reviewer` | Reactコードをコンポジションパターン観点でレビュー（8ルール） |

## 使用している外部プラグイン

このツールキットとは別に、以下の外部プラグインもプロジェクトで使用:

| プラグイン | 説明 | インストール |
|-----------|------|------------|
| [gstack](https://github.com/garrytan/gstack) | Claude Code用エンジニアリングツールスイート（QA, レビュー, デプロイ等28コマンド） | `git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git .claude/skills/gstack && cd .claude/skills/gstack && ./setup` |
| [superpowers](https://github.com/anthropics/claude-code-superpowers) | Claude Code公式の拡張スキル（TDD, デバッグ, プラン作成等） | Claude Code プラグインとして自動インストール |

## ライセンス

MIT
