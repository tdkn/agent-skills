# Agent Skills

[English](README.md) | **日本語**

AI コーディングエージェント向けのスキル定義。各スキルにトリガー・ワークフロー・慣習をまとめています。

## 構造

```
agent-skills/
└── skills/
    └── pr-drafter/
        └── SKILL.md    # リポジトリの PR テンプレートに沿った PR 本文の下書き
```

## スキル

### [PR Drafter](./skills/pr-drafter/SKILL.md)

リポジトリの PR テンプレートに沿った GitHub の PR 本文（または短いブランチ要約）。下書きは `.private/pr-drafts/` に出力。ワークスペースと差分は GitButler（`but`）を使用。

## Installation

[skills.sh](https://skills.sh/) の [`skills` CLI](https://skills.sh/docs/cli)（`npx` のみ。グローバルインストール不要）:

```bash
npx skills add tdkn/agent-skills
```

`-l` は一覧のみ、`-g` はユーザー単位、`--agent` でエージェント指定。詳細は [CLI ドキュメント](https://skills.sh/docs/cli)。テレメトリ無効化は `DISABLE_TELEMETRY=1`。

## コントリビューション

1. `skills/` 配下にディレクトリと `SKILL.md` を追加
2. 上の **スキル** に一行で追記

## ライセンス

[MIT License](LICENSE)
