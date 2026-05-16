# Agent Skills

[English](README.md) | **日本語**

AI コーディングエージェント向けのスキル定義。各スキルにトリガー・ワークフロー・慣習をまとめています。

## スキル

| スキル | 説明 |
| --- | --- |
| [PR Drafter](./skills/pr-drafter/SKILL.md) | リポジトリのテンプレートまたはブランチ要約から、レビュアー向けの GitHub PR 本文を下書きします。 |
| [Sibling Repo](./skills/sibling-repo/SKILL.md) | クロスリポジトリの契約や挙動を確認するため、隣接するローカルリポジトリを読み取り専用コンテキストとして使います。 |

## インストール

[skills.sh](https://skills.sh/) の [`skills` CLI](https://skills.sh/docs/cli) を使います。

```bash
npx skills add tdkn/agent-skills
```

## コントリビューション

1. `skills/` 配下にディレクトリと `SKILL.md` を追加
2. 上の **スキル** に簡潔に記載

## ライセンス

[MIT License](LICENSE)
