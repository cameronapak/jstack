# jstack = Jesus stack

I believe Jesus Christ of Nazareth is the source of wisdom and He gives it to those who sincerly ask.

Over my time in the software industry, I've discovered we too easy default how we work to be prescribed by Silicon Valley's "best practices." For example, the software development lifecycle is often run in a cadence of "sprints". We sprint. And sprint. And sprint. And, BAM... We run straight into burnout and depression.

Questions to consider as you build:

- What if there were a better way to work?
- What if your tech stack and software approach was infused with the teachings and values of Jesus?

The goal of this repo is to document what I learn into a series of bite-sized teachings, [skills](https://agentskills.io/home), and resources that can help aid in the software development lifecycle.

This is imperfect and will improve over time.

Contributions welcomed.

## Your app doesn't have to look vibe-coded

A lot of pastors and followers of Jesus are building software for the first time with AI. That's a gift, and at the same time, it also means a lot of apps look the same: purple gradients, generic cards, and that "an agent made this" feel.

**Beautiful interfaces matter because it shows people you put craft and care into what you created.**

If your app looks like every other AI-created app, then someone may ride it off as generic and not give it a second glance.

Here are some AI skills I recommend for UI / UX design and thinking:

1. **[UI Skills](https://www.ui-skills.com/)** - a collection of design-engineering skills for accessibility, motion, frontend craft, and interface quality. Start here when you're about to build or fix a UI.
2. **[Impeccable](https://impeccable.style)** - focused craft for production-grade interfaces that avoid generic AI aesthetics. There's also a [Chrome Extension](https://chromewebstore.google.com/detail/impeccable/bdkgmiklpdmaojlpflclinlofgjfpabf).

## Skills

[skills.sh](https://skills.sh/cameronapak/jstack)

Installable skill content lives in `skills/`.

```bash
# Local repo installation
npx skills add cameronapak/jstack
```

This repo includes agent skills that package the Jesus-centered software guidance into reusable workflows:

### Alignment Skills

- **[ft-discern-christian-app-idea](./skills/ft-discern-christian-app-idea/)** - Discern whether and how to build a Christian app through heart alignment, the Surrender-Scour-Synergize-Sow-Share framework, and the faith.tools selection criteria.
- **[ft-evaluate-christian-ai-apps](./skills/ft-evaluate-christian-ai-apps/)** - Evaluate Christian AI apps against the 6 unofficial guardrails using a 25-question testing framework with scoring rubrics. Covers chatbots and generator tools that draft content a pastor will deliver as their own.

### Discovery Skills

- **[ft-find-bible-developer-resources](./skills/ft-find-bible-developer-resources/)** - Find Bible APIs, SDKs, MCP servers, concordance tools, and licensing info for building Bible-aware applications.

### Development Skills

- **[ft-once-keep-agents-and-readme-fresh](./skills/ft-once-keep-agents-and-readme-fresh/)** - One-time setup skill that adds Documentation Freshness rules to existing agent instruction files so agents keep `AGENTS.md` and `README.md` aligned with repo reality.
- **[ft-remove-ai-code-slop](./skills/ft-remove-ai-code-slop/)** - Cleanup skill for removing obvious AI-generated code slop from a branch diff while preserving the intended feature work.
- **[ft-create-concise-pr](./skills/create-concise-pr/)** - Create or update a pull request with a concise, skimmable snapshot description — full loop from reading the diff to posting via `gh`.

### Additional Skills

Here are additional resources that may be helpful.

- I've benefited a ton from using [Matt Pocock's AI skills](https://github.com/mattpocock/skills/tree/main), especially the `/grill-me` and `/grill-with-docs` skills

## Free AI Christian Chatbot Prompts

Here are some free and open-source AI Bible prompts for LLMs like ChatGPT, Claude, or your favorite agent.

1. [Christian discipleship AI prompt](./prompts/christian-discipleship-ai-prompt.md)
2. [Christian discipleship AI prompt (compact)](./prompts/christian-discipleship-ai-prompt-compact.md) _(This prompt is used on the [ChatGPT Bible Bot GPT](https://go.faith.tools/bible-bot))_
