---
name: wiki-llm-setup
description: Set up or retrofit an LLM Wiki in a repository using a wiki-first folder pattern (wiki/raw + wiki derived pages + schema), ingest/query/lint operations, and index/log conventions from the DDPA article and Karpathy's original gist. Use when the user wants a persistent, compounding markdown knowledge base for AI agents.
compatibility: Markdown + YAML frontmatter. Works best in git repositories and with agent instruction files such as AGENTS.md or CLAUDE.md.
---

# wiki-llm-setup

Practical workflow for adopting an LLM-maintained wiki as a persistent knowledge layer for AI agents.

Use this skill when a user wants to:
- initialize a new LLM Wiki from scratch;
- retrofit an existing notes/research vault into a structured wiki workflow;
- move from one-shot RAG answers to compounding, maintained markdown knowledge;
- standardize ingest/query/lint operations for repeatable agent behavior;
- keep raw sources immutable while letting the LLM maintain derived wiki pages;
- make wiki evolution auditable with `index.md` and `log.md`.

## Inputs Required

Before creating files or changing structure, ask and confirm:

1. Target scope
- Apply to current repository or another directory?

2. Setup mode
- `from-scratch` (new wiki scaffold) or `adapt-existing` (merge into existing notes/wiki)?

3. Domain and intended outcomes
- What is this wiki for: research, product knowledge, internal team memory, personal second brain, or mixed?

4. Source policy
- Which source types are allowed (articles, docs, PDFs, transcripts, datasets, images)?
- Should raw sources be strictly immutable?

5. Governance level
- Human-in-the-loop for each ingest, or mostly autonomous ingestion with periodic review?
- Any mandatory citation/provenance rules?

6. Change policy
- Merge with existing files (recommended) or replace sections when safe?

If any answer is ambiguous, stop and ask a follow-up instead of guessing.

## Directory placement contract

Use these placement rules unless the user explicitly overrides them:

- Single top-level knowledge directory: `wiki/`
- All LLM Wiki assets must be inside `wiki/`
- Raw source layer: `wiki/raw/`
- Derived knowledge pages and operation files (`index.md`, `log.md`) also inside `wiki/`
- Schema contract file (`AGENTS.md` or `CLAUDE.md`) may remain in repo root

If an existing repository already uses a different layout (for example root-level `raw/`), preserve it during adaptation unless the user asks for migration.

## What To Do First

1. Detect current knowledge layout.
- Check for `wiki/`, `wiki/raw/`, `AGENTS.md`, `CLAUDE.md`, `README.md`, `docs/`, `notes/`, `knowledge/`, `index.md`, `log.md`.

2. Classify current model.
- Determine whether the repo currently behaves like:
  - raw-only note storage,
  - ad-hoc wiki without operating rules,
  - structured LLM Wiki with defined ingest/query/lint.

3. Decide setup flow.
- No structured wiki: run `from-scratch`.
- Existing notes/wiki: run `adapt-existing` and preserve existing intent.

4. Anchor on the three-layer architecture.
- `wiki/raw/` as immutable source of truth,
- `wiki/` as LLM-maintained knowledge layer,
- schema file (`AGENTS.md`, `CLAUDE.md`, or equivalent) as behavioral contract.

## Preflight Detection

Run in target repo:

```bash
pwd
rg --files -g 'AGENTS.md' -g 'CLAUDE.md' -g 'README.md' -g 'wiki/**' -g 'raw/**' -g 'docs/**' -g 'notes/**' -g 'knowledge/**'
rg -n "ingest|query|lint|index.md|log.md|wiki|knowledge base|RAG|cross-link|wikilink" -g '*.md' -g '*.txt' -g '*.yaml' -g '*.yml'
```

Interpretation:
- If `wiki/` does not exist, scaffold canonical structure.
- If `wiki/` exists but lacks `index.md` and `log.md`, add them first.
- If schema instructions are missing, create or patch `AGENTS.md`/`CLAUDE.md` with explicit workflow rules.

## Canonical File Architecture

Recommended baseline:

```text
wiki/
  raw/
    inbox/
    assets/
  index.md
  log.md
  entities/
  concepts/
  summaries/
  queries/
AGENTS.md (or CLAUDE.md)
```

Design intent:
- `wiki/raw/` is immutable input.
- `wiki/` is continuously maintained output.
- `index.md` is the content catalog for retrieval/navigation.
- `log.md` is append-only chronology of operations.

