---
name: query-knowledge
description: Search the Research agent hub cache (INDEX, topics, inbox) before any internet lookup. Use when looking up a prior finding, checking whether a topic was already researched, or running scripts/search-knowledge.
---

# Query knowledge

Search this hub before the web.

Hub path: `/Users/samalmutairi/ws/Research agent`

## Command

From any working directory:

```bash
"/Users/samalmutairi/ws/Research agent/scripts/search-knowledge" "<query>"
```

From this repo:

```bash
"./scripts/search-knowledge" "<query>"
```

Exit 0 = hits. Exit 1 = miss (do fresh research).

Matching: exact phrase first, then files containing **all** words in any order — so `"pkce oauth"` still finds a note titled "OAuth PKCE". Use 2-4 topic words, not a full sentence.

## Order

1. Run `search-knowledge`.
2. If needed, read `knowledge/INDEX.md`, then matching files under `knowledge/topics/` and `inbox/`.
3. Prefer a durable topic note over an inbox drop when both match.
4. If the note answers the question, return it in `templates/brief.md` form and cite the path. Do not re-fetch the web.
