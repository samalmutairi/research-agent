# Finding: Current Node.js LTS version and its end-of-life date

- Date: 2026-08-25
- Asked by: Agent X / this workspace
- Method: hub cache (miss, pre-checked by caller), then playbook (3 WebSearch, 0 WebFetch)

## Question

What is the current Node.js LTS version and its end-of-life date?

## Answer

The current Active LTS line is **Node.js 24.x, codename "Krypton"**, with a scheduled end-of-life of **2028-04-30**. It entered Active LTS on 2025-10-28 and moves to Maintenance LTS on 2026-10-20. Node.js 22.x "Jod" is still supported in Maintenance LTS (EOL 2027-04-30), and Node.js 26.x is Current, scheduled to become LTS on 2026-10-28 with EOL 2029-04-30. Confirmed by the official nodejs/Release schedule on GitHub and by nodejs.org (releases page and the v24.11.0 LTS announcement stating support "through to the end of April 2028").

## Claims

- Node.js 24.x "Krypton" is Active LTS; End-of-life 2028-04-30 (Active LTS start 2025-10-28, Maintenance start 2026-10-20) — https://github.com/nodejs/Release/blob/main/README.md
- nodejs.org lists v24 (Krypton) as LTS as of Aug 2026 — https://nodejs.org/en/about/previous-releases
- v24.11.0 marked the 24.x LTS transition; "will continue to receive updates through to the end of April 2028" — https://nodejs.org/en/blog/release/v24.11.0
- Node.js 22.x "Jod" is Maintenance LTS, EOL 2027-04-30; Node.js 26.x is Current, LTS start 2026-10-28, EOL 2029-04-30 — https://github.com/nodejs/Release/blob/main/README.md

## Hits

- nodejs/Release (official release schedule) — https://github.com/nodejs/Release/blob/main/README.md
- Node.js — Node.js Releases — https://nodejs.org/en/about/previous-releases
- Node.js — Node.js 24.11.0 (LTS) — https://nodejs.org/en/blog/release/v24.11.0
- Node.js — Evolving the Node.js Release Schedule (annual cadence from 27.x) — https://nodejs.org/en/blog/announcements/evolving-the-nodejs-release-schedule
- Node.js — End-Of-Life — https://nodejs.org/en/about/eol

## Files

- none

## Lane

- github + docs

## Gaps

- none — two primary sources (nodejs/Release schedule and nodejs.org) agree on version, codename, and EOL date.
