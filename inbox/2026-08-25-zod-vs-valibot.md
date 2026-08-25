# Finding: Zod vs Valibot — bundle size, API style, when to pick each

- Date: 2026-08-25
- Asked by: Agent X / this workspace
- Method: hub cache (miss), then playbook (4 WebSearch, 0 WebFetch)

## Question

Compare Zod and Valibot: bundle size, API style, and when to pick each. Concrete bundle-size figures with source, the key API-style difference (chained schema methods vs modular pipe functions), and a one-line recommendation per library.

## Answer

For a typical login-form schema, Valibot bundles to ~1.37 kB while standard Zod needs ~17.7 kB with esbuild (~15.18 kB with Rolldown), a ~90% reduction; Zod's tree-shakable Zod Mini variant lands at ~6.88 kB (esbuild) / ~3.94 kB (Rolldown), still 3–5x larger than Valibot (valibot.dev comparison, with bundlejs measurements). Zod's own docs report Zod Mini at 2.12 kB gzip vs 5.91 kB for regular Zod on a small schema (64% reduction) and advise most users to stick with regular Zod unless bundle constraints are unusually strict. The API difference: Zod chains methods on schema objects (`z.string().email()`), while Valibot composes small standalone functions through `v.pipe(v.string(), v.email())` — each action is a separate tree-shakeable export, which is what enables the size gap. Recommendation: pick Zod for Node.js servers and ecosystem-heavy stacks (tRPC etc.) where a few kB is invisible and the fluent API and huge ecosystem win; pick Valibot for browser-shipped and edge/serverless code where bundle bytes and cold starts matter.

## Claims

- Login form: Zod 17.7 kB (esbuild) / 15.18 kB (Rolldown) vs Valibot 1.37 kB — ~90% smaller; Zod Mini 6.88 kB (esbuild) / 3.94 kB (Rolldown), still 3–5x Valibot — https://valibot.dev/guides/comparison/
- Zod's own numbers: Zod Mini 2.12 kB gzip vs Zod 5.91 kB on a simple schema (64% reduction); 4.0 kB vs 13.1 kB on a larger one — https://zod.dev/packages/mini
- Zod maintainer: "In general you should probably use regular Zod unless you have uncommonly strict constraints around bundle size" (~17 kB gzipped adds ~0.6 ms to Lambda cold start) — https://zod.dev/packages/mini
- API style: "In Zod, you chain methods like `.email`… In Valibot you use pipelines" (`v.pipe(v.string(), v.email())`) — https://valibot.dev/guides/migrate-from-zod/
- Valibot's modular design (small independent functions, no classes) enables tree-shaking of unused code, "up to 95%" smaller than Zod — https://valibot.dev/guides/introduction/
- Valibot maintainer (v1 announcement): individual bundle "between 1 and 2 kB for most users"; created explicitly to cut library bundle size >90% — https://valibot.dev/blog/valibot-v1-the-1-kb-schema-library
- Real Cloudflare Worker build: Zod 4.3.6 = 26.75 KiB gzipped vs Valibot 1.3.1 = 2.72 KiB (9.8x) for identical schema; Valibot team concedes Zod's ergonomics/ecosystem may matter more for warm long-lived services — https://valibot.dev/blog/dependency-size-and-cold-starts/
- Maintainer's original design writing: Zod's object-oriented/method API can't be tree-shaken; Valibot exports every functionality individually — https://www.builder.io/blog/valibot-bundle-size

## Hits

- Comparison guide — https://valibot.dev/guides/comparison/
- Zod Mini docs — https://zod.dev/packages/mini
- Migrate from Zod guide — https://valibot.dev/guides/migrate-from-zod/
- Valibot introduction — https://valibot.dev/guides/introduction/
- Valibot v1 announcement — https://valibot.dev/blog/valibot-v1-the-1-kb-schema-library
- Dependency size and cold starts — https://valibot.dev/blog/dependency-size-and-cold-starts/
- This technique makes Valibot's bundle 10x smaller than Zod's (Fabian Hiller, Builder.io) — https://www.builder.io/blog/valibot-bundle-size
- Introducing Valibot, a <1kb Zod Alternative (Fabian Hiller, Builder.io) — https://www.builder.io/blog/introducing-valibot

## Files

- none

## Lane

- docs

## Gaps

- All figures come from WebSearch snippets of the canonical pages (valibot.dev, zod.dev, builder.io); pages were not fetched. Snippets quoted the pages' own tables/links (bundlejs measurements), so citation confidence is high.
- Bundle figures are schema- and bundler-dependent; the valibot.dev comparison and zod.dev use different example schemas, so the numbers are not directly comparable to each other.
