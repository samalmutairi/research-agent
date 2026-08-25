# Measurement protocol

## Isolation

- One fresh, isolated subagent per run; no context reuse between A and B of the same case.
- Same model for every run in a suite.
- A runs follow the real pipeline: `scripts/search-knowledge` (cache check) → `researcher` subagent → `extractor` subagent when the brief's Files section is non-empty. The orchestrating session only routes; it does not search.
- B runs are authorized control runs: the subagent uses WebSearch/WebFetch itself and, when needed, downloads PDFs to `./tmp-bench/` and reads them directly. Delete `tmp-bench/` after each B run.

## What counts

- **Web calls** = WebSearch + native WebFetch only. `scripts/fetch-source` and `extract-doc` are logged in the run note as CLI calls, not web calls.
- **Tokens**: Cursor Settings → Usage totals when available (count researcher/extractor requests too). Otherwise proxy = visible tool-result characters / 4, self-reported by the run subagent and marked `est`.
- **Wall time**: dispatch to completion of the run (A runs include extractor stage).

## Hard rules for A runs

- Never Read() PDFs or paste page bodies into chat; sidecar contents stay in the extractor's context.
- Caps per the playbook: 4 WebSearch, 3 HTML WebFetch, 2 PDF downloads; stop at cap and report.
- Gaps reported honestly (`scanned_needs_ocr`, JS-rendered, oversized, etc.) — never invented content.

## Run notes

One note per run at `benchmarks/runs/s08-<case><a|b>.md` using the header template in `runs/README.md`.
