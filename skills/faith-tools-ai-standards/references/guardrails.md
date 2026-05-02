# AI Guardrails for Christian Apps

This guide is for **builders** creating Christian AI applications. These guardrails help ensure your app meets the [5 unofficial rules](https://faith.tools/posts/unofficial-rules-for-ai-apps-for-christians) before you ever submit to faith.tools.

## Why Guardrails Matter

AI is a computation — a deterministic function underneath the probabilistic output. Because of that, you *can* put proper boundaries in place. Guardrails aren't about restricting the Holy Spirit (the Spirit doesn't need your AI). They're about stewarding technology so it doesn't lead people astray.

## 1. Give AI the Right Resources

Don't rely on what the LLM "remembers" from training data about the Bible. Give it the actual text in real time.

**The principle:** *"Don't rely on LLMs to quote things with 100% accuracy b/c you don't know what they were trained on exactly. Just give them the information they need via RAG in real-time."* — Jake Carlson, Apologist

### Bible APIs

| API | Details |
|---|---|
| [**Free Use Bible API**](https://bible.helloao.org/docs/) | 1,000+ translations. Free, no API keys, no limits, JSON. Also has commentary endpoints. By AO Lab. |
| [**API.Bible**](https://scripture.api.bible/) | 2,500 versions, 1,600 languages. By American Bible Society. Free for non-commercial use. |
| [**YouVersion Platform**](https://developers.youversion.com/api) | Full Bible API — passages, books, chapters, verses. Requires app key. |
| [**bible-api.com**](https://bible-api.com/) | Simple JSON API for public domain Bibles (WEB, KJV, etc). Free, rate-limited. |
| [**ESV API**](https://api.esv.org/) | English Standard Version. Free for non-commercial. HTML/text/XML. |
| [**NET Bible API**](https://labs.bible.org/api_web_service) | Free for non-commercial. HTML/JSON/XML. |
| [**NLT API**](http://api.nlt.to/) | New Living Translation. Free for non-commercial (Tyndale). |
| [**Bible Brain API**](https://www.faithcomesbyhearing.com/audio-bible-resources/bible-brain) | 1,700+ languages with text, audio, and video. Free. By Faith Comes By Hearing. |
| [**BibleSDK**](https://biblesdk.com/) | NET Bible text + Strong's concordance + AI-powered semantic search. REST API + TypeScript SDK. |
| [**Aquifer Bible**](https://www.aquifer.bible/) | Open-source, multilingual, multimodal Bible resources for global translation. Requires API key. |
| [**Christian Context API**](https://www.getcontext.xyz/developers.php) | 3,752 verses + 1,790 sermon videos + 206 commentaries, all cross-referenced. Free. |

### Bible MCP Servers

MCP (Model Context Protocol) servers let AI assistants like Claude and Cursor access Scripture directly without hallucinating.

| Server | Details |
|---|---|
| [**Bible MCP**](https://bible-mcp.faith.tools/) | Open-source MCP server using the Free Use Bible API. Hosted endpoint: `https://bible-mcp.faith.tools/mcp`. 97/100 quality on Smithery, 99.7% uptime. [Source on Val.Town](https://www.val.town/x/cameronpak/bible-mcp). |
| [**geosp/mcp-bible**](https://github.com/geosp/mcp-bible) | Python MCP server via BibleGateway. ESV/NIV/KJV/NASB/NKJV/NLT/AMP/MSG. Supports stdio, HTTP MCP, and REST modes. |
| [**AdbC99/ai-bible**](https://github.com/AdbC99/ai-bible) | JavaScript MCP server + OpenAI completions API wrapper. Reliable, reproducible verse lookup. Also at [ai-bible.com](http://ai-bible.com/). |

### Concordance & Word Study Tools

| Tool | Details |
|---|---|
| [**BibleSDK**](https://biblesdk.com/) | Strong's numbers, original language definitions, transliterations via REST API. |
| [**STEPBible Data**](https://github.com/tyndale/STEPBible-Data) | CC BY 4.0. Extended Strongs for Hebrew/Greek, morphological tags, lexicons, proper names, cross-references. |
| [**Blue Letter Bible**](https://www.blueletterbible.org/) | Free online Strong's concordance, lexicons, word tools. Has [ScriptTagger web tool](https://www.blueletterbible.org/webtools/getPlugin.cfm) for auto-linking Bible refs. |
| [**OpenScriptures Hebrew Bible**](https://hb.openscriptures.org/) | OSIS XML, Hebrew Lexicon, morphology codes. Open source. |
| [**morphgnt**](https://github.com/morphgnt) | Linguistic databases + Python tools for the Greek NT. REST API, Strong's Greek Dictionary in XML. |

### Commentary Access

| Resource | Details |
|---|---|
| [**Free Use Bible API**](https://bible.helloao.org/docs/) | Includes commentary endpoints alongside translations. |
| [**Christian Context API**](https://www.getcontext.xyz/developers.php) | Verse-matched commentary from curated sources. |
| [**Biblia.com API**](http://bibliaapi.com/docs/) | Faithlife/Logos backend. Bible text + commentaries + search. Free. |

### Directories

- [**get.bible Bible Data Sets**](https://get.bible/bible-data-sets/) — The most comprehensive directory of Bible APIs, datasets, XML formats, and public domain texts
- [**awesome-bible-developer-resources**](https://github.com/biblenerd/awesome-bible-developer-resources) — Curated list of Bible dev tools and resources
- [**faith.tools For Developers**](https://faith.tools/for-developers) — Christian developer resources directory

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

### Getting Started
- [Free prompt for AI Christian chatbots](https://git.new/bible-ai-prompt) — open-source starting point
- [Bible MCP](https://bible-mcp.faith.tools/) — drop-in MCP server so your AI quotes real Scripture, not hallucinations
- [Free Use Bible API](https://bible.helloao.org/docs/) — the go-to RAG source for real-time Scripture access (free, no keys)

### Word Study & Original Languages
- [BibleSDK](https://biblesdk.com/) — Strong's concordance + semantic search in one API (TypeScript SDK available)
- [STEPBible Data](https://github.com/tyndale/STEPBible-Data) — CC BY 4.0 Greek/Hebrew word study data, lexicons, morphology
- [Blue Letter Bible](https://www.blueletterbible.org/) — free online Strong's concordance and lexicons

### Directories & Comprehensive Lists
- [get.bible Bible Data Sets](https://get.bible/bible-data-sets/) — master directory of all Bible APIs, datasets, and formats
- [awesome-bible-developer-resources](https://github.com/biblenerd/awesome-bible-developer-resources) — curated list of Bible dev tools
- [faith.tools For Developers](https://faith.tools/for-developers) — Christian developer resources

### Global & Multilingual
- [Aquifer Bible](https://www.aquifer.bible/) — open-source, multilingual Bible resources for global translation
- [Bible Brain API](https://www.faithcomesbyhearing.com/audio-bible-resources/bible-brain) — 1,700+ languages, text/audio/video

### Ethics & Design
- [Laws of UX](https://lawsofux.com/) — design excellence honors God
- [FaithTech Playbook](https://faithtech.com/the-faithtech-playbook/) — building redemptive technology
- [Redemptive AI Ethics Framework](https://medium.com/@faithtech/redemptive-ai-ethics-framework-e2a2c278569c) — FaithTech (2025)
