# AGENTS.md — Technical Norms for content-ops

This file defines how agents should work in this repository.

## Commit Style

- Short imperative subject line (50 chars max): `Add quality gate docs`
- Body only when context isn't obvious
- Co-author line required: `Co-Authored-By: Paperclip <noreply@paperclip.ing>`

## Branch Strategy

- `main` is stable — only merge completed, reviewed work
- Feature branches: `<agent-namekey>/<issue-identifier>-<short-description>`
  - Example: `cto/ABA-6-quality-gate`
- No long-lived branches — merge and delete promptly

## Directory Conventions

```
content-ops/
├── docs/           # All workflow documentation (markdown)
├── metrics/        # Engagement tracking logs (one file per 30-day window)
├── research/       # Daily digest inputs for ContentCreator (one file per session)
├── AGENTS.md       # This file
└── README.md       # Repo overview
```

## File Naming

- `docs/` files: `kebab-case.md` (e.g., `quality-gate.md`, `posting-schedule.md`)
- `metrics/` files: `YYYY-MM.md` (e.g., `2026-04.md`)
- `research/` files: `YYYY-MM-DD.md` (e.g., `2026-04-09.md`) — one file per content session

## Documentation Standards

- Every doc in `docs/` starts with a one-line summary of what it covers
- Include a "Last Updated" date at the bottom
- Cross-link to related Paperclip issues using `/ABA/issues/ABA-N` format

## Metrics Files

- Use the template in `metrics/template.md` for all new monthly files
- Add entries after each post session, not in batch
- Never delete old entries — the rolling window calculation depends on history

## Agent Responsibilities

| Agent | Can write to | Should not touch |
|-------|-------------|-----------------|
| CTO | All directories | Nothing restricted |
| ContentCreator | `metrics/` (adding entries), `research/` (daily digest files) | `AGENTS.md`, `docs/`, core repo structure |
