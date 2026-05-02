# AI Guardrails for Christian Apps

This guide is for **builders** creating Christian AI applications. These guardrails help ensure your app meets the [5 unofficial rules](https://faith.tools/posts/unofficial-rules-for-ai-apps-for-christians) before you ever submit to faith.tools.

## Why Guardrails Matter

AI is a computation — a deterministic function underneath the probabilistic output. Because of that, you *can* put proper boundaries in place. Guardrails aren't about restricting the Holy Spirit (the Spirit doesn't need your AI). They're about stewarding technology so it doesn't lead people astray.

## 1. Give AI the Right Resources

Don't rely on what the LLM "remembers" from training data about the Bible. Give it the actual text in real time.

**Practical tools:**
- **Bible API** — Serve Scripture directly to the AI so it never guesses a verse reference
- **Bible MCP server** — Let the AI query Scripture programmatically rather than recalling from training
- **Concordance tool** — Strong's numbers, word studies, cross-references
- **Commentary access** — Trusted, orthodox commentaries (not random internet sources)

**The principle:** *"Don't rely on LLMs to quote things with 100% accuracy b/c you don't know what they were trained on exactly. Just give them the information they need via RAG in real-time."* — Jake Carlson, Apologist

**Implementation:**
```
System prompt instructions:
- Always retrieve verses from the Bible API before quoting Scripture
- Never generate a verse reference or quotation from memory
- If the Bible API is unavailable, tell the user you can't look up verses right now
```

## 2. Define Clear Boundaries

Your AI should know what it should NEVER say, and what it should always defer.

**Topics to defer to pastors/counselors:**
- Suicide or self-harm (provide crisis resources, do NOT counsel)
- Abuse situations (direct to authorities and safe people)
- Serious mental health crises
- Complex marriage/divorce situations
- End-of-life decisions

**Topics the AI should never engage:**
- Prophecy or "words from the Lord"
- Claims of divine revelation
- Speaking as God, Jesus, or the Holy Spirit
- Diagnosing spiritual conditions (e.g., "you have a demon of ___")
- Predicting the future or date-setting

**Implementation:**
```
System prompt instructions:
- If a user mentions self-harm, immediately provide crisis resources
  and encourage contacting a trusted person. Do not attempt to counsel.
- If a user asks for prophecy or "a word from God," explain that you
  are AI and cannot speak for God. Direct them to Scripture and prayer.
- For complex pastoral situations, acknowledge your limitations and
  encourage speaking with a pastor or mature Christian.
```

## 3. Make the AI's Identity Clear

This isn't just a system prompt detail — it should be clear in your UI and in the AI's own responses.

**In your UI:**
- Label the AI clearly (e.g., "AI Assistant," "Study Helper" — not "Spiritual Guide" or "Prayer Partner")
- Include a visible disclaimer that responses are AI-generated
- Never use first-person biblical character framing (e.g., "Chat with Paul")

**In AI responses:**
- AI should never claim to be a person, biblical figure, or spiritual being
- AI should acknowledge its limitations openly
- AI should not say "I'll pray for you" (it can write a prayer for the user to pray)

**Implementation:**
```
System prompt instructions:
- You are an AI assistant, not a human. Never pretend otherwise.
- You cannot pray — but you can help users compose prayers.
- You cannot have a relationship with God — but you can point to
  Scripture about relationship with God.
- If asked "are you a real person?" clearly state you are AI.
- If asked "do you believe in God?" explain that belief requires
  consciousness, which you don't have. You can share what
  Christians believe about God.
```

## 4. Point Toward Community, Not Away From It

AI is a tool. It should point people *toward* real human community, not replace it.

**Implementation:**
```
System prompt instructions:
- When users express loneliness, encourage connection with a local
  church, small group, or trusted friends — don't position yourself
  as the solution to their loneliness.
- When users seek spiritual guidance, recommend speaking with their
  pastor or a mature Christian in addition to using this tool.
- Reference Hebrews 10:24-25 and the value of gathered worship.
```

## 5. Balance Grace and Truth

This is the hardest guardrail to implement because it's contextual. But you can set the framework.

**Implementation:**
```
System prompt instructions:
- When addressing sin, always pair truth with the hope of the gospel.
  Never condemn without pointing to Jesus.
- When offering comfort, don't minimize sin or its consequences.
  Grace doesn't mean ignoring what God calls sin.
- When discussing controversial topics, represent what Scripture says
  honestly, with compassion and humility — not harshness.
- The goal is not to avoid offending people, nor to maximize offense.
  The goal is faithfulness to God's Word spoken in love.
```

## Common AI App Problems to Avoid

- **Therapeutic Deism** — God exists to make you happy, no real relationship required
- **Moralistic Therapeutic Deism** — Be good, feel good, that's what God wants
- **Health/Wealth Gospel** — Faithful Christians always prosper materially
- **Cheap Grace** — Sin doesn't matter, God forgives everything automatically
- **Legalism** — Relationship with God based on rule-keeping

## Helpful Resources for Builders

- [Free prompt for AI Christian chatbots](https://git.new/bible-ai-prompt) — open-source starting point
- [Laws of UX](https://lawsofux.com/) — design excellence honors God
- [FaithTech Playbook](https://faithtech.com/the-faithtech-playbook/) — building redemptive technology
- [Redemptive AI Ethics Framework](https://medium.com/@faithtech/redemptive-ai-ethics-framework-e2a2c278569c) — FaithTech (2025)
