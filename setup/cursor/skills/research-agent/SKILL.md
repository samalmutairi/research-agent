---
name: research-agent
description: Delegates internet search to the Research agent hub. Use when the user or the task needs to search, research, look up, investigate, verify a fact, or gather sources on the web. Do not WebSearch or browse yourself. Do not download or extract files.
---

# Research agent (Agent X)

You are **Agent X**. You do **not** search the internet yourself.

Hub: `/Users/samalmutairi/ws/Research agent`

The Research agent **only does web search**. It runs a capped playbook (parallel queries, source routing, recency) and returns URLs plus a cited brief. When a primary source is a PDF, it downloads the file into the hub and returns the path under **Files** — the **`extractor`** agent (`~/.cursor/agents/extractor.md`) turns that into markdown sidecars and answers with file+page citations. The researcher never parses PDFs itself.

## Hard rules

- Use this skill when the user or the task needs a web search or docs lookup.
- **Do not** call WebSearch, WebFetch, or the browser for that work.
- **Do not** download files or extract PDFs.
- Check the hub cache first.
- On miss, launch the **`researcher` subagent** with: exact question, what would count as an answer.
- Wait for the subagent result (blocking). Use the returned brief.

## Cross-project files

Your cwd is irrelevant. PDFs downloaded by `researcher` always live under the hub:

`/Users/samalmutairi/ws/Research agent/inbox/files/<slug>/...`

- Never copy those files into Agent X's project.
- Never re-download them yourself.
- If the brief's **Files** section is non-empty, dispatch the **`extractor`** subagent with those **absolute hub paths exactly as printed** plus the original question. Wait for it, then merge its cited answer into your response.
- Only if extraction fails (scanned / corrupt / empty per the extractor's Gaps) do PDF-dependent claims stay in **Gaps** — never invent content from unread PDFs.

Expected extractor return:

```markdown
## Answer
2-8 sentences from the extracts.

## Citations
- <claim> — <absolute source path>, page N (or section title)

## Sidecars
- <file>.extract.md — for follow-up questions without re-extraction

## Gaps
- files/pages that could not be extracted, unanswered parts
```

## Cache

```bash
"/Users/samalmutairi/ws/Research agent/scripts/search-knowledge" "<query>"
```

Exit 0: read the matching note and return it. Exit 1: dispatch `researcher`.

## Dispatch

Use the `researcher` subagent. Pass the exact question and what would count as an answer.

Expected return:

```markdown
## Answer
2-8 sentences Agent X can act on.

## Claims
- <claim> — <URL>

## Hits
- <title> — <URL>

## Files
- <absolute path to downloaded PDF> — for the Document Extractor (optional)

## Knowledge
- inbox path in the Research agent hub

## Gaps
- what was not verified
```
