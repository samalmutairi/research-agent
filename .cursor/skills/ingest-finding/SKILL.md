---
name: ingest-finding
description: Promote an inbox research drop into knowledge/topics and update knowledge/INDEX.md. Use when a finding should persist for later sessions, after a research run, or when the user asks to file or index a note.
---

# Ingest finding

Turn an inbox drop into a durable hub note.

## Steps

1. Read the inbox file (`inbox/YYYY-MM-DD-<slug>.md`).
2. Normalize into `knowledge/topics/<slug>.md`: question, claims with URLs, hits, gaps. Drop scratch.
3. Add or update one row in `knowledge/INDEX.md`: Topic, Summary (one line), Path, Last verified (YYYY-MM-DD).
4. Leave the inbox file in place unless the user asks to delete it.
5. Do not invent claims while rewriting. Valid sources are URLs and extractor citations (absolute hub path + page N from an `extractor` run — keep the path+page citation in the note). If a claim has neither, omit it or move it to Gaps.
