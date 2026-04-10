---
title: "My Codebase Had Docs in 4 Places. I Built a Wiki That Maintains Itself."
type: x-article
status: draft
date: 2026-04-11
source: research/articles/2026-04-10-llm-wiki-architecture.md
tags:
  - llm-wiki
  - codebase-documentation
  - qmd
  - obsidian
  - claude-code
  - implementation-guide
word-count: ~1100
format: x-article (publish via x.com Article editor)
scheduled-promo-thread: 2026-04-11T13:00:00Z
---

# My Codebase Had Docs in 4 Places. I Built a Wiki That Maintains Itself.

Documentation in my monorepo was scattered across four folders, none of them connected:

```
docs/                    — ADRs, architecture constitution, PRDs
backend/docs/            — 9 files: project structure, sessions, AI, testing
mobile-app/docs/         — 10 files: auth, HTTP, state, contracts, analytics
tasks/completed/         — dozens of completed tasks with implementation history
```

Understanding how authentication worked meant reading files from three different folders. The session docs had no idea the AI module docs existed. `grep "authentication"` couldn't find the file that said "JWT login flow." New developers asked me the same questions every week.

I fixed this with a wiki that compiles all of it into one searchable, interlinked knowledge base and keeps itself current. 28 pages, 600 indexed documents, six layers of automation. Here's every step.

## The architecture in one paragraph

Claude Code acts as a librarian. It reads source docs and code, then writes compiled wiki pages into a `wiki/` directory inside the monorepo. qmd (Tobi Lutke's semantic search tool) indexes everything locally. Obsidian renders the wiki with a graph view and clickable links.

The critical design choice: source docs stay close to the code. The wiki compiles from them but never replaces them. This prevents a hallucination loop where the AI reads its own output as truth.

## Phase 1: The vault structure

Create the wiki directory:

```bash
mkdir -p wiki/{raw,concepts,modules,decisions,onboarding,output}
```

Then write `wiki/claude.md`. This file matters more than everything else combined. Without it, the AI writes scattered notes. With it, strict protocol.

About 60 lines. It defines three operations: INGEST (read sources, write wiki pages, add backlinks, update indexes), QUERY (start at `master-index.md`, drill into specifics, use qmd for deep search), and LINT (audit for broken links, orphan pages, stale content).

The line that makes the whole thing work:

> "You are responsible for keeping this wiki current. Do not wait for the user to ask."

That directive turns a folder of markdown into a living knowledge base.

Next, create `master-index.md` as the navigation hub. Links to every section: concepts, modules, decisions, onboarding. The AI reads this first before answering any question.

Every subfolder gets an `_index.md` catalog, one level down.

## Phase 2: Compile the content

I had 28 pages to write. Instead of going one by one, I ran three AI agents in parallel:

- Agent 1 compiled cross-cutting concepts (authentication, architecture, API contracts)
- Agent 2 handled secondary concepts (testing, i18n, analytics) and migrated 7 ADRs
- Agent 3 compiled all 7 domain module pages

Each agent read source docs plus actual source code, then produced wiki pages with YAML frontmatter, wikilinks to related pages, source citations, and backlink sections.

Output: 28 files, roughly 3,400 lines total. The sessions module page alone hit 292 lines because it's the most complex domain. It covers the session lifecycle state machine, exercise types, skill dimensions, domain services, and the planning pipeline.

I also migrated 6 ADRs from `docs/adr/` and 1 from `mobile-app/docs/adr/` into `wiki/decisions/`. Added wikilinks and normalized naming. Then deleted the original folder (git history preserves everything).

## Phase 3: Search with qmd

qmd turns your wiki and codebases into a unified search engine that understands meaning, not just keywords.

Install and create collections:

```bash
npm install -g @tobilu/qmd

qmd collection add ./wiki --name wiki
qmd collection add backend/src --name backend \
  --mask "**/*.{ts,md}" --ignore "**/*.spec.ts"
qmd collection add mobile-app/src --name mobile \
  --mask "**/*.{tsx,ts,md}"
```

Then add context descriptions:

```bash
qmd context add qmd://wiki "LLM-compiled wiki — architecture, concepts, ADRs, modules"
qmd context add qmd://backend "NestJS backend — DDD, Clean Architecture, 52 use-cases"
```

When qmd returns a search result, it includes that context. The AI knows *where* the result came from and *what that code area does*, not just the matching text.

Generate embeddings:

```bash
qmd embed
```

Downloads EmbeddingGemma-300M (~328MB) and processes everything locally. 1,343 chunks from 600 documents in 60 seconds. No API calls, no cloud dependency.

Connect qmd to Claude Code as an MCP server:

```bash
claude mcp add --transport stdio --scope local qmd -- /opt/homebrew/bin/qmd mcp
```

Set `includeByDefault: false` on everything except wiki. A query like `qmd query "auth flow"` searches the compiled wiki first (~2-3K tokens) instead of loading 400K+ raw documents.

## Phase 4: Obsidian

Open `wiki/` as an Obsidian vault. Graph view shows all 28 pages and their connections. Wikilinks are clickable. Callouts render. Backlinks panel shows who references each page.

Add a `.gitignore` for Obsidian's personal settings and you're set for team use.

## Phase 5: Keep it fresh

This is where most wiki projects die. Without automation, content goes stale in weeks. I built six layers of protection:

1. **Proactive directive** in `claude.md` tells the AI to update wiki after code changes
2. **Stop hook** checks `git diff` when sessions end, reminds you to run `/wiki-update`
3. **Code review agent** flags missing wiki updates as a major finding during `/sr`
4. **On-demand skills** (`/wiki-update` and `/wiki-lint`) for manual maintenance and auditing
5. **Machine-managed fact scripts** extract volatile data (Prisma models, enum values) from source code and inject them into wiki pages deterministically. No AI needed for parts derivable from code.
6. **CI hard gate** runs the fact pipeline on every PR. If wiki pages drift from source code, the build fails.

First four are nudges. Last two are hard enforcement. Together they keep the wiki accurate even when you forget.

## The numbers

| Metric | Value |
|--------|-------|
| Wiki pages | 28 files, ~3,400 lines |
| qmd collections | 6 |
| Indexed documents | 600 docs, 1,343 chunks |
| Embeddings | EmbeddingGemma-300M, 60 seconds |
| Tokens per query | ~2-3K (vs 400K+ loading raw docs) |
| docs/ cleanup | 15,000 → 3,700 lines (-75%) |

Setup took about a week. Two days for infrastructure, rest for initial content compilation. After that, maintenance is automatic.

## What actually changed

Before: `grep` couldn't find answers. Docs contradicted each other. New developers asked me the same questions.

After: anyone types a question, gets an answer from compiled, cross-referenced wiki pages in seconds. The wiki flags its own staleness. CI catches drift before it reaches main.

If your codebase has documentation scattered across folders and nobody reads it, this is fixable. The tools all run locally and cost nothing.

What does your codebase documentation look like right now?
