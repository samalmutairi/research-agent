# Search playbook

Search-only. No downloads, no PDFs, no browser. **Spend tokens on selection, not on pages.**

## Hard caps (do not exceed)

| Action | Max per question |
| --- | --- |
| WebSearch calls | 4, all in **one** parallel turn |
| WebFetch calls | 3 HTML pages total |
| PDF downloads (`scripts/fetch-source`) | 2, only when the PDF is a primary source |
| Hits listed in the note | 8 URLs, one line each |
| Extra search round | 2 more WebSearch only if round 1 found **zero** primary URLs |

Stop as soon as **two** primary HTML sources confirm the answer. Unused fetch budget is success, not a leftover to spend.

## Effort tiers (stop rules inside the caps)

Pick the tier before searching. Caps are a ceiling, not a target.

| Tier | When | Budget |
| --- | --- | --- |
| a | Single fact, canonical source known (arXiv ID, RFC number, official docs URL) | Go direct; at most 1 WebSearch to confirm currency |
| b | Single fact, source unknown | Up to 2 WebSearch; stop at first primary confirmation; 2nd source only if recency-sensitive or sources disagree |
| c | Comparison / multi-claim | Up to 4 WebSearch, one parallel turn |

Tier a/b inbox notes may be short form (≤5 lines: date, question, claim(s) with URL, gap); tier c uses `templates/finding.md`.

## Token rules

- Prefer WebSearch snippets. Fetch only when a snippet is too thin to cite a claim.
- Never paste WebFetch bodies, HTML, or long quotes into the inbox note or the brief. Quote at most one short clause per claim.
- Do not WebFetch PDFs, binaries, or JS-only apps. PDF primaries: download with `scripts/fetch-source` (costs zero context tokens) and list the path under Files for the Document Extractor. Never open or parse the PDF yourself.
- Do not run a second fetch on the same URL.
- Do not summarize every hit. Rank, pick, then fetch the winners.

## Route (pick one primary lane)

Choose from the question. Mix at most **two** lanes.

| Lane | Use when | Query ingredients |
| --- | --- | --- |
| `docs` | API, SDK, library, product how-to | official product + "docs" + symbol/API name |
| `github` | implementation, source of truth in a repo | `site:github.com` + owner/repo or project name |
| `rfc` | protocol, HTTP, OAuth, email, IETF | `site:rfc-editor.org` or `site:datatracker.ietf.org` + RFC number or protocol name |
| `web-standard` | HTML, DOM, CSS | `site:html.spec.whatwg.org` or `site:w3.org` |
| `changelog` | version, breaking change, "does it still work" | vendor changelog + current year |

## Query variants (build ≤4, fire together)

1. **Canonical** — RFC number, API name, exact error string.
2. **Routed** — the `site:` (or docs domain) for the chosen lane.
3. **Natural** — the user's question in plain words (only if 1–2 are not enough).
4. **Recency** — only if the question is time-sensitive: add `changelog` or the current year (`2026`).

Drop the natural query if canonical + routed already cover it. Four searches is the ceiling, not a target.

## Recency

- **Time-sensitive** (current API, pricing, "latest", security advisory): prefer 2025–2026 and changelogs. If every hit is older, still cite them and put "may be stale" in Gaps.
- **Stable spec** (RFC, language standard): publication date is enough; do not force a year token.
- Never fetch a third page just to find a newer blog.

## Rank before fetch

Keep URLs that match the source hierarchy in `source-quality.md`. Discard aggregators, SEO blogs, and LLM-written roundups unless they point at a primary URL you then use.

Fetch order: official docs / RFC HTML → first-party API page → GitHub README or canonical doc page → changelog.

## After search

Write `templates/finding.md` with claims + URLs only. Return `templates/brief.md`. Do not attach raw tool output.
