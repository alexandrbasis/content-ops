# X/Twitter Posting Schedule

Optimal posting windows based on 2026 data from Buffer (8.7M tweets), Sprout Social (2B engagements), and Statweestics.

## Recommended Schedule

### Primary Slots (Highest Engagement)

| Day | Time (Local) | Notes |
|-----|-------------|-------|
| Tuesday | 9:00–10:00 AM | #1 slot globally (Buffer data) |
| Wednesday | 9:00–11:00 AM | #2/#3 slots globally — best overall day |
| Wednesday | 12:00–1:00 PM | "Single best hour" per AutoTweet data |
| Thursday | 10:00 AM–1:00 PM | Strong for threads and interactive content |

### Secondary Slots (Good Reach)

| Day | Time (Local) | Notes |
|-----|-------------|-------|
| Monday | 9:00–11:00 AM | Audience catching up; lead with news/insight |
| Tuesday | 1:00–3:00 PM | Afternoon secondary peak |
| Friday | 8:00–10:00 AM | Only this window; skip afternoon on Fridays |

### Avoid

- Saturday mornings and Sunday (except 7–9 PM Sunday for conversational content)
- Late Friday afternoons (2 PM+)
- Any slot between 2–6 AM local time

---

## Posting Frequency

| Mode | Posts/Day | When to Use |
|------|-----------|-------------|
| Minimum (algorithmic floor) | 1 | Absolute minimum to maintain feed presence |
| **Recommended** | **2–3** | **Optimal for quality + reach balance** |
| Aggressive growth | 4–5 | Requires strong content supply pipeline |
| Do not exceed | 7 | Per-post performance degrades above this |

**ContentCreator target: 2–3 posts per weekday, hitting at least one primary slot.**

---

## Why Timing Still Matters in 2026

X's algorithm is chronological-adjacent. A post that gets strong early engagement (within the first 30–60 minutes) gets surfaced in "For You" feeds of non-followers. For accounts under 10K followers, timing is a significant multiplier — you don't have enough followers to generate organic velocity on your own, so you need to catch the natural traffic window.

Posting at a peak time doesn't fix bad content. It amplifies good content.

---

## Content Type by Slot

| Slot | Best Content Types |
|------|--------------------|
| 9–10 AM weekday | Insights, data points, strong opinions |
| 12–1 PM weekday | Quick takes, questions, short threads |
| Afternoon (1–3 PM Tue/Wed) | Longer threads, how-tos, case studies |
| Friday 8–10 AM | Week-in-review, lightweight, lighter tone |

---

## Scheduling via Publora

ContentCreator uses the `x-post` skill (Publora MCP) for posting. The recommended workflow:

1. Batch draft 6–10 posts per session
2. Schedule each post at a primary slot time using Publora's scheduling feature
3. Leave 1–2 slots per week open for reactive, real-time posts on trending topics
4. After each post, log impressions and replies in `metrics/2026-MM.md`

**Target mix:** 70% scheduled (batch-created) / 30% reactive (real-time).

---

## Iteration

This schedule is a starting baseline. Once `metrics/` data accumulates (4+ weeks), compare actual engagement by time slot and adjust:

- If Tuesday 9 AM consistently underperforms, shift to a different slot
- If a specific day shows outsized engagement, add a slot there
- Review schedule monthly alongside the 30-day rolling metrics report

Related: [ABA-7](/ABA/issues/ABA-7) — engagement metrics tracking, [ABA-8](/ABA/issues/ABA-8)

---
*Last Updated: 2026-04-09 | Sources: Buffer (8.7M tweets), Sprout Social (2B engagements), Statweestics, AutoTweet*
