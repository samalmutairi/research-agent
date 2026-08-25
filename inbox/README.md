# Inbox

Search findings from the `researcher` subagent. Do not edit `knowledge/INDEX.md` until ingest.

- Findings: `inbox/YYYY-MM-DD-<slug>.md` (copy `templates/finding.md`)
- Downloads: `inbox/files/<slug>/` — PDFs saved by `scripts/fetch-source` for the **Document Extractor** agent. The researcher never reads their contents.

Promote a finding into `knowledge/topics/` with the `ingest-finding` skill.
