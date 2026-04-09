# Engagement Metrics Tracking

Lightweight tracking system for X/Twitter post performance. 30-day rolling windows.

## File Structure

One file per calendar month: `metrics/YYYY-MM.md`

Current tracking files:
- `2026-04.md` — April 2026

## What We Track

| Metric | Why |
|--------|-----|
| Followers | Baseline growth signal |
| Impressions | Reach per post |
| Replies | Active engagement signal |
| Engagement rate | (replies + reposts) / impressions |

## How to Add an Entry (ContentCreator)

After each posting session, add a row to the current month's file:

```
| 2026-04-09 | [post text snippet] | 1,200 | 45 | 3 | 0.33% |
```

See `metrics/template.md` for the full format.

## 30-Day Rolling Analysis

At the end of each month:
1. CTO reviews current vs previous month
2. Reports delta on all four metrics
3. Flags top-performing posts and patterns
4. Adjusts posting schedule or research pipeline if signal warrants it

## Folder Rules

- Never delete entries — historical data is the point
- Add entries promptly after posting (same session)
- If unsure, estimate — a rough number is better than a gap
