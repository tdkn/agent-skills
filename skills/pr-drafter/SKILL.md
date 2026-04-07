---
name: pr-drafter
description: >-
  Use this skill when the user wants a GitHub pull request body that follows
  the repository PR template, or a concise summary of branch changes for
  reviewers. Apply for informal asks like "write the PR" or "summarize this
  branch" even when they do not mention templates or GitHub explicitly.
---

# PR Drafter

Build PR description Markdown from **whatever PR template the repo actually uses** (headings, checklist rows, and HTML comment instructions), then **write it to a file under `.private/pr-drafts/`**—not only as chat output.

Follow the **workflow** in order. Use **rules for the PR body** while drafting. Skim **common mistakes** before finishing.

## Workflow

1. **Confirm merge base and PR head** — Ask the user to name **merge base** (e.g. `main`) and **PR head** (the branch that contains the PR changes). Do not guess. Cross-check with:

```bash
but status -fv  # current branches, stacks, and CLI IDs
```

If that output disagrees with the user, **prefer the user** (workspace vs GitHub head can differ). Do not state base/head relationships as fact beyond what the user confirmed; GitButler’s internal base may differ from GitHub’s.

2. **Use GitButler (`but`)** — Load the GitButler (but) agent skill when your environment exposes it and follow it. If it does not load:

```bash
but --help  # discover subcommands and flags
```

Use `but` for workspace state and diffs. Do **not** use `git` to mutate history or the working tree. Use read-only `git` only if you must reconcile **base..head** with the user’s intent and `but` alone is not enough—avoid it by default.

3. **Resolve and read the PR template** — Templates differ by project; resolve explicitly—do not assume a fixed layout.
   - **Default**: `.github/pull_request_template.md` at the repo root (common GitHub convention).
   - **Alternatives**: `.github/PULL_REQUEST_TEMPLATE/*.md`, `docs/` variants, or a path the user names. If multiple exist, prefer the one the project documents or ask the user.
   - **None found**: ask for the template path or the sections the team expects, then follow that.

   Read the file end-to-end. Treat **HTML comments** as author instructions: follow them even when they conflict with generic rules below (project wins).

4. **Gather facts** — Resolve the head branch’s **CLI ID** from `but status` each time (IDs change). Typical order:

```bash
but status -fv  # branch CLI IDs and apply state
but branch show <branch-id> -f  # commits ahead of base and per-commit file changes
but diff <branch-id>  # full branch diff when needed (use --no-tui in automation if TUI opens)
but branch show <branch-id> --ai  # optional draft summary—verify against commits/diff before using
```

5. **Draft, persist, and hand off** — Fill placeholders using commits and diffs. Apply **Rules for the PR body** below. Map changes to any “scope” or “type” checklists using paths and commit messages; only check “what we verified” items that actually apply.

   **Persist**:
   - Path: **`.private/pr-drafts/<filename>.md`** (repo root–relative).
   - Create **`.private/pr-drafts/`** if it does not exist.
   - **Filename**: filesystem-safe stem from the confirmed **PR head** branch (e.g. replace `/` with `-`); if that collides or is empty, use a short ISO date prefix (e.g. `2026-04-06-<stem>.md`).

   **Write** the file with the full Markdown content, tell the user the path, and give a **short chat summary or copy-paste block** of the same body so they can drop it into GitHub without opening the file.

## Rules for the PR body

- **Heading fidelity**: Keep the template’s **`##` / `###` titles and their order** exactly as written. Do not translate, rename, or add sections the template does not define.
- **Checklists**: If the template includes `- [ ]` lines, **keep every row** unless the template explicitly tells you to drop rows or sections. Leave items **unchecked** when you did not run or verify them; do not tick boxes to “look done.”
- **Placeholders**: Replace issue/PR placeholders (e.g. incomplete `Closes #`, empty `Fixes #`) with a real reference when the user confirms one; otherwise **remove the broken line** so GitHub keywords stay valid.
- **Optional sections**: Some templates say to **delete whole sections** when not applicable (e.g. screenshots). Others want the heading left with “N/A.” **Follow the template comments**, not a global rule.
- **Deliverable cleanliness**: Strip HTML comments from the **pasted PR body** when they are only agent notes and would clutter the review; keep the structure those comments required.

## Common mistakes

<!-- prettier-ignore -->
| Mistake | Why it hurts |
|:---|:---|
| Inventing headings or reordering the template | Breaks team conventions and review bots. |
| Removing checklist lines to shorten the PR | Violates explicit template rules; reviewers lose signal. |
| Checking verification boxes without evidence | Misleading for CI/review; only check what you or the user confirmed. |
| Copying a summary from another repo's template shape | Wrong sections, wrong language, or missing required blocks. |
| Trusting tool "base" without user confirmation | GitButler/GitHub merge bases can differ; wrong "what changed" narrative. |
| Leaving `Closes #` or similar with no number | Invalid or confusing GitHub linking. |
