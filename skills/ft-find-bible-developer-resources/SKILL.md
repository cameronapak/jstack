---
name: ft-find-bible-developer-resources
description: Find Bible APIs, SDKs, MCP servers, concordance tools, commentary resources, datasets, and licensing info for building Bible-aware applications. Covers route.bible for portable Scripture linking, Free Use Bible API, API.Bible, YouVersion, Bible Brain, BibleSDK, Bible MCP, STEPBible Data, and more. Use when looking for a Bible API, adding Scripture access to an app, finding Bible MCP servers, checking translation licensing, or integrating route.bible for outbound Scripture links.
metadata:
  fruit: kindness
---

# Find Bible Developer Resources

Curated directory of APIs, SDKs, MCP servers, concordance tools, commentary, and datasets for building Bible-aware applications.

## Quick Start

For the full directory with details, see `references/bible-developer-resources.md`.

### Scripture Linking — route.bible

Use [route.bible](https://route.bible/) for outbound/share/export Scripture links. One stable URL that works across any Bible app.

```
https://route.bible/{passage}?v={translation}&src={your_app}
```

| Example | URL |
|---|---|
| John 3:16 | `https://route.bible/jhn.3.16` |
| With translation | `https://route.bible/jhn.3.16?v=ESV` |

### Key Bible APIs

| API | Cost | Highlights |
|---|---|---|
| [Free Use Bible API](https://bible.helloao.org/docs/) | Free | 1,000+ translations, no keys, JSON |
| [API.Bible](https://scripture.api.bible/) | Free (non-commercial) | 2,500 versions, 1,600 languages |
| [YouVersion Platform](https://developers.youversion.com/api) | Free (non-commercial) | Full Bible API, requires app key |
| [Bible Brain API](https://www.faithcomesbyhearing.com/audio-bible-resources/bible-brain) | Free | 1,700+ languages, text/audio/video |

### Bible MCP Servers

| Server | Details |
|---|---|
| [Bible MCP](https://bible-mcp.faith.tools/) | Hosted endpoint, 97/100 quality on Smithery |
| [Doxa MCP](https://doxa.app/mcp) | Hosted endpoint with three tools: encourage (Doxa-voice reply anchored in Scripture), scripture (BSB lookup), way_movement (Doxa Way framework). Free per-individual quota, BYOL Anthropic for unlimited |
| [AdbC99/ai-bible](https://github.com/AdbC99/ai-bible) | MCP server + OpenAI wrapper |
| [geosp/mcp-bible](https://github.com/geosp/mcp-bible) | Python, via BibleGateway |

### Licensing Quick Reference

**Public domain (safe to use):** BSB, KJV (US), WEB, ASV, Strong's data
**Free non-commercial:** NET Bible
**Requires permission:** ESV, NIV, NLT, NASB, CSB, MSG

Many APIs handle licensing on their end. If self-hosting or commercial, secure your own license. When in doubt, stick with public domain or use an API that handles licensing.

## References

- `references/bible-developer-resources.md` — Full directory with Bible APIs, SDKs, MCP servers, concordance tools, commentary resources, datasets, text downloads, and Greek/Hebrew original language data
