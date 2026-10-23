---
name: deep-social-intel
description: >-
  High-quality, exhaustive intelligence gathering across Reddit, X (Twitter), and the
  broader web for strategic planning, architectural design, competitor analysis,
  and deep user sentiment. Uses Exa AI, Apify Actors (tweet & reddit scrapers),
  and Firecrawl MCP servers for deep, high-signal results. Activate when the user
  asks for deep research, comprehensive planning, full Reddit comment trees, complete
  tweet threads, competitor audits, or thorough technical investigations.
---

# Deep Social & Web Intelligence (Setup 1: High-Quality Planning)

This skill provides an exhaustive, high-signal intelligence pipeline across **Reddit**, **X (Twitter)**, and the **entire web**. It is designed for deep architecture planning, technical problem validation, and sentiment analysis.

---

## 🛠 Available Engines & Routing

When executing deep research, choose the right MCP tool based on the data depth required:

| Target Platform | Preferred Engine | Tool Call / Actor | When to Use |
| :--- | :--- | :--- | :--- |
| **Reddit (Semantic / Themes)** | Exa AI | `call_mcp_tool(ServerName="exa", ToolName="web_search_exa", ...)` | Discover relevant Reddit threads across the site, extract clean discussion summaries, and filter by `includeDomains: ["reddit.com"]`. |
| **Reddit (Deep Comment Trees)** | Apify | `call_mcp_tool(ServerName="apify", ToolName="coding-doctor-omar/reddit-scraper-pro", ...)` or `trudax/reddit-scraper-lite` | Extract entire comment trees, top upvoted posts, karma scores, 30+ metadata fields, and user quotes from subreddits, keywords, or URLs. |
| **X / Twitter (Semantic Tweets)** | Exa AI | `call_mcp_tool(ServerName="exa", ToolName="web_search_exa", ...)` | Discover public tweets, developer thoughts, and industry announcements filtering by `includeDomains: ["x.com", "twitter.com"]`. |
| **X / Twitter (Full Threads & Metrics)** | Apify | `call_mcp_tool(ServerName="apify", ToolName="apidojo/tweet-scraper", ...)` | Extract complete tweet threads, author profiles, replies, timestamps, retweets, and likes without needing an official X developer subscription. |
| **Complete Websites & Docs** | Firecrawl | `call_mcp_tool(ServerName="firecrawl", ToolName="firecrawl_crawl", ...)` or `firecrawl_scrape` | Deep crawl multi-page technical documentation, whitepapers, or articles, bypassing anti-bot shields and converting pages to clean Markdown. |

> [!IMPORTANT]
> **API Key Fallback**: If Exa, Apify, or Firecrawl fail due to missing/expired API keys or return 401/403/timeout, **do not stall or retry**. Immediately fall back to native `search_web` (using `site:reddit.com` or `site:x.com`) and `read_url_content` (via `quick-web-scout`).

---

## 📋 Research Workflow

Follow this 4-step workflow for comprehensive planning:

### Step 1: Define Research Matrix
Clarify the key intelligence questions:
1. **Core Problem**: What technical hurdle or market question are we solving?
2. **Subreddits to Target**: (e.g. `r/embedded`, `r/hardware`, `r/MachineLearning`, `r/LocalLLaMA`).
3. **Key Search Operators**: Specific model numbers, error codes, chips, or architectural concepts.

### Step 2: Query Execution
- **Exa Search Query Example**:
  - Filter `includeDomains`: `["reddit.com"]` or `["x.com"]`.
  - Neural prompt: *"discussions comparing ESP32-S3 and FPGA latency for voice activation"*.
- **Apify Actor Execution**:
  - Run `apidojo/tweet-scraper` with query string and limit (e.g., 20-50 tweets).
  - Run `trudax/reddit-scraper-lite` targeting specific subreddits or search terms.
- **Firecrawl Web Extraction**:
  - Crawl full documentation or technical whitepaper domains.

### Step 3: Synthesis & Verification
- Filter out noise, sponsored promotions, and low-karma outliers.
- Group findings into:
  1. **Consensus & Best Practices**: What the majority of engineers/practitioners recommend.
  2. **Known Failure Modes / Gotchas**: Subtle bugs, hardware limits, memory leaks, or latency spikes reported in the field.
  3. **Real-World Metrics**: Reported benchmarks, timing figures, and power draw numbers.

### Step 4: Executive Planning Deliverable
Format findings in an actionable markdown artifact or response:
- **Executive Summary** (Key takeaways)
- **Sentiment & Consensus Breakdown** (Reddit vs X perspectives)
- **Technical Gotchas & Constraints** (Direct quotes & source URLs)
- **Actionable Architectural Recommendations**
