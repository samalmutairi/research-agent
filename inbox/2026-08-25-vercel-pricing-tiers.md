# Finding: Vercel pricing tiers (names and monthly prices)

- Date: 2026-08-25
- Asked by: Agent X / this workspace
- Method: hub cache (miss, pre-checked), then playbook (3 WebSearch, 0 WebFetch)

## Question

Find the pricing tiers currently listed on Vercel's pricing page (tier names and monthly prices).

## Answer

Vercel's pricing page lists exactly three tiers: Hobby at $0/mo, Pro at $20/mo, and Enterprise at custom pricing. The Pro price is a $20/month platform fee that includes one deploying team seat and $20/month in usage credit; additional deploying seats (Owner/Member roles) are $20/month each, while Viewer seats are free. Hobby is free and restricted to personal, non-commercial use. Enterprise has no published price ("Custom"); it is negotiated with sales. These values were read from the static text of vercel.com/pricing itself (returned in full by search, tier table verified verbatim) and corroborated by Vercel's own plan docs.

## Claims

- Pricing page plan table: Hobby $0/mo., Pro $20/mo., Enterprise Custom — https://vercel.com/pricing
- Vercel offers three account plans: Hobby, Pro, and Enterprise — https://vercel.com/docs/plans
- Pro platform fee is $20/month with 1 deploying seat and $20/month usage credit; extra Owner/Member seats $20/month each — https://vercel.com/docs/plans/pro-plan
- Hobby plan is free, for personal projects — https://vercel.com/docs/plans/hobby
- Enterprise is custom-priced; contact sales — https://vercel.com/pricing

## Hits

- Pricing — https://vercel.com/pricing
- Plans — https://vercel.com/docs/plans
- Pro plan — https://vercel.com/docs/plans/pro-plan
- Hobby plan — https://vercel.com/docs/plans/hobby
- Pricing docs (resource rates) — https://vercel.com/docs/pricing
- New Pro pricing plan (credit model announcement) — https://vercel.com/blog/new-pro-pricing-plan

## Files

- none

## Lane

- docs (+ changelog/recency)

## Gaps

- None material: despite the JS-rendering concern, WebSearch returned the full static text of vercel.com/pricing, and the tier table (Hobby $0/mo., Pro $20/mo., Enterprise Custom) was verified verbatim from that first-party page text, not from memory or third-party blogs.
- Enterprise has no published price on vercel.com; third-party estimates (~$3,000–3,500/mo entry) were NOT verified against any first-party source and are excluded from the answer.
