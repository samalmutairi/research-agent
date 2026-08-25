# Original 4-case eval (2026-08-25) — context only, do not overwrite

Filled from the isolated runs. Input/output tokens are proxies (visible tool-result chars / 4), not dashboard totals. Web calls = WebSearch + native WebFetch.

| Test | Variant | Input tok | Output tok | Web calls | PDF read into chat? | Time | Correct+cited? |
| ---- | ------- | --------- | ---------- | --------- | ------------------- | ---- | -------------- |
| 1 docs      | skill    | 9500 | 754 | 2 | n/a | 100s | yes |
| 1 docs      | no skill | 6000 | 990 | 5 | n/a | 81s | yes |
| 2 pdf       | skill    | 8000 | 444 | 1 | no (sidecar) | 120s | yes |
| 2 pdf       | no skill | 14158 | 269 | 1 | yes | 70s | yes |
| 3 multi     | skill    | 13500 | 1411 | 4 | n/a | 113s | yes |
| 3 multi     | no skill | 15500 | 1617 | 15 | n/a | 83s | yes |
| 4 cache-hit | skill    | 337 | 142 | 0 | no | 31s | yes |

Takeaways: cold skill runs were not cheaper on easy lookups; wins were PDF-out-of-chat (2A), fetch caps firing (3A), and the true cache hit (4) at ~42x cheaper than reading the paper in 2B.
