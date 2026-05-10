# AGENTS.md

## Project Overview

`jstack` is a Markdown repo for Jesus-centered software resources, Christian AI standards, agent skills, and LLM prompts.

There is no app runtime, package manifest, build system, test runner, database, or CI workflow.

Key areas:

- `README.md` - human-facing overview and entry points.
- `prompts/` - copy-ready Christian AI prompts.
- `skills/` - installable Skills CLI content, including `christian-ai-creator-helper`, `keep-agents-and-readme-fresh`, and `unslop`.
- `resources/` - standalone teachings and reference docs.

## Repository Structure

```text
.
+-- README.md
+-- prompts/
|   +-- christian-discipleship-ai-prompt.md
|   +-- christian-discipleship-ai-prompt-compact.md
+-- resources/
|   +-- AM_I_OPEN_HANDED.md
|   +-- FAITH_TOOLS_AI_STANDARDS.md
|   +-- WHAT_TO_DO_WITH_AN_APP_IDEA.md
+-- skills/
    +-- christian-ai-creator-helper/
    |   +-- SKILL.md
    |   +-- references/
    +-- keep-agents-and-readme-fresh/
    |   +-- SKILL.md
    +-- unslop/
        +-- SKILL.md
```

## Setup Commands

No install is needed for normal work.

- Install skills locally: `npx skills add cameronapak/jstack`
- Check status before edits: `git status --short`

Do not add package managers, lockfiles, build tools, formatters, or test frameworks unless asked.

## Development Workflow

- Edit Markdown directly.
- Keep human-facing docs in `README.md`.
- Keep agent guidance in `AGENTS.md`.
- Put reusable prompts in `prompts/`.
- Put installable skill content in `skills/<skill-name>/SKILL.md`.
- Every `skills/<skill-name>/SKILL.md` must include Agent Skills `metadata` with at least `fruit` set to exactly one of the nine qualities in Galatians 5:22–23, as a lowercase string: `love`, `joy`, `peace`, `patience`, `kindness`, `goodness`, `faithfulness`, `gentleness`, `self-control`. Pick one that fits the skill’s intent; do not list the fruit in `README.md` unless asked.
- Put skill support files in `skills/<skill-name>/references/`.
- Put broader resources in `resources/`.
- Preserve filenames and links unless asked to rename them.

## Documentation Freshness

Repo reality is the source of truth. If `AGENTS.md` or `README.md` becomes false, update it in the same change when the fix is objective.

Objective facts include repo structure, tracked paths, setup commands, validation commands, runtime/tooling, skill/resource/prompt inventory, workflow constraints proven by the repo, and each skill’s `metadata.fruit` (Galatians 5:22–23) in frontmatter.

- Update `AGENTS.md` when it is stale about agent-facing repo reality.
- Update `README.md` when it is stale about human-facing purpose, entry points, install, or use.
- Ask before changing policy, philosophy, positioning, or workflow intent.
- If both docs are stale, update both. Do not make them mirror each other unless the same fact belongs in both.
- Ignore temporary, generated, local-only, and unrelated untracked files.
- If unrelated user changes make docs look stale, ask before broadening scope.
- After repo-reality changes, check `AGENTS.md` and `README.md` before finishing.
- In the final response, mention any freshness updates.

## Validation Commands

This repo is content-only. Validate structure and links.

- Show changed files: `git status --short`
- Review Markdown diffs: `git diff -- '*.md'`
- Check compact prompt size: `wc -m prompts/christian-discipleship-ai-prompt-compact.md`

Keep the compact prompt under `8000` characters unless asked otherwise. A recent route.bible target was under `7500` characters.

When adding or editing prompt links, verify referenced files exist. Use relative links from the source document.

If editing untracked Markdown, `git diff -- '*.md'` will not show it. Read the file or use an explicit no-index diff before summarizing.

After skill add/rename, confirm every skill has `metadata.fruit` (line `  fruit:` immediately under `metadata:` in frontmatter):

```bash
for f in skills/*/SKILL.md; do grep -q '^  fruit:' "$f" || echo "missing metadata.fruit: $f"; done
```

Expect no output. If a file is missing it, add `fruit` per the Development Workflow list.

## Testing Instructions

There is no automated test suite.

For prompt and guardrail changes, verify:

