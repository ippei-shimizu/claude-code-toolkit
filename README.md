# claude-code-toolkit

Claude Code 用の共通スキル・エージェントプラグイン。プロジェクト横断で使える汎用的なツールを集約。

## インストール

プロジェクトの `.claude/plugins/` にクローン（gstackサブモジュール含む）:

```bash
git clone --recurse-submodules https://github.com/ippei-shimizu/claude-code-toolkit.git .claude/plugins/claude-code-toolkit
cd .claude/plugins/claude-code-toolkit/skills/gstack && ./setup
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
| `gstack` | Claude Code用エンジニアリングツールスイート（QA, レビュー, デプロイ等28コマンド） | `/qa`, `/review`, `/ship` 等のスラッシュコマンド |

### エージェント

| エージェント | 説明 |
|-------------|------|
| `react-perf-reviewer` | Reactコードをパフォーマンス観点でレビュー（CRITICAL/HIGH優先、57ルール） |
| `composition-reviewer` | Reactコードをコンポジションパターン観点でレビュー（8ルール） |

## 使用している外部プラグイン

このツールキットとは別に、以下の外部プラグインもプロジェクトで使用:

| プラグイン | 説明 | インストール |
|-----------|------|------------|
| [superpowers](https://github.com/anthropics/claude-code-superpowers) | Claude Code公式の拡張スキル（TDD, デバッグ, プラン作成等） | Claude Code プラグインとして自動インストール |

## ライセンス

MIT
