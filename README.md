# Agent Skills

**English** | [日本語](README.ja.md)

Skill definitions for AI coding agents: triggers, workflows, and conventions per skill.

## Structure

```
agent-skills/
└── skills/
    └── pr-drafter/
        └── SKILL.md    # PR description drafts from repo templates
```

## Skills

### [PR Drafter](./skills/pr-drafter/SKILL.md)

GitHub PR bodies from the repo’s PR template (or a short branch summary). Writes drafts under `.private/pr-drafts/`; uses GitButler (`but`) for workspace state and diffs.

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
