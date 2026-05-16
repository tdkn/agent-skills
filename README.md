# Agent Skills

**English** | [日本語](README.ja.md)

Skill definitions for AI coding agents: triggers, workflows, and conventions per skill.

## Structure

```
agent-skills/
└── skills/
    ├── pr-drafter/
    │   └── SKILL.md    # PR description drafts from repo templates
    └── sibling-repo/
        └── SKILL.md    # Read-only context from neighboring local repos
```

## Skills

### [PR Drafter](./skills/pr-drafter/SKILL.md)

Reviewer-ready GitHub PR bodies from the repo’s PR template (or a short branch summary). Writes drafts under `.private/pr-drafts/`; uses GitButler (`but`) for workspace state and diffs, and emphasizes reviewer context, risk, and validation.

### [Sibling Repo](./skills/sibling-repo/SKILL.md)

Read neighboring local repositories beside the current git repo as read-only context for cross-repo contracts, shared types, APIs, schemas, SDKs, generated clients, env vars, feature flags, and behavior alignment.

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
