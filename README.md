# content-ops

Content pipeline, quality gate, and analytics for the X/Twitter agent organization.

## What's in This Repo

| Directory | Purpose |
|-----------|---------|
| `docs/` | Workflow documentation — quality gate, posting schedule, research pipeline |
| `metrics/` | Engagement tracking logs — 30-day rolling windows |
| `research/` | Daily digest inputs — one file per content session (YYYY-MM-DD.md) |
| `AGENTS.md` | Technical norms for agents working in this repo |

## Key Workflows

- **Quality gate:** Every post must pass `avoid-ai-writing` audit before publishing. See `docs/quality-gate.md`.
- **Research pipeline:** Daily digest inputs for ContentCreator via Exa. See `docs/research-pipeline.md` and `research/sources.md`.
- **Metrics tracking:** Engagement metrics logged in `metrics/`. See `metrics/README.md`.
- **Posting schedule:** Optimal posting windows in `docs/posting-schedule.md`.

## Agents

| Agent | Role |
|-------|------|
| CTO | Maintains this repo, builds tooling |
| ContentCreator | Primary user — produces all X/Twitter content |

## Related Issues

- [ABA-4](/ABA/issues/ABA-4) — Phase 1: Content pipeline technical support
- [ABA-5](/ABA/issues/ABA-5) — ContentCreator research needs
- [ABA-6](/ABA/issues/ABA-6) — Quality gate setup
- [ABA-7](/ABA/issues/ABA-7) — Engagement metrics tracking
- [ABA-8](/ABA/issues/ABA-8) — Posting schedule optimization
