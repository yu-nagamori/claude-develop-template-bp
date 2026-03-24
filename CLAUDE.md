# Claude Code プロジェクト設定

このリポジトリは Claude Code のプロジェクトテンプレートです。

## プロジェクト概要

Claude Code を効果的に活用するためのベストプラクティステンプレート。
チーム開発における設定・ルール・スキル・エージェントの構成例を提供します。

## ディレクトリ構成

- `CLAUDE.md` - プロジェクト全体の指示（このファイル）
- `.claude/settings.json` - チーム共有設定（hooks, permissions）
- `.claude/settings.local.json` - 個人設定（git-ignored）
- `.claude/rules/` - 自動読み込みルール群
- `.claude/skills/` - スキル（/スラッシュコマンド化）
- `.claude/agents/` - サブエージェント定義
- `.claude/commands/` - レガシーコマンド（skillsに統合済み）

## 基本ルール

- コードスタイルは `.claude/rules/code-style.md` に従う
- テストは `.claude/rules/testing.md` に従う
- セキュリティは `.claude/rules/security.md` に従う

## 言語・フレームワーク

このテンプレートは言語・フレームワーク非依存です。
プロジェクトに合わせてカスタマイズしてください。

## コミットメッセージ

- 日本語で記述
- Conventional Commits 形式を推奨（例: `feat:`, `fix:`, `docs:`）

## レビュー

- `/review` スキルでコードレビューを実行可能
- `.claude/skills/review/checklist.md` のチェックリストに基づく

## デプロイ

- `/deploy` スキルでデプロイ手順を確認可能
