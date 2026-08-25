# Research agent

> Install on a new machine (Cursor, Claude Code, ChatGPT/Codex): see [setup/README.md](setup/README.md). Companion repo: Document Extractor. hub

This repo is a **Research agent**. It **only does web search**. Other Cursor sessions (**Agent X**) ask it to find sources and return a cited brief.

Hub path: `/Users/samalmutairi/ws/Research agent`

## Agent X (any other project)

1. User-level skill `research-agent` (`~/.cursor/skills/research-agent/SKILL.md`) — check cache, then dispatch `researcher`.
2. Cache:

```bash
"/Users/samalmutairi/ws/Research agent/scripts/search-knowledge" "oauth pkce"
```

3. On a miss, launch **`researcher`**. Agent X must not WebSearch, WebFetch, or browse.

The researcher follows a **capped playbook**: up to 4 parallel WebSearch queries (docs / GitHub / RFC routing, recency when needed), then at most 3 HTML WebFetches. PDF primaries are **downloaded** (max 2, via `scripts/fetch-source`) into `inbox/files/` and returned as paths under **Files** — the **`extractor`** agent (`~/.cursor/agents/extractor.md`, pipeline in `/Users/samalmutairi/ws/Document Extractor`) converts them to markdown sidecars and answers with file+page citations. The researcher never parses PDFs and never uses the browser. Cache hits skip the web entirely.

## Used from another project

Agent X's working directory does **not** matter. Downloads never go into that project.

1. Agent X (any repo) dispatches `researcher`.
2. `researcher` runs the absolute hub scripts (`search-knowledge`, `fetch-source`).
3. `fetch-source` writes under `/Users/samalmutairi/ws/Research agent/inbox/files/<slug>/` and prints that **absolute** path.
4. The brief's **Files** section carries those hub paths.
5. If **Files** is non-empty, Agent X dispatches the `extractor` agent with those absolute paths plus the original question, then merges its cited answer into the final response. Do not copy files into Agent X's project.

This requires a **local** Cursor session on the same machine (shared filesystem). A cloud agent that cannot see the hub path cannot use hub downloads.

## Dedicated session (this workspace)

Open this project and use `/research` as a Custom Mode. Write markdown findings to `inbox/`.

## Scripts

```bash
"./scripts/search-knowledge" "<query>"                                  # cache lookup (exit 1 = miss)
"./scripts/fetch-source" "https://example.com/paper.pdf" "optional-slug"  # PDF download for the Extractor (HTTPS, 25 MB cap)
```

## Layout

- `knowledge/INDEX.md` — catalog other agents search first
- `knowledge/topics/` — durable notes
- `inbox/` — search findings
- `templates/brief.md` — return schema
- `.cursor/agents/researcher.md` — also at `~/.cursor/agents/researcher.md`
- `.cursor/skills/research/references/search-playbook.md` — query variants, routing, recency, token caps
