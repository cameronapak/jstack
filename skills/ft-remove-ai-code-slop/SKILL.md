---
name: ft-remove-ai-code-slop
description: Removes AI-generated code slop from a git branch diff. Cuts unnecessary comments, verbose patterns, and redundant code while preserving intent. Invoke when you want to clean up AI-generated code in a branch.
metadata:
  fruit: self-control
---

# Unslop

Check the diff against the branch's merge base (where it forked from). Remove all AI-generated slop introduced in this branch.

Be moderate — remove obvious slop and collapse verbose AI patterns into idiomatic code, but do not question whether feature logic deserves to exist. Trust the intent behind what was added; just make it cleaner.

## Comments

- Cut every new comment that doesn't explain *why*
- Preserve pre-existing comments and any "why" comment that earns its place

## What to Cut

| Target | Why It Dies |
| --- | --- |
| `any` types | Replace with proper types |
| Comments that restate the code | The code already says it |
| Verbose error handling that adds no value | Let errors propagate naturally |
| Redundant null checks | Unnecessary optional chaining |
| Unnecessary async/await | Only async when you await |
| Unnecessary else blocks after return | The return already handles it |
| Wrapper functions that delegate and add nothing | Call the thing directly |
| Excessive spreading | Pass the original when it works |
| JSDoc on obvious functions | The name says enough |
| Nested conditionals that could be early returns | Flatten the logic |
| Unused imports | Dead weight |
| Verbose variable names that add no clarity | Shorter when the context is obvious |

## What to Keep

- Pre-existing comments and conventions
- "Why" comments that explain non-obvious reasoning
- Verbose variable names that are genuinely self-explanatory and helpful
- Feature logic — even if it looks like it could be simpler, trust the intent

## Principles

- **Only touch changed lines** — the agent reads the full repo for context but only edits what this branch introduced
- **One idea per function** — collapse when AI padded it out, but don't refactor what was already there
- **No word is sacred** — especially the ones the AI added
- **Clarity over style** — idiomatic, not clever
- **Fix inconsistent formatting** in functions the diff touches, even on unchanged lines

## Rules

- Do NOT commit changes — leave edits unstaged
- Report at the end with only a 1-3 sentence summary of what changed
