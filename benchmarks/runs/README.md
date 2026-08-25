# Run notes

One markdown file per benchmark run: `s08-<case><a|b>.md` (e.g. `s08-13a.md`), cache-only cases as `s08-19.md` / `s08-20.md`.

Header template (then the cited answer below it):

```markdown
# s08-<id> <short title>
wall_seconds:
web_searches:
native_webfetch:
fetch_source_cli:
extract_doc_cli:
cache_hits:
search_knowledge_exit:     # 0 hit / 1 miss / n/a for B
pdf_read_into_chat:        # yes / no / n/a
sidecar_read_into_chat:    # must be no on A (extractor context only)
gaps:                      # none | scanned_needs_ocr | js_rendered | oversized_pdf | ...
visible_tool_chars:        # est, self-reported
proxy_input_tok:           # visible_tool_chars / 4, est
proxy_output_tok:          # est
correct_and_cited:         # yes/no + one line why
cap_events:                # 0 or describe
inbox_note:                # path or none
```
