---
name: keep-agents-and-readme-fresh
description: One-time setup skill that adds Documentation Freshness rules to existing AGENTS.md or CLAUDE.md files so agents keep AGENTS.md and README.md aligned with repo reality. Use when you want future coding-agent sessions to update agent and human docs when objective repo facts change.
---

# Keep Agents And README Fresh

Install the canonical Documentation Freshness policy into existing agent instruction files. This is an additive, one-time setup task.

## Canonical Section

```md
## Documentation Freshness

Repo reality is the source of truth. If `AGENTS.md` or `README.md` becomes false, update it in the same change when the fix is objective.

Objective facts include repo structure, tracked paths, setup commands, validation commands, runtime/tooling, skill/resource/prompt inventory, and workflow constraints proven by the repo.

- Update `AGENTS.md` when it is stale about agent-facing repo reality.
- Update `README.md` when it is stale about human-facing purpose, entry points, install, or use.
- Ask before changing policy, philosophy, positioning, or workflow intent.
- If both docs are stale, update both. Do not make them mirror each other unless the same fact belongs in both.
- Ignore temporary, generated, local-only, and unrelated untracked files.
- If unrelated user changes make docs look stale, ask before broadening scope.
- After repo-reality changes, check `AGENTS.md` and `README.md` before finishing.
- In the final response, mention any freshness updates.
```

## Workflow

1. Find existing `AGENTS.md` and `CLAUDE.md` files in the repo.
2. If none exist, stop. Tell the user this skill is additive and recommend creating an agent instruction file first with `https://skills.sh/github/awesome-copilot/create-agentsmd`.
3. Prefer `AGENTS.md` over sibling `CLAUDE.md` in the same directory.
4. If both sibling files exist and are not symlinked, update `AGENTS.md` only and recommend symlinking them if they are meant to stay identical.
5. Update every active existing agent instruction file, including nested files, because the closest instruction file can take precedence.
6. If more than 5 target files are found, list them and ask before bulk editing.
7. Do not create new `AGENTS.md` or `CLAUDE.md` files.
8. Do not create backup files.
9. Do not commit changes.

## Placement

- If a file already has the exact canonical section, leave it unchanged.
- If a file has a partial or older `Documentation Freshness` section with the same policy intent, replace that section with the canonical section.
- If a `Documentation Freshness` section has different or broader meaning, ask before replacing it.
- Otherwise insert the canonical section after workflow or overview material, before validation, testing, style, or contribution sections.
- Keep the canonical wording exact. Only adapt surrounding placement or heading context if required by the file.

## Final Report

Report only:

- Files updated.
- Files that already had the section.
- Any symlink recommendation for duplicate sibling `AGENTS.md` and `CLAUDE.md` files.
