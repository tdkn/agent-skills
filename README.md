# Agent Skills

**English** | [日本語](README.ja.md)

Skill definitions for AI coding agents: triggers, workflows, and conventions per skill.

## Skills

| Skill | Description |
| --- | --- |
| [PR Drafter](./skills/pr-drafter/SKILL.md) | Drafts reviewer-ready GitHub PR bodies from the repo template or branch summary. |
| [Other Repo](./skills/other-repo/SKILL.md) | Uses other local repos as read-only context for cross-repo contracts and behavior. |

## Installation

Use the [`skills` CLI](https://skills.sh/docs/cli) from [skills.sh](https://skills.sh/):

```bash
npx skills add tdkn/agent-skills
```

## Contributing

1. Add a directory under `skills/` with a `SKILL.md`
2. Document it briefly in **Skills** above

## License

[MIT License](LICENSE)
