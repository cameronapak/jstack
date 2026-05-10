# AGENTS.md

## Project Overview

`jstack` is a Markdown-first repository for Jesus-centered software development resources, Christian AI standards, reusable agent skills, and LLM prompt templates.

This repo currently contains content only. There is no app runtime, package manager manifest, build system, test runner, database, or CI workflow checked in.

Key areas:

- `README.md` - human-facing repo overview and entry points.
- `prompts/` - copy-ready Christian AI prompt templates.
- `.agents/skills/` - local agent skill packages tracked in this repo, including `christian-ai-creator-helper` and `unslop`.
- `skills/` - installable Skills CLI package content, currently `christian-ai-creator-helper`.
- `resources/` - standalone teachings and reference documents, including the faith.tools AI standards source material.

## Repository Structure

```text
.
+-- README.md
+-- .agents/
+|   +-- skills/
+|       +-- christian-ai-creator-helper/
+|       +-- unslop/
+-- prompts/
|   +-- christian-discipleship-ai-prompt.md
|   +-- christian-discipleship-ai-prompt-compact.md
+-- resources/
|   +-- AM_I_OPEN_HANDED.md
|   +-- FAITH_TOOLS_AI_STANDARDS.md
|   +-- WHAT_TO_DO_WITH_AN_APP_IDEA.md
+-- skills/
    +-- christian-ai-creator-helper/
        +-- SKILL.md
        +-- references/
```

## Setup Commands

No dependency installation is required for normal work in this repo.

- Install this repo's skills locally through the Skills CLI: `npx skills add cameronapak/jstack`
- Check repository status before editing: `git status --short`

Do not add a package manager, lockfile, build tool, formatter, or test framework unless the user explicitly asks for one.

## Development Workflow

- Edit Markdown directly.
- Keep human-facing documentation in `README.md` concise.
- Put agent-specific operational guidance in `AGENTS.md`.
- Put reusable prompts in `prompts/`.
- Put installable Skills CLI skill content in `skills/<skill-name>/SKILL.md` with supporting files under `skills/<skill-name>/references/`.
- Keep tracked local agent skill copies in `.agents/skills/<skill-name>/` aligned when they represent the same skill content.
- Use `.agents/skills/unslop/SKILL.md` for branch-diff cleanup guidance; it is a local skill, not part of the installable `skills/` package.
- Put broader resource documents in `resources/`.
- Preserve existing filenames and links unless a rename is requested.

## Validation Commands

Because this is a content repo, validation is mostly structural and link-oriented.

- Show changed files: `git status --short`
- Review Markdown diffs: `git diff -- '*.md'`
- Validate compact prompt size: `wc -m prompts/christian-discipleship-ai-prompt-compact.md`

The compact prompt should stay under `8000` characters unless the user changes that requirement. A recent target used for route.bible work was under `7500` characters.

If adding or editing prompt links, verify the referenced files exist and use relative links from the source document.

If editing untracked Markdown files, `git diff -- '*.md'` will not show them. Read the file or use an explicit no-index diff before summarizing changes.

## Testing Instructions

There is no automated test suite configured.

For prompt and guardrail changes, manually verify:

- Scripture accuracy rules are preserved.
- The prompt does not encourage fabricated Bible quotes.
- AI identity remains clear and non-anthropomorphic.
- Prayer guardrails remain explicit: AI must not say "I'll pray for you" or "let's pray together"; it may offer wording the user can pray.
- Human community referrals remain present for prayer, confession, doctrinal questions, loneliness, pastoral care, crisis, abuse, and ongoing discipleship.
- Doctrinal comparison stays direct when historic orthodox Christianity conflicts with another tradition; do not blur non-Nicene or non-Christian claims into orthodoxy.
- Avoid vague spiritual or anthropomorphic language such as "my dear friend," "I'm here for you," or claims about "fresh revelation" stirring in the user.
- Crisis, abuse, self-harm, and professional-help boundaries remain intact.
- route.bible is described as a Scripture linking/routing layer, not a Bible text source.
- Compact prompt character count remains within the requested limit.

