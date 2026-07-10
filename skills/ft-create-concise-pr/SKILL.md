---
name: ft-create-concise-pr
description: Create or update a pull request with a concise, skimmable snapshot description. Use when opening a PR, writing or rewriting a PR description, or refreshing a PR description after review changes.
metadata:
  fruit: self-control
---

# Snapshot PR

A PR description is a snapshot: one glance gives the reviewer the whole picture. A concise description is kindness to the people who review your work. Everything below serves that.

## Gather

Know the whole change before writing a word:

1. Find where the branch forked: `git merge-base HEAD <default-branch>`.
2. Read the full diff and commit messages since the merge base.
3. If a PR already exists (`gh pr view`), read its current description and review comments, then jump to **After review** below.

Done when every changed file is accounted for in your understanding — not necessarily in the description.

## Write

Use exactly this template. Omit sections that don't apply. Never add sections.

```md
## Summary

## Changes

## Flow (only if the gate passes)

## Breaking / Migration (only if applicable)

## Test plan
```

Rules:

- **Title**: imperative mood, under 70 characters.
- **Summary**: max 2 sentences. What changed and why. No "This PR..." openers.
- **Changes**: 3–7 bullets, one line each. Order: behavior changes first, then logic changes, then refactors/chores. Describe intent, not file names — the diff already shows those.
- **Test plan**: one line stating what was actually verified (commands run, flows exercised). If nothing was verified, write `Not tested`. Never invent verification.
- No filler, no adjectives.

### Flow diagram gate

Include a Mermaid diagram (GitHub renders it natively) only when the change alters flow across 3 or more components, or reorders a sequence of operations. Max 8 nodes. Show the new flow only — no before/after pairs. Never diagram what one bullet already explains.

## Apply

Post it: `gh pr create` for a new PR, `gh pr edit --body-file` for an existing one.

Done when the PR on GitHub shows the snapshot description.

## After review

When the PR changes after review:

- Keep the structure. Edit only the bullets affected by new commits.
- Don't let the Summary grow.
- If a change reverses an earlier bullet, replace the bullet rather than appending.
- Refresh the Test plan if new verification happened. Refresh or delete the diagram if the flow changed.
