# jstack = Jesus stack

I believe Jesus Christ of Nazareth is the source of wisdom and He gives it to those who sincerly ask.

Over my time in the software industry, I've discovered we too easy default how we work to be prescribed by Silicon Valley's "best practices." For example, the software development lifecycle is often run in a cadence of "sprints". We sprint. And sprint. And sprint. And, BAM... We run straight into burnout and depression. 

What if there were a better way to work? What if your tech stack and software approach was infused with the teachings and values of Jesus?

The goal of this repo is to document what I learn into a series of bite-sized teachings, [skills](https://agentskills.io/home), and resources that can help aid in the software development lifecycle.

## AI Bible Bot Prompts

Here are some free and open-source AI Bible prompts for LLMs like ChatGPT, Claude, or your favorite agent. 

1. [Christian discipleship AI prompt](./prompts/christian-discipleship-ai-prompt.md)
2. [Christian discipleship AI prompt (compact)](./prompts/christian-discipleship-ai-prompt-compact.md)

## Skills 

[![skills.sh](https://skills.sh/b/cameronapak/jstack)](https://skills.sh/cameronapak/jstack)

Easiest and best way to get started is through using Vercel's [skills](https://skills.sh/docs/cli) package.

This repo includes agent skills that package the Jesus-centered software guidance into reusable workflows:

- **christian-ai-creator-helper** - Evaluate, build, and resource Christian AI apps using the faith.tools 5 unofficial rules, guardrail guidance, Bible developer tools, and a 20-question test framework.
- **keep-agents-and-readme-fresh** - One-time setup skill that adds Documentation Freshness rules to existing agent instruction files so agents keep `AGENTS.md` and `README.md` aligned with repo reality.
- **unslop** - Cleanup skill for removing obvious AI-generated code slop from a branch diff while preserving the intended feature work.

Installable skill content lives in `skills/`.

```bash
# Local repo installation
npx skills add cameronapak/jstack
```
