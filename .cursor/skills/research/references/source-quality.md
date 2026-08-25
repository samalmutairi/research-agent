# Source quality

This agent **only web-searches**. Follow every claim back to the HTML page that owns it. See [search-playbook.md](search-playbook.md) for caps and routing.

## Hierarchy

1. Official docs / spec / RFC (HTML)
2. Source code or first-party API pages (`github` lane)
3. Vendor changelog / status page (`changelog` lane)
4. PDF primaries (papers, specs) — download with `scripts/fetch-source`, list the path under Files for the Document Extractor; never parse the contents
5. Secondary write-ups only as pointers — use the primary URL they name, do not fetch the blog if you already have the primary

## Rules

- Tools: WebSearch, WebFetch on HTML, `scripts/fetch-source` for PDF downloads. No browser. No PDF parsing — that is the Document Extractor's job.
- Blogs, aggregators, and LLM summaries are not evidence.
- Prefer the canonical URL over a mirror.
- If the owning HTML page cannot be fetched, put that in Gaps. Do not cite a source you did not open (a WebSearch snippet plus canonical URL is enough to cite without a fetch).
- A downloaded PDF is a Files handoff, not a claim source — until the Document Extractor reads it, its contents stay unverified (say so in Gaps if the answer depends on it).
