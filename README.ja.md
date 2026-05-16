# Agent Skills

[English](README.md) | **日本語**

AI コーディングエージェント向けのスキル定義。各スキルにトリガー・ワークフロー・慣習をまとめています。

## 構造

```
agent-skills/
└── skills/
    ├── pr-drafter/
    │   └── SKILL.md    # リポジトリの PR テンプレートに沿った PR 本文の下書き
    └── sibling-repo/
        └── SKILL.md    # 隣接するローカルリポジトリを読み取り専用コンテキストとして参照
```

## スキル

### [PR Drafter](./skills/pr-drafter/SKILL.md)

リポジトリの PR テンプレートに沿った、レビューワー向けの GitHub PR 本文（または短いブランチ要約）。下書きは `.private/pr-drafts/` に出力。ワークスペースと差分は GitButler（`but`）を使用し、レビュー文脈・リスク・検証内容を重視します。

### [Sibling Repo](./skills/sibling-repo/SKILL.md)

現在の git リポジトリの隣にあるローカルリポジトリを、読み取り専用コンテキストとして参照します。共有型、API、スキーマ、SDK、生成クライアント、環境変数、フィーチャーフラグ、契約や挙動の整合確認に使用します。

## Installation

[skills.sh](https://skills.sh/) の [`skills` CLI](https://skills.sh/docs/cli):

```bash
npx skills add tdkn/agent-skills
```

`-l` は一覧のみ、`-g` はユーザー単位、`--agent` でエージェント指定。詳細は [CLI ドキュメント](https://skills.sh/docs/cli)。テレメトリ無効化は `DISABLE_TELEMETRY=1`。

## コントリビューション

1. `skills/` 配下にディレクトリと `SKILL.md` を追加
2. 上の **スキル** に一行で追記

## ライセンス

[MIT License](LICENSE)
