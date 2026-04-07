# AGENTS.md

Instructions for AI coding agents working on this repository.

## Project overview

This repository hosts **agent skills**: Markdown skill definitions (`SKILL.md`) with YAML front matter, triggers, workflows, and conventions. Skills live under `skills/<skill-name>/`. There is no application runtime, package manager lockfile, or automated test suite at the repo root—changes are documentation and structure.

**Consumers** install the bundle via the [skills CLI](https://skills.sh/docs/cli) (`npx skills add tdkn/agent-skills`).

## Repository layout

```
agent-skills/
├── skills/
│   └── <skill-name>/
│       ├── SKILL.md      # primary English skill (required)
│       └── SKILL.ja.md   # optional Japanese variant
├── .github/
│   └── pull_request_template.md
├── README.md
├── README.ja.md
└── LICENSE
```

Draft PR bodies from skills may reference `.private/pr-drafts/` (gitignored or local drafts); do not treat it as source of truth for the catalog.

## Adding or changing a skill

1. Add a directory under `skills/` containing `SKILL.md` (and optionally `SKILL.ja.md`).
2. Update **both** `README.md` and `README.ja.md` in the **Skills** section when adding a skill or materially changing one.
3. Keep front matter valid: `name`, `description`, and body content aligned with [skills.sh](https://skills.sh/) expectations.
4. Verify that any referenced tools, commands, paths, and workflow steps in the skill still exist and match the intended environment.

## Conventions

- **Language**: Primary skill text is English in `SKILL.md`; Japanese may live in `SKILL.ja.md` where provided.
- **Accuracy**: Skills are procedural—commands and file paths must be copy-paste accurate.
- **Scope**: Prefer one logical change per PR; avoid unrelated drive-by edits.

## Pull requests

The default template is `.github/pull_request_template.md`. Preserve its heading order and checklist semantics; do not tick verification items unless they were actually satisfied.

Suggested title pattern: short, imperative summary of the change (e.g. `docs: add foo skill`).

## Version control (GitButler)

Prefer **GitButler** (`but`) for branch, commit, and diff workflows when available. Avoid raw `git` for mutating operations if project tooling expects `but`; use read-only `git` only when reconciling scope with the user. Load the **`but`** skill from the user’s skill path when performing VCS tasks.

## Testing and CI

There is **no** project-level test or lint command in this repo. Validation is manual: read paths, follow steps in new or edited skills, and ensure README entries match.

## Security

Do not commit secrets, tokens, or machine-specific paths. Skills should describe generic placeholders where credentials would apply.
