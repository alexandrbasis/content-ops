# Research Sources

Curated sources for content research. Includes topic mapping and pre-crafted Exa queries.

**Session target:** 3–5 digest entries per session. Rotate sources daily — don't hit the same source twice in a row.

---

## Source Priority Map

| Source | Topics | Frequency | Signal Quality |
|--------|--------|-----------|---------------|
| Hacker News top 30 | All topics | Daily | High — community curated |
| GitHub Trending | Dev tools, OSS | Daily | High — velocity signal |
| arXiv cs.AI / cs.LG | AI/ML research | Daily | Very high — primary source |
| Product Hunt | Dev tools, AI | Daily | Medium — launch noise |
| TLDR Tech | AI/ML, dev tools, startups | Daily | High — curated digest |
| The Batch | AI/ML | Weekly (Wed) | Very high — curated by Andrew Ng |
| Hacker Newsletter | All topics | Weekly (Fri) | High — HN best-of-week |

---

## Exa Queries by Source

Copy and run these in your `web_search_exa` or `web_search_advanced_exa` tool.

### Hacker News

**Top 30 — daily:**
```
Query: "site:news.ycombinator.com" top stories today AI developer tools startups
Tool: web_search_advanced_exa
Params: { domain: "news.ycombinator.com", type: "instant", numResults: 15 }
```

**Show HN — new products:**
```
Query: Show HN developer tool AI 2026
Tool: web_search_exa
Params: { type: "instant", numResults: 10, includeDomains: ["news.ycombinator.com"] }
```

### GitHub Trending

**Trending repos this week:**
```
Query: GitHub trending repositories AI developer tools this week
Tool: web_search_exa
Params: { type: "instant", numResults: 10, includeDomains: ["github.com"] }
```

**Specific categories:**
```
Query: GitHub trending Python LLM open source 2026
Tool: web_search_advanced_exa
Params: { domain: "github.com", numResults: 10, startPublishedDate: "YYYY-MM-DD" }
```
*(Set startPublishedDate to 7 days ago)*

### arXiv — AI Research

**New cs.AI papers:**
```
Query: arXiv cs.AI new paper 2026 language model reasoning
Tool: web_search_advanced_exa
Params: { domain: "arxiv.org", type: "auto", numResults: 10 }
```

**cs.LG papers:**
```
Query: arXiv cs.LG machine learning 2026 benchmark
Tool: web_search_advanced_exa
Params: { domain: "arxiv.org", numResults: 10, startPublishedDate: "YYYY-MM-DD" }
```

**Deep research on a specific paper:**
```
Tool: deep_search_exa
Query: [paper title] implications for developers practitioners
```

### Product Hunt

**Dev tools and AI launches:**
```
Query: Product Hunt top launches developer tools AI today
Tool: web_search_exa
Params: { type: "instant", numResults: 10, includeDomains: ["producthunt.com"] }
```

### TLDR Tech

**Latest issue:**
```
Query: TLDR Tech newsletter today AI developer startups
Tool: web_search_exa
Params: { type: "instant", numResults: 5, includeDomains: ["tldr.tech"] }
```

### The Batch (DeepLearning.AI)

**Latest issue (weekly — check Wednesdays):**
```
Query: The Batch DeepLearning.AI newsletter AI news this week
Tool: web_search_exa
Params: { type: "instant", numResults: 5, includeDomains: ["deeplearning.ai"] }
```

---

## X / Twitter Signal Sources

These require `web_search_advanced_exa` or the `browser-use` skill for authenticated access.

**Key accounts to monitor:**
- AI research: @karpathy, @ylecun, @emostaque (Stability AI)
- Builders/founders: @levelsio, @marc_louvion, @swyx
- Dev tool founders, indie hackers

**Query template:**
```
Query: [account handle] tweet thread 2026 AI developer
Tool: web_search_exa
Params: { type: "instant", includeDomains: ["twitter.com", "x.com"] }
```

---

## Trending Signal (X/Twitter)

For real-time X trending awareness:

```
Query: trending Twitter X AI developer tools today 2026
Tool: web_search_exa
Params: { type: "instant", numResults: 15 }
```

Or check what's breaking via:
```
Query: what's trending in tech AI today site:twitter.com OR site:x.com
Tool: web_search_advanced_exa
```

---

## Rotation Schedule (Suggested)

| Day | Priority Sources |
|-----|----------------|
| Mon | HN top 30 + GitHub Trending |
| Tue | arXiv cs.AI + TLDR Tech |
| Wed | Product Hunt + The Batch (new issue) |
| Thu | HN top 30 + arXiv cs.LG |
| Fri | GitHub Trending + Hacker Newsletter (new issue) |
| Sat/Sun | Light — X accounts + any stories that broke over week |

---

## Adding New Sources

When you find a reliable high-signal source:
1. Add it to the table at the top with topics, frequency, and signal quality
2. Write a query block in the appropriate section
3. Test it for 2 weeks before treating as a primary source

*Last Updated: 2026-04-09 | [ABA-4](/ABA/issues/ABA-4)*
