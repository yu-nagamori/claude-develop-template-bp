# Claude Code プロジェクトテンプレート

Claude Code を効果的に活用するためのベストプラクティステンプレートです。

## 概要

このテンプレートは、チーム開発で Claude Code を導入する際の推奨ディレクトリ構成を提供します。ルール・スキル・エージェント・設定ファイルの構成例が含まれています。

## ディレクトリ構成

```
project-root/
├── CLAUDE.md                        # プロジェクト全体の指示
├── .claude/
│   ├── settings.json                # チーム共有設定（hooks, permissions）
│   ├── settings.local.json          # 個人設定（git-ignored）
│   ├── rules/                       # 自動読み込みルール群
│   │   ├── code-style.md            #   コードスタイルルール
│   │   ├── testing.md               #   テストルール
│   │   └── security.md              #   セキュリティルール
│   ├── skills/                      # スキル（/スラッシュコマンド化）
│   │   ├── deploy/
│   │   │   └── SKILL.md             #   デプロイ手順スキル
│   │   └── review/
│   │       ├── SKILL.md             #   コードレビュースキル
│   │       └── checklist.md         #   レビューチェックリスト
│   ├── agents/                      # サブエージェント定義
│   │   └── code-reviewer/
│   │       └── AGENT.md             #   コードレビューエージェント
│   └── commands/                    # レガシー（skillsに統合済み）
│       └── test.md
├── .gitignore
├── LICENSE
└── README.md
```

## 各ディレクトリの役割

### `CLAUDE.md`

プロジェクト全体の指示を記述するファイルです。Claude Code が最初に読み込みます。プロジェクトの概要、基本ルール、開発フローなどを200行以内で簡潔に記述します。

### `.claude/settings.json`

チームで共有する Claude Code の設定ファイルです。Git で管理します。

- **permissions**: 許可・拒否するツールの設定
- **hooks**: コミット前チェックなどのフック設定

### `.claude/settings.local.json`

個人用の設定ファイルです。`.gitignore` に追加されており、Git 管理対象外です。個人の環境固有の設定を記述します。

### `.claude/rules/`

Claude Code が自動で読み込むルールファイルを格納します。

| ファイル | 内容 |
|---------|------|
| `code-style.md` | 命名規則、フォーマット、コメントのルール |
| `testing.md` | テストの書き方、カバレッジ方針 |
| `security.md` | セキュリティに関するルール |

### `.claude/skills/`

`/スラッシュコマンド` として実行できるスキルを定義します。各スキルは `SKILL.md` に手順を記述します。

| スキル | コマンド | 内容 |
|--------|---------|------|
| deploy | `/deploy` | デプロイ手順の確認・実行 |
| review | `/review` | コードレビューの実行 |

### `.claude/agents/`

サブエージェントを定義します。`AGENT.md` に役割・手順・出力形式を記述します。

| エージェント | 内容 |
|------------|------|
| code-reviewer | コード変更の自動レビュー |

### `.claude/commands/`

レガシーコマンド置き場です。`skills/` に統合済みですが、後方互換性のために残しています。

## 使い方

### 1. テンプレートをコピー

```bash
git clone https://github.com/yu-nagamori/claude-develop-template-bp.git
cp -r claude-develop-template-bp/.claude your-project/.claude
cp claude-develop-template-bp/CLAUDE.md your-project/CLAUDE.md
```

### 2. プロジェクトに合わせてカスタマイズ

- `CLAUDE.md` にプロジェクト固有の情報を記述
- `.claude/rules/` にプロジェクトのルールを追加・編集
- `.claude/skills/` に必要なスキルを追加
- `.claude/settings.json` で permissions を調整

### 3. `.gitignore` に追加

```gitignore
.claude/settings.local.json
```

## カスタマイズ例

### ルールの追加

`.claude/rules/` に新しい `.md` ファイルを追加するだけで、Claude Code が自動的に読み込みます。

```bash
# 例: APIガイドラインを追加
echo "# API設計ルール\n\n- RESTful設計に従う\n- ..." > .claude/rules/api-guidelines.md
```

### スキルの追加

```bash
mkdir -p .claude/skills/my-skill
cat > .claude/skills/my-skill/SKILL.md << 'EOF'
# My Skill
実行手順を記述...
EOF
```

### エージェントの追加

```bash
mkdir -p .claude/agents/my-agent
cat > .claude/agents/my-agent/AGENT.md << 'EOF'
# My Agent
役割と手順を記述...
EOF
```

## ライセンス

MIT License
