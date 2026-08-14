---
name: ft-rightsize-agents-md
description: Cut always-on AGENTS.md and CLAUDE.md down to identity, gotchas, guardrails, and router pointers. Use when agent instruction files have grown too large or when you want to trim always-on guidance.
disable-model-invocation: true
metadata:
  fruit: self-control
---

# Rightsize AGENTS.md

Before rewriting, read the `writing-for-agents` skill. If it is missing locally, fetch https://raw.githubusercontent.com/mattpocock/skills/main/skills/productivity/writing-for-agents/SKILL.md.

## Steps

1. **Locate.** Open the file the user named. Default: repo-root `AGENTS.md`, then `CLAUDE.md`. Treat both as one always-on budget. Open a nested file only when the user named it. Edit `.cursor/rules` only when the user named them.
   Done when the target path is known and the current text is in context.

2. **Scan the environment.** README, package manifests, scripts, linters, existing skills, docs indexes. The environment is source of truth.
   Done when every block is marked confessed (the repo already states it) or unconfessed (only this file would).

3. **Classify.** Label every block keep, pointer, or delete using the taxonomy below. Create a skill only when the user asks.
   Done when every heading and every bullet has one label.

4. **Rewrite.** Replace the file in place. Phrase the target behavior. One meaning, one place. Leading words over restated triads. If `AGENTS.md` and `CLAUDE.md` both exist, put shared lines in `AGENTS.md` and keep `CLAUDE.md` as `@AGENTS.md` plus Claude-only notes. If the file is missing, write a thin router: identity plus pointers.
   Done when every remaining line is identity, gotcha, guardrail, or a pointer.

5. **Report.** What stayed, what became a pointer, what died, line count before and after. Name skill candidates. Stop after the report.
   Done when every keep, pointer, and delete is named, with before/after line counts.

## Taxonomy

**Keep** (always-on):

- Identity: 1 to 3 sentences for where this repo is
- Gotcha: a landmine or non-standard convention the repo does not confess
- Guardrail: a hard safety constraint that judgement cannot replace
- Router pointer: a named doc or skill plus the branch that should open it
- A line that this file stays brief

**Pointer** (move out of always-on):

- A workflow used on some tasks, not all (verify, review, deploy, auth)
- A long convention that already lives in a doc, or should
- Claude-only notes: live under the `@AGENTS.md` import, not copied

**Delete**:

- Preamble
- Directory overviews and architecture tours
- Discoverable env: runtime, package manager, scripts the manifest already names
- Style the linter already enforces
- Overconstrained rules and constraining examples
- README restates, `/init` filler, no-ops, repeats
- Sediment: a rule added after one failure that no longer trips the agent

## Pointer wording

Front-load the leading word. One trigger per branch. Cut identity the target already carries.

```
## Testing
Testing or coverage: read `docs/testing.md`.
```

## Target shape

```
# <repo>

<1 to 3 sentence identity>

Keep this file brief. Put task-specific guidance behind a pointer.

## Gotchas
- <landmine or non-standard convention the repo does not confess>

## Guardrails
- <hard safety constraint judgement cannot replace>

## <Branch>
<pointer>
```

Omit empty Gotchas or Guardrails headings.