## Flow A: From Scratch

### Step 1: Scaffold the three layers

Create `wiki/`, `wiki/raw/`, and schema file (`AGENTS.md` or `CLAUDE.md`) if missing.

### Step 2: Seed `wiki/index.md`

`index.md` should include:
- top-level categories (entities, concepts, summaries, query artifacts);
- one-line descriptions per page;
- optional metadata (last updated, source count).

### Step 3: Seed `wiki/log.md`

Use append-only, parseable headers.
Example pattern:

```md
## [2026-06-26] ingest | Source title
- action: created summary page
- touched: wiki/summaries/source-title.md, wiki/concepts/topic-x.md
- notes: key contradiction flagged with existing claim on Y
```

### Step 4: Define schema workflow rules

In `AGENTS.md`/`CLAUDE.md`, define:
- ingest behavior (read source from `wiki/raw/`, update summaries, update related pages, update index, append log);
- query behavior (answer from wiki first, add citations, optionally persist valuable answers into wiki);
- lint behavior (detect contradictions, stale claims, orphans, missing cross-links, gaps);
- quality gates (citation expectations, no silent deletion of unresolved conflicts).

### Step 5: Run first controlled ingest

Ingest one source to validate:
- touched multiple pages where needed;
- index updated;
- log appended;
- contradictions explicitly noted.

## Flow B: Adapt Existing Project

### Step 1: Map existing materials into layers

Typical mapping:
- mixed notes/articles -> `wiki/raw/` (immutable source layer);
- derived summaries and concept pages -> `wiki/`;
- existing AI instruction files -> schema contract.

### Step 2: Preserve and normalize

When adapting existing wiki content:
- keep existing page names unless they are misleading;
- standardize link style and page categories gradually;
- avoid mass rewrites when targeted fixes are enough.

### Step 3: Add missing operational controls

If absent, add:
- `wiki/index.md` content catalog;
- `wiki/log.md` operation timeline;
- explicit ingest/query/lint instructions in schema file.

### Step 4: Introduce periodic lint discipline

Define lint cadence and scope policy:
- per-ingest local checks on touched pages and neighbors;
- periodic broad lint for stale pages and unresolved conflicts.

## Operational Model (Ingest, Query, Lint)

### Ingest
- Read one new raw source.
- Create/update summary page.
- Update related entity/concept pages.
- Update `wiki/index.md`.
- Append `wiki/log.md` entry.

### Query
- Start from `wiki/index.md` to locate relevant pages.
- Synthesize answers from wiki pages with citations.
- Persist high-value outputs as new wiki pages when useful.

### Lint
- Detect contradictions between related pages.
- Flag stale claims superseded by newer sources.
- Find orphan pages and missing cross-links.
- Identify knowledge gaps and propose next-source targets.

## Validation Checklist

Before completion, confirm:
- `wiki/` and `wiki/raw/` layers exist and responsibilities are clear;
- raw sources are treated as immutable;
- `wiki/index.md` exists and is updated on ingest;
- `wiki/log.md` exists and is append-only;
- schema file contains explicit ingest/query/lint workflow;
- contradictions and uncertainty are represented explicitly, not overwritten silently;
- wiki pages are interlinked and discoverable.

## Troubleshooting

1. Wiki quality degrades over time
- Strengthen lint rules and citation requirements.
- Add periodic stale-claim cleanup.

2. Token cost grows too fast
- Query via `index.md` first, then read only relevant pages.
- Prefer scoped lint over whole-wiki passes for frequent checks.

3. Duplicate concepts/pages appear
- Add naming and merge conventions in schema.
- Record merge decisions in `log.md`.

4. Agent behaves like generic chat instead of maintainer
- Tighten schema instructions with explicit step-by-step operations.
- Require operation logging for ingest/query/lint.

## Execution Guidance

When invoked, do this sequence:
1. Run preflight inventory and detect existing wiki assets.
2. Confirm setup mode (`from-scratch` or `adapt-existing`).
3. Ensure three-layer architecture exists.
4. Ensure `index.md` and `log.md` are present and structured.
5. Patch schema instructions with ingest/query/lint rules.
6. Validate with one sample ingest and one sample query.
7. Summarize resulting structure and recommended next sources.

## References

- https://ddpa.ru/kb/ai/llm-wiki/
- https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