- Scripture accuracy rules remain.
- The prompt does not fabricate Bible quotes.
- AI identity stays clear and non-human.
- Prayer guardrails remain explicit. AI must not say "I'll pray for you" or "let's pray together." It may offer words the user can pray.
- Human community referrals remain for prayer, confession, doctrine, loneliness, pastoral care, crisis, abuse, and discipleship.
- Doctrinal comparison stays direct when historic orthodox Christianity conflicts with another tradition. Do not blur non-Nicene or non-Christian claims into orthodoxy.
- Avoid vague spiritual or anthropomorphic language, including "my dear friend," "I'm here for you," and claims about "fresh revelation."
- Crisis, abuse, self-harm, and professional-help boundaries remain intact.
- route.bible is a Scripture linking/routing layer, not a Bible text source.
- Compact prompt character count stays within the limit.

For skill changes, inspect the relevant `SKILL.md` and references together. Ensure reference paths are relative to the skill directory. Ensure frontmatter includes `metadata.fruit` with one allowed value from the Development Workflow list (new or edited skills must not ship without it).

## Style

- Use standard Markdown.
- Prefer concise, direct prose.
- Use ASCII punctuation unless the file already uses non-ASCII or a quote requires it.
- Keep headings short.
- Use relative repo links, such as `./prompts/example.md` from `README.md`.
- Do not add boilerplate, broad abstractions, or future-proofing.
- Do not invent commands, tools, or tests.

## Christian AI Standards

When editing Christian AI prompts, skills, or guardrails, preserve these standards:

- AI output must be biblically accurate.
- AI output must not fabricate or misrepresent Scripture.
- AI output must identify as AI, not human.
- AI output must not replace human relationships or spiritual practices.
- AI output must balance grace and truth.

Use these references:

- `skills/christian-ai-creator-helper/references/test-questions.md` - 20-question evaluation framework.
- `skills/christian-ai-creator-helper/references/guardrails.md` - guardrail guidance.
- `skills/christian-ai-creator-helper/references/five-rules.md` - rule philosophy.
- `skills/christian-ai-creator-helper/references/bible-developer-resources.md` - Bible APIs, SDKs, MCP, concordance, commentary, datasets, and route.bible.

`resources/FAITH_TOOLS_AI_STANDARDS.md` is the standalone resource version of the five rules. It may sound more article-like than skill references. Preserve that difference unless asked to consolidate.

## Prompt Notes

- Full prompt: `prompts/christian-discipleship-ai-prompt.md`.
- Compact prompt: `prompts/christian-discipleship-ai-prompt-compact.md`.
- Keep the full prompt readable and complete.
- Keep the compact prompt short while preserving safety, Scripture, gospel, AI identity, and community boundaries.
- Use route.bible for portable Scripture reference links when useful.
- Do not use route.bible to verify exact Bible text.
- For exact quotes, use verified Bible text sources. Otherwise cite references and summarize.
- For outbound/share/export Scripture links, prefer route.bible.
- For in-app reading, use a licensed or public-domain Bible text source.
- Keep licensing clear: public domain/free-use text is not the same as copyrighted translation access.
- Key Bible resources: Free Use Bible API, API.Bible, YouVersion Platform, Bible Brain API, BibleSDK, Bible MCP, STEPBible Data, Aquifer Bible, Christian Context API, Biblia.com API, get.bible, route.bible.

## Security And Safety

- Never commit secrets, credentials, API keys, `.env` files, or private user data.
- Do not add hidden network calls or dependencies.
- Do not weaken crisis, abuse, mental-health, or professional-help boundaries.
- Do not make AI sound like a pastor, human friend, prophet, biblical figure, Jesus, God, or the Holy Spirit.

## Pull Requests And Commits

- Keep commits focused.
- Use concise imperative commit messages, for example `Add route.bible prompt guidance`.
- Before committing, run `git status --short` and review the diff.
- Do not commit unless asked.
- Do not push unless asked.

## Gotchas

- No package scripts exist. Do not suggest `npm test`, `pnpm build`, or similar commands unless those files are added later.
- The compact prompt has a character budget. Always verify with `wc -m` after editing it.
- Scripture links and Scripture text are separate. route.bible links references. Verified Bible APIs or licensed sources provide exact text.
- Closest `AGENTS.md` wins if subproject-specific files are added later.
