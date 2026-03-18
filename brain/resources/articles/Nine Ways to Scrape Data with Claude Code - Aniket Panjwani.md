---
captured: 2026-03-14
source_url: https://x.com/aniketapanjwani/article/2029304239345017050
category: article
author: Aniket Panjwani
source: x.com
type: x-article
---

## Summary

Aniket Panjwani details nine different methods for scraping data with Claude Code, ranging from simple "just ask" approaches to specialized tools like ScrapeCreators, Apify, Firecrawl, yt-dlp, Reddit JSON endpoints, and Agent Browser. Each method suits different data sources and complexity levels.

## Key Thesis/Insights

- **Start simple:** For many sites, just asking Claude Code to scrape and output to CSV/SQLite works
- **Give the right nudges:** Adding terms like "look for endpoints" improves results significantly
- **Social media is hard:** Instagram, TikTok, etc. require specialized tools like ScrapeCreators due to anti-bot measures
- **Firecrawl vs DIY:** Firecrawl handles edge cases better but costs money; open-source alternatives (Turndown, MarkItDown) work for budget-conscious users
- **YouTube is under-exploited:** yt-dlp for subtitles + Claude Code for summarization = massive value
- ** Authentication:** Two approaches — use existing browser cookies or Agent Browser with stored credentials

## The Nine Ways to Scrape Data

### Way 1: Just Ask Claude Code to Scrape the Site

**Best for:** Large set of standard websites with static content

**How it works:**
1. Tell Claude Code to scrape the site
2. Tell it what data you want
3. Ask it to write to CSV or SQLite file

**What Claude does:**
- Pokes around the site
- Writes a Python script
- Runs the script
- Maybe writes unit tests
- Writes data to your computer

**No complex setup needed** — just ask naturally.

### Way 2: Ask Claude Code to Find Endpoints

**Best for:** Dynamic sites loading data via API calls

**The problem:** Interesting data often isn't rendered statically — it's loaded dynamically via API.

**The nudge:** Add the word "endpoints" to your request:

```
"Look for an API which, for example, is showing this hotel pricing 
and booking data for competitor analysis."
```

**Why it works:** Claude sometimes reverse-engineers APIs itself, but explicitly asking for endpoints gives better results.

### Way 3: ScrapeCreators

**Best for:** Social media sites (Instagram, TikTok, etc.)

**The problem:** Social media endpoints are difficult to reverse-engineer due to:
- Anti-bot rules
- Changing selectors weekly
- Aggressive rate limiting

