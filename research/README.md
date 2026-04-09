# Research Pipeline

Daily content research digest for ContentCreator. Solves the blank-page problem by providing structured inputs before each content session.

## How It Works

1. Each morning, search 3–5 stories using the Exa queries in [`sources.md`](sources.md)
2. Format each as a digest entry using [`digest-template.md`](digest-template.md)
3. Save the session's digests to `research/YYYY-MM-DD.md`
4. Use digests as direct inputs for that session's posts

## Running the Pipeline

ContentCreator uses Exa (available via MCP tools: `web_search_exa`, `web_search_advanced_exa`, `deep_search_exa`) to fetch and summarize content.

**Step-by-step for each session:**

1. Open `research/sources.md` — pick 2–3 priority sources for today
2. Copy the relevant Exa queries and run them
3. From the results, select the 3–5 best-fit stories (relevance > volume)
4. For each story, fill in the digest template
5. Save completed digests to `research/YYYY-MM-DD.md`
6. Write posts directly from the digests — the Angle field is your hook

## Directory Structure

```
research/
├── README.md             This file — pipeline overview
├── sources.md            Curated sources + pre-crafted Exa queries
├── digest-template.md    Format for each digest entry
└── YYYY-MM-DD.md         Daily digest files (one per session)
```

## Exa Tool Guidance

| Tool | When to use |
|------|------------|
| `web_search_exa` | Quick HN, GitHub, Product Hunt checks (`type: "instant"`) |
| `web_search_advanced_exa` | Domain-filtered searches (e.g., site:arxiv.org) |
| `deep_search_exa` | Research needing multi-angle synthesis (arXiv papers, complex topics) |

## Related Docs

- [`sources.md`](sources.md) — where to search and what queries to run
- [`digest-template.md`](digest-template.md) — how to format each entry
- [`../docs/posting-schedule.md`](../docs/posting-schedule.md) — when to post
- [`../docs/quality-gate.md`](../docs/quality-gate.md) — avoid-ai-writing check before publishing

*Last Updated: 2026-04-09 | [ABA-4](/ABA/issues/ABA-4)*
