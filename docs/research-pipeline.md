# Content Research Pipeline

Workflow documentation for ContentCreator's daily research process.

---

## What This Is

The research pipeline converts raw source monitoring into structured digest inputs that ContentCreator can immediately turn into posts. It eliminates the blank-page problem by ensuring every content session starts with 3–5 pre-researched story inputs.

---

## The Digest Format

Every research input follows this structure (see [`research/digest-template.md`](../research/digest-template.md) for the full template with examples):

```
Title: [headline or your summary of what this is really about]
Source: [URL]
Summary: [2–3 sentences: what it says + why it matters]
Angle: [1 sentence: the content hook]
Quote: [optional — one verbatim line if it's strong enough to anchor a post]
```

---

## Daily Research Workflow

### Session start
1. Open `research/sources.md` — pick 2–3 sources for today per the rotation schedule
2. Run the pre-crafted Exa queries for those sources
3. Skim results — discard anything older than 48h, anything you've already covered, anything that requires deep domain expertise you don't have

### Digest creation
4. Select the 3–5 best-fit stories from results (relevance > volume)
5. For each, write the digest entry — summary and angle in your own voice, not copied
6. Save all entries to `research/YYYY-MM-DD.md`

### Content session
7. Read through your digests
8. Pick 2–3 that have the strongest angles for today's format mix
9. Write posts using the digest as the raw material — the Angle field is your hook

---

## File Naming

Daily digests go in `research/` with date-based names:

```
research/2026-04-09.md
research/2026-04-10.md
```

Start each file with a front-matter block:

```markdown
# Research Digest — YYYY-MM-DD

Session: [morning / afternoon / evening]
Sources checked: [comma-separated list]
Entries: N

---
```

Then append each digest entry separated by `---`.

---

## Source Rotation

See [`research/sources.md`](../research/sources.md) for:
- Full curated source list with topic mappings
- Pre-crafted Exa queries for each source
- Suggested daily rotation schedule
- Instructions for adding new sources

---

## Exa Tool Reference

| Need | Tool + Params |
|------|--------------|
| Quick HN or Product Hunt check | `web_search_exa`, `type: "instant"` |
| Domain-scoped search (arXiv, GitHub) | `web_search_advanced_exa`, set `domain` |
| Deep synthesis of a paper or topic | `deep_search_exa` |

---

## Trending Signal

To catch what's hot on X right now before it goes stale:

```
Tool: web_search_exa
Query: trending AI developer tools X Twitter today 2026
Params: { type: "instant", numResults: 15 }
```

Run this at the start of each session before diving into newsletters or arXiv — it catches live momentum that slower sources will cover tomorrow.

---

## Quality Bar

A good digest entry:
- Source is fresh (< 48 hours, unless it's a slow-burn trend)
- Summary is your words — not copied text
- Angle is one tight sentence with a clear hook or tension
- You could write the post in 5 minutes using just this entry

Reject entries that:
- Are pure announcement without an angle ("X company raised $Y")
- Require domain expertise you'd need hours to fake
- Are already saturated on X by bigger accounts

---

## Related Docs

- [`research/sources.md`](../research/sources.md) — curated source list + Exa queries
- [`research/digest-template.md`](../research/digest-template.md) — entry format with examples
- [`docs/posting-schedule.md`](posting-schedule.md) — optimal posting windows
- [`docs/quality-gate.md`](quality-gate.md) — avoid-ai-writing check before publishing
- [`metrics/README.md`](../metrics/README.md) — tracking what's working

*Last Updated: 2026-04-09 | [ABA-4](/ABA/issues/ABA-4)*
