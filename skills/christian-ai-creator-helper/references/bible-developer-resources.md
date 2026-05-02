# Bible Developer Resources

A curated directory of APIs, SDKs, MCP servers, concordance tools, commentary resources, and datasets for building Bible-aware applications.

## Scripture Linking — route.bible

When your app links out to Scripture (share links, QR codes, verse cards, sermon notes, "Open in Bible app" buttons), use [**route.bible**](https://route.bible/) instead of provider-specific URLs.

`route.bible` is a canonical URL and routing layer for Bible passages. One stable URL that works across any installed Bible app, browser, or device.

**Why it matters:**
- **One URL format** instead of hard-coding YouVersion/Logos/BibleGateway/etc. links
- **Portable** — copied links and QR codes work regardless of which Bible app the recipient has
- **Licensing-aware** — routes restricted translations (ESV, NIV) to licensed destinations instead of hosting them
- **Fallback-first** — if no preferred app is installed, falls back to a web reader

**URL format:**
```
https://route.bible/{passage}?v={translation}&src={your_app}
```

| Example | URL |
|---|---|
| John 3:16 | `https://route.bible/jhn.3.16` |
| Range | `https://route.bible/jhn.3.16-jhn.3.18` |
| With translation | `https://route.bible/jhn.3.16?v=ESV` |
| With source tag | `https://route.bible/rom.8.28?src=my_app` |

**Integration options:**

| Method | When to use |
|---|---|
| **Canonical URLs directly** | Your app already knows the passage. Just emit `https://route.bible/jhn.3.16` |
| [**grab-bcv**](https://www.npmjs.com/package/grab-bcv) (npm) | Your app needs to parse user input into passage references locally |
| [**@route-bible/client**](https://www.npmjs.com/package/@route-bible/client) (npm) | Your app needs hosted parsing, resolution, QR generation, or adapter metadata |
| [**badge.js**](https://route.bible/badge.js) | CMS/article pages wanting copy-paste integration with minimal code |
| [**Share target**](https://route.bible/share-target) | Your page has article metadata but not a clean parsed passage |

> **Rule of thumb:** Use `route.bible` for outbound/share/export links. Keep your own internal reader route for the primary in-app reading experience.

Full integration guide: [route.bible/skill.md](https://route.bible/skill.md)

## Bible Licensing — Know Before You Ship

Not all Bible translations are free to use. Many are copyrighted and require publisher permission — even via API. **Before you serve any translation to users, confirm you have the rights to do so.**

### Public domain (no permission needed)

| Translation | Details |
|---|---|
| **Berean Standard Bible (BSB)** | [Dedicated to public domain](https://berean.bible/terms.htm) (CC0) as of April 30, 2023. All uses freely permitted, including commercial. |
| **King James Version (KJV)** | Public domain in the US and most countries. **Exception:** In the UK, the KJV is under Crown copyright (Royal Prerogative). ([source](https://commonplacefacts.com/2026/01/18/is-the-king-james-bible-copyrighted/)) |
| **World English Bible (WEB)** | Public domain. ("World English Bible" is a trademark of eBible.org, but the text itself is unrestricted.) |
| **American Standard Version (ASV, 1901)** | Public domain worldwide. |
| **Strong's Concordance data** | Published 1890, public domain. |

### Free for non-commercial (permission required for commercial use)

| Translation | Details |
|---|---|
| **NET Bible** | Copyrighted by Biblical Studies Press, L.L.C. Free for non-commercial use with attribution. **Commercial use requires permission from [HarperCollins Christian Publishing](https://www.harpercollinschristian.com/sales-and-rights/licensing/).** ([full terms](https://netbible.com/copyright/)) |

### Requires publisher permission (for any use beyond limited quoting)

| Translation | Publisher | Permission |
|---|---|---|
| **English Standard Version (ESV)** | Crossway | Free to quote up to 500 verses non-commercial with attribution. Beyond that or commercial: [request permission](https://www.crossway.org/permissions/) |
| **New International Version (NIV)** | Biblica | Free to quote up to 500 verses non-commercial with attribution. Commercial or full-text: [written permission](https://www.biblica.com/permissions/) |
| **New Living Translation (NLT)** | Tyndale House Foundation | [Permission required](http://api.nlt.to/) for commercial use |
| **New American Standard Bible (NASB)** | The Lockman Foundation | [Permission to quote form](https://www.lockman.org/permission-to-quote-request-form/) required beyond limited quoting |
| **Christian Standard Bible (CSB)** | Holman Bible Publishers (B&H) | [Permission required](https://csbible.com/permissions/) |
| **The Message (MSG)** | Eugene H. Peterson / NavPress | Written permission required. ([terms](https://biblia.com/books/message/article/COPY)) |

> **Tip:** Many APIs handle licensing on their end (e.g., API.Bible, YouVersion). But if you're self-hosting Bible text or using it commercially, you must secure your own license. When in doubt, stick with public domain translations or use an API that handles licensing for you.

---

## Bible APIs

| API | Cost | Details |
|---|---|---|
| [**Free Use Bible API**](https://bible.helloao.org/docs/) | Free | 1,000+ translations. No API keys, no limits, JSON. Also has commentary endpoints. By AO Lab. |
| [**API.Bible**](https://scripture.api.bible/) | Free (non-commercial) | 2,500 versions, 1,600 languages. By American Bible Society. |
| [**YouVersion Platform**](https://developers.youversion.com/api) | Free (non-commercial) | Full Bible API — passages, books, chapters, verses. Requires app key. |
| [**bible-api.com**](https://bible-api.com/) | Free | Simple JSON API for public domain Bibles (WEB, KJV, etc). Rate-limited. |
| [**ESV API**](https://api.esv.org/) | Free (non-commercial) | English Standard Version. HTML/text/XML. |
| [**NET Bible API**](https://labs.bible.org/api_web_service) | Free (non-commercial) | NET Bible text. HTML/JSON/XML. |
| [**NLT API**](http://api.nlt.to/) | Free (non-commercial) | New Living Translation. By Tyndale. |
| [**Bible Brain API**](https://www.faithcomesbyhearing.com/audio-bible-resources/bible-brain) | Free | 1,700+ languages with text, audio, and video. By Faith Comes By Hearing. |
| [**Aquifer Bible**](https://www.aquifer.bible/) | Free (API key required) | Open-source, multilingual, multimodal Bible resources for global translation. |
| [**Christian Context API**](https://www.getcontext.xyz/developers.php) | Free | 3,752 verses + 1,790 sermon videos + 206 commentaries, all cross-referenced. |
| [**Biblia.com API**](http://bibliaapi.com/docs/) | Free | Faithlife/Logos backend. Bible text + commentaries + search. |

## Bible SDKs

| SDK | Language | Details |
|---|---|---|
| [**BibleSDK**](https://biblesdk.com/) | TypeScript / REST | NET Bible text + Strong's concordance + AI-powered semantic search. [Docs](https://biblesdk.com/docs) / [SDK guide](https://biblesdk.com/docs/sdk) |
| [**Bible SuperSearch API**](https://api.biblesupersearch.com/) | REST | Free, 1,000 hits/day. Many languages available for non-commercial use. |
| [**IQ Bible API**](https://iqbible.com/) | REST | 40+ endpoints — original Hebrew/Greek, audio narrations, study tools. |
| [**SWORD Engine**](http://www.crosswire.org/sword/index.jsp) | C++ (bindings for many) | CrossWire Bible Society's open source Bible software engine. |

## Bible MCP Servers

MCP (Model Context Protocol) servers let AI assistants like Claude and Cursor access Scripture directly without hallucinating.

| Server | Language | Details |
|---|---|---|
| [**Bible MCP**](https://bible-mcp.faith.tools/) | TypeScript (Deno) | Uses the Free Use Bible API. Hosted endpoint: `https://bible-mcp.faith.tools/mcp`. 97/100 quality on Smithery, 99.7% uptime. [Source](https://www.val.town/x/cameronpak/bible-mcp). [On faith.tools](https://faith.tools/app/6401-bible-mcp). |
| [**AdbC99/ai-bible**](https://github.com/AdbC99/ai-bible) | JavaScript | MCP server + OpenAI completions API wrapper. Reliable, reproducible verse lookup. Also at [ai-bible.com](http://ai-bible.com/). |
| [**geosp/mcp-bible**](https://github.com/geosp/mcp-bible) | Python | Via BibleGateway. ESV/NIV/KJV/NASB/NKJV/NLT/AMP/MSG. Supports stdio, HTTP MCP, and REST modes. |

## Concordance & Word Study Tools

| Tool | Format | Details |
|---|---|---|
| [**BibleSDK**](https://biblesdk.com/) | REST API | Strong's numbers, original language definitions, transliterations. Add `?concordance=true` to any verse endpoint. |
| [**STEPBible Data**](https://github.com/tyndale/STEPBible-Data) | TSV/CSV (CC BY 4.0) | Extended Strongs for Hebrew/Greek, morphological tags, lexicons, proper names, cross-references. |
| [**Blue Letter Bible**](https://www.blueletterbible.org/) | Web + [ScriptTagger](https://www.blueletterbible.org/webtools/getPlugin.cfm) | Free online Strong's concordance, lexicons, word tools. ScriptTagger auto-links Bible refs on any website. |
| [**OpenScriptures Hebrew Bible**](https://hb.openscriptures.org/) | OSIS XML | Hebrew Lexicon, morphology codes. Open source. |
| [**morphgnt**](https://github.com/morphgnt) | Python + REST API | Linguistic databases + tools for the Greek NT. Strong's Greek Dictionary in XML. |

## Commentary & Extrabiblical Resources

| Resource | Type | Details |
|---|---|---|
| [**Free Use Bible API**](https://bible.helloao.org/docs/) | API | Commentary endpoints alongside translations. `GET /api/c/{commentary}/books.json` |
| [**Christian Context API**](https://www.getcontext.xyz/developers.php) | API | Verse-matched commentary + sermons from curated sources. Query by theme, book, verse, or pastor. |
| [**Biblia.com API**](http://bibliaapi.com/docs/) | API | Faithlife/Logos backend. Bible text + commentaries + search. |
| [**BibleTalk.tv Data API**](https://bibletalk.tv/data-api) | API | Free Bible study materials in JSON. Add `.json` to URIs. |

## Directories & Master Lists

| Directory | Details |
|---|---|
| [**get.bible Bible Data Sets**](https://get.bible/bible-data-sets/) | The most comprehensive directory of Bible APIs, datasets, XML formats, and public domain texts. |
| [**awesome-bible-developer-resources**](https://github.com/biblenerd/awesome-bible-developer-resources) | Curated list of Bible dev tools and resources on GitHub. |
| [**faith.tools For Developers**](https://faith.tools/for-developers) | Christian developer resources directory. |

## Bible Text Downloads (for self-hosting / RAG)

| Source | Format | Details |
|---|---|---|
| [**open.bible**](https://open.bible/) | USX, USFM, Word, audio | Biblica's CC-licensed Bibles in 700+ languages. |
| [**fetch.bible**](https://fetch.bible/) | USX 3+, USFM, HTML, text | Free access to 1,100+ Bible translations with API. |
| [**berean.bible/downloads**](https://berean.bible/downloads.htm) | XLSX, PDF, Word, text | Berean Study Bible (public domain). |
| [**ebible.org**](http://ebible.org/find) | HTML, ePub, PDF, SQL, USFM | Bibles in many languages and formats. |
| [**OpenBible.com**](https://openbible.com/) | XLSX, PDF, Word, ePub, text | Open source Bibles for download and development. |
| [**github.com/seven1m/open-bibles**](https://github.com/seven1m/open-bibles) | XML | Public domain and freely licensed Bibles. |
| [**Bible Versions DB**](https://github.com/scrollmapper/bible_databases) | MySQL, SQLite, XML, CSV, JSON | ASV, BBE, DARBY, KJV, WBT, WEB, YLT + cross-references. |

## Greek & Hebrew Original Language Data

| Source | Details |
|---|---|
| [**STEPBible Data**](https://github.com/tyndale/STEPBible-Data) | CC BY 4.0. Tagged Hebrew OT, amalgamated Greek NT, extended Strongs lexicons, proper names. |
| [**morphgnt**](https://github.com/morphgnt) | Linguistic databases + Python tools for Greek NT. REST API. |
| [**OpenScriptures Hebrew Bible**](https://hb.openscriptures.org/) | OSIS XML, Hebrew Lexicon, morphology codes. |
| [**biblicalhumanities.org**](http://biblicalhumanities.org/dashboard/) | Nestle 1904 GNT, Codex Sinaiticus, Septuagint, Liddell-Scott-Jones lexica, Mounce Lexicon. |
| [**TextCritical.net**](https://textcritical.net/) | Free access to ancient Greek works in the original language. Open source. |

---

*Scripture linking powered by [route.bible](https://route.bible/) — a canonical URL and routing layer for Bible passages. One stable URL that works across any Bible app, browser, or device. By [selah.tools](https://selah.tools/).*
