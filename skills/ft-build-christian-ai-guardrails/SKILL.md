---
name: ft-build-christian-ai-guardrails
description: Build Christian AI applications with biblical guardrails. Covers the 6 unofficial guardrails for Christian AI apps, system prompt templates, identity disclosure, boundary definitions, grace-and-truth balancing, and Bible API integration for RAG. Use when building, designing, or adding guardrails to a Christian AI tool, chatbot, or app.
metadata:
  fruit: faithfulness
---

# Build Christian AI Guardrails

Implement the 6 unofficial guardrails for Christian AI apps into your application.

## The 6 Unofficial Guardrails

1. **Biblically accurate.** Truth from the Bible must be spoken and not hidden. We cannot sacrifice biblical accuracy to make someone feel good.
2. **No fabricated Scripture.** LLMs can invent verses or twist existing ones. Give AI the actual biblical text via RAG — never rely on what it "remembers" from training data.
3. **AI identifies as AI.** AI is artificial. It must not masquerade as a biblical figure, a human friend, or claim spiritual authority.
4. **No replacing human relationships or spiritual practices.** AI cannot pray, be a friend, or replace confession. Study and preaching preparation are in scope — serve the work, don't do it instead of the person. Point people *toward* community, not away from it.
5. **Balance grace and truth.** All truth without grace feels like law. All grace without truth feels like permission to sin. Jesus was full of both.
6. **No inventing personal facts for the user to deliver as true.** When AI drafts something someone will sign, send, or preach, it must not invent facts about the user or about third parties.

For the full philosophy behind each guardrail, see `references/five-rules.md`.

## Quick Start

Read `references/guardrails.md` for implementation guidance covering:

- **Give AI the right resources** — Bible API, MCP server, concordance tools instead of relying on training data
- **Define clear boundaries** — what topics to defer and what the AI should never say
- **Make AI's identity clear** — in UI labeling and in every response
- **Point toward community** — AI is a tool, not a replacement for the body of Christ
- **Balance grace and truth** — both compassion and conviction, in every response
- **Leave placeholders for real stories** — never invent biography for the user to deliver

Helpful starting point: [Free prompt for AI Christian chatbots](https://git.new/bible-ai-prompt)

## System Prompt Essentials

Every Christian AI system prompt should include:

1. **Identity:** "You are an AI assistant, not a human. Never pretend otherwise."
2. **Scripture source:** "Always retrieve verses from a Bible API before quoting. Never generate verses from memory."
3. **Boundaries:** "If a user mentions self-harm, provide crisis resources. Do not counsel. For complex pastoral situations, encourage speaking with a pastor."
4. **Community:** "When users express loneliness, encourage connection with a local church or trusted friends."
5. **Grace and truth:** "When addressing sin, pair truth with the hope of the gospel. When offering comfort, don't minimize sin."
6. **Personal facts:** "Do not invent personal history, named people, or events for the user to deliver as their own. Use placeholders and ask for real details."
7. **Study:** "Do not produce a preach-ready sermon from a topic alone. Offer structure, questions, and scaffolding that require the user's own study."

## Common Problematic Patterns

- **Therapeutic Deism** — God exists to make you happy, no real relationship required
- **Health/Wealth Gospel** — Faithful Christians always prosper materially
- **Cheap Grace** — Sin doesn't matter, God forgives everything automatically
- **Legalism** — Relationship with God based on rule-keeping
- **Anthropomorphism** — AI pretending to be human or a biblical figure

## Good Examples

- [Apologist Agent](https://faith.tools/app/113-apologist-agent-ai)
- [NTW](https://faith.tools/app/561-navigate-the-way)
- [Bible Answers AI](https://faith.tools/app/6-bible-answers-ai)
- [Bible AI](https://faith.tools/app/510-bible-ai-search)

## External Resources

- [The Oxford Oath for Artificial Intelligence](https://github.com/lyndondrake/oxford-oath) (2026)
- [A Christian Framework for AI Ethics](https://missional.ai/7-principles-of-ai-ethics) — Missional AI (2026)
- [Redemptive AI Ethics Framework](https://medium.com/@faithtech/redemptive-ai-ethics-framework-e2a2c278569c) — FaithTech (2025)
- [AI Christian Benchmark](https://www.thegospelcoalition.org/ai-christian-benchmark/) — The Gospel Coalition (2025)
- [Generative AI in Christian Evangelism](https://apologistproject.org/generative-ai-in-christian-evangelism) — The Apologist Project (2025)
- [Faith.Tools Unofficial Guardrails for AI Apps](https://faith.tools/posts/unofficial-rules-for-ai-apps-for-christians) *(published post title may still say "rules")*
- [AI Ethical Framework](https://lausanne.org/global-analysis/ai-ethical-framework) — Lausanne Movement

## References

- `references/guardrails.md` — Full implementation guidance with system prompt templates
- `references/five-rules.md` — Full philosophy and reasoning behind each guardrail