For skill changes, inspect the relevant `SKILL.md` and referenced files together. Make sure paths in the skill are correct relative to the skill directory. If changing `christian-ai-creator-helper`, update both `.agents/skills/christian-ai-creator-helper/` and `skills/christian-ai-creator-helper/` unless there is a deliberate reason for them to diverge.

## Code Style And Content Guidelines

- Use standard Markdown.
- Prefer concise, direct prose.
- Use ASCII punctuation unless the surrounding document already uses non-ASCII or the quoted material requires it.
- Keep headings short and descriptive.
- Use relative links for repository files, for example `./prompts/example.md` from `README.md`.
- Do not add generated boilerplate, broad abstractions, or future-proofing that the repo does not need.
- Do not invent commands, tools, or tests that are not present in the repo.

## Christian AI Standards

When editing Christian AI prompts, skills, or guardrails, preserve these core standards:

- AI output must be biblically accurate.
- AI output must not fabricate or misrepresent Scripture.
- AI output must clearly identify as AI, not human.
- AI output must not replace human relationships or spiritual practices.
- AI output must balance grace and truth.

Use `skills/christian-ai-creator-helper/references/test-questions.md` for the 20-question evaluation framework, `skills/christian-ai-creator-helper/references/guardrails.md` for guardrail guidance, `skills/christian-ai-creator-helper/references/five-rules.md` for the philosophy behind the rules, and `skills/christian-ai-creator-helper/references/bible-developer-resources.md` for Bible API, SDK, MCP, concordance, commentary, dataset, and route.bible resources.

`resources/FAITH_TOOLS_AI_STANDARDS.md` is a standalone resource version of the five rules. It may use a more article-like voice than the skill references; preserve that distinction unless asked to consolidate.

## Prompt Editing Notes

- Full prompt: `prompts/christian-discipleship-ai-prompt.md`.
- Compact prompt: `prompts/christian-discipleship-ai-prompt-compact.md`.
- Keep the full prompt comprehensive and readable.
- Keep the compact prompt short while preserving the core safety, Scripture, gospel, AI identity, and community boundaries.
- Use route.bible for portable Scripture reference links when appropriate.
- Do not treat route.bible as verification for exact Bible text.
- Prefer verified Bible text sources for exact quotations; otherwise cite references and summarize without claiming exact wording.
- For outbound/share/export Scripture links, prefer route.bible. For in-app reading, use a licensed or public-domain Bible text source.
- Bible resource guidance should keep licensing clear: public domain/free-use text is not the same as copyrighted translation access.
- Key Bible developer resources currently include Free Use Bible API, API.Bible, YouVersion Platform, Bible Brain API, BibleSDK, Bible MCP, STEPBible Data, Aquifer Bible, Christian Context API, Biblia.com API, get.bible, and route.bible.

## Security And Safety

- Never commit secrets, credentials, API keys, `.env` files, or private user data.
- Do not add hidden network calls or dependencies.
- Be careful with Christian spiritual-care content: do not weaken crisis, abuse, mental-health, or professional-help boundaries.
- Do not make AI sound like a pastor, human friend, prophet, biblical figure, Jesus, God, or the Holy Spirit.

## Pull Request And Commit Guidelines

- Keep commits focused on one logical change.
- Use concise imperative commit messages, for example `Add route.bible prompt guidance`.
- Before committing, run `git status --short` and review the diff.
- Do not commit unless the user explicitly asks.
- Do not push unless the user explicitly asks.

## Known Gotchas

- The repo has no package scripts; do not suggest `npm test`, `pnpm build`, or similar commands unless those files are added later.
- The compact prompt has a character budget; always verify with `wc -m` after editing it.
- Scripture links and Scripture text are separate concerns: route.bible links references, while verified Bible APIs or licensed sources provide exact text.
- Closest `AGENTS.md` takes precedence if subproject-specific files are added later.