**The solution:** [ScrapeCreators](https://scrapecreators.com/) — API endpoints for virtually every social media platform.

**Recommended approach:**
- Create a Skill for ScrapeCreators endpoints
- One-time utility setup
- Agentic coding tool always has access

**Cost:** Paid service (pricing varies by usage)

### Way 4: Apify Actor

**Best for:** Difficult-to-scrape websites with existing solutions

**What it is:** Marketplace of rentable scrapers (called "actors") for specific sites.

**Recommended actors:**
- Google Maps scraper (great for social scientists and business competition analysis)
- Yelp scraper
- LinkedIn scraper

**Pricing model:**
- Some pay-by-usage
- Some rent-by-month
- Free trial available
- Requires Apify subscription after trial

### Way 5: Firecrawl → Markdown → Structured Extraction

**Best for:** Unstructured data from varying websites

**Use case example:** Scraping economics job market candidate pages where each university has different HTML structure.

**Pipeline:**
1. **Firecrawl** converts webpage → Markdown
2. **OpenAI API** parses Markdown with structured outputs
3. Get consistent structured data from varying sources

**Why paid Firecrawl over DIY:**
- Handles edge cases better
- Nicely designed service
- Worth it if ROI positive

**Budget alternative:** Use open-source (Way 6)

### Way 6: DIY HTML → Markdown → Structured Extraction

**Best for:** Budget-conscious users (academics, hobbyists)

**Open-source alternatives:**

| Tool | URL | Notes |
|------|-----|-------|
| **Turndown** | https://github.com/mixmark-io/turndown | JavaScript-based |
| **MarkItDown** | https://github.com/microsoft/markitdown | Microsoft's tool |

**Workflow:**
1. Convert HTML → Markdown using one of these tools
2. Pass Markdown to OpenAI API for structured extraction
3. Or have Claude Code/Codex do extraction directly (for smaller-scale projects)

**Scale consideration:** For thousands/tens of thousands of documents, external API calls are more practical than having Claude extract everything.

### Way 7: yt-dlp

**Best for:** YouTube video data extraction

**What it does:**
- Scrape any YouTube video
- Extract metadata
- Download subtitles

**Tool:** [yt-dlp on GitHub](https://github.com/yt-dlp/yt-dlp)

**Power user workflow:**
1. Download subtitles with yt-dlp
2. Have Claude Code/Codex create personalized summary
3. Apply video content to your specific context

**Example use case:** Reverse engineer successful AI YouTubers' videos to understand what content performs well.

**Author's note:** "I basically never watch videos anymore. I'll just download the subtitles and then have Claude Code create a personalized summary."

**Why it's under-exploited:** Massive amount of useful data in YouTube videos that most people don't tap into.

### Way 8: Reddit JSON Endpoint

**Best for:** Reddit monitoring and analysis

**The trick:** Add `.json` to any Reddit URL

**Example:**
- Regular URL: `https://old.reddit.com/r/claudecode/`
- JSON endpoint: `https://old.reddit.com/r/claudecode.json`

**What you get:** Entire subreddit content as structured JSON document.

**Power user setup:**
- Create Skills that hit JSON endpoints
- Keep pulse on multiple subreddits automatically
- Structured data ready for analysis

### Way 9: Agent Browser + Credentials

**Best for:** Sites behind authentication (Facebook groups, private communities)

**Two approaches:**

**Option A: Browser Cookies**
1. Do authentication exchange manually
2. Get cookie stored on computer
3. Claude Code uses cookie to authenticate
4. Scrape authenticated views

**Option B: Agent Browser (Vercel)**
- Tool: [agent-browser.dev](https://agent-browser.dev/)
- Browser automation CLI optimized for agents
- Store credentials securely (vault, env vars)
- Create skills for authenticated scraping

**Example workflow:**
1. Store Facebook credentials (vault or .env)
2. Create skill using Agent Browser
3. Log into Facebook group
4. Grab all posts
5. Write data to destination

**Scale:** Agent Browser preferred for small-scale authenticated scraping.

## Tool Comparison Matrix

| Method | Best For | Technical Level | Cost | Scale |
|--------|----------|-----------------|------|-------|
| Just Ask Claude | Static sites, simple scraping | Low | Free (Claude sub) | Small-medium |
| Find Endpoints | Dynamic/API-driven sites | Medium | Free | Medium |
| ScrapeCreators | Social media | Low-Medium | Paid | Medium-Large |
| Apify | Hard-to-scrape sites | Low | Paid | Large |
| Firecrawl | Unstructured to structured | Medium | Paid | Medium-Large |
| DIY Markdown | Budget-conscious | Medium | Free | Small-medium |
| yt-dlp | YouTube videos | Low | Free | Medium |
| Reddit JSON | Reddit monitoring | Low | Free | Medium |
| Agent Browser | Authenticated sites | Medium | Free (OSS) | Small |

## Stats Table

| Metric | Value |
|--------|-------|
| Replies | 7 |
| Reposts | 47 |
| Likes | 518 |
| Bookmarks | 1,589 |
| Views | 56,407 |
| Date | Mar 4, 2026 |

## Key Quotes

> "One of the easiest and most useful tasks to which to put Claude Code is scraping data. However, getting optimal data scraping results from Claude Code depend on giving it the right nudges and access to the correct tools."

> "A lot of interesting data is not rendered as a static page, but is being loaded dynamically via some API call."

> "Social media sites make their endpoints particularly difficult to reverse engineer. They have their own anti-bot rules, and they change the way selectors work each week."

> "I basically never watch videos anymore. I'll just download the subtitles and then have Claude Code or Codex create a personalized summary for me."

> "There is a ton of useful data in YouTube videos, and I really think that this tool in particular is highly under-exploited."

> "For small-scale scraping, I've been preferring to use Agent Browser."

## Full Article

<details>
<summary>Click to expand full article</summary>

[Full article includes detailed explanations of each method, video walkthrough links, and community information. See source URL for complete content.]

</details>

## Related Resources

- [ScrapeCreators](https://scrapecreators.com/)
- [Apify](https://apify.com/)
- [Firecrawl](https://firecrawl.dev/)
- [Turndown](https://github.com/mixmark-io/turndown)
- [MarkItDown (Microsoft)](https://github.com/microsoft/markitdown)
- [yt-dlp](https://github.com/yt-dlp/yt-dlp)
- [Agent Browser (Vercel)](https://agent-browser.dev/)
- [Video tutorial](https://youtu.be/4jQJdCfjPcw)
- [The AI MBA Community](https://www.skool.com/the-ai-mba)
