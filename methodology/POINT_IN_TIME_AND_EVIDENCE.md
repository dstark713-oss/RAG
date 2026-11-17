# Point-in-time and evidence standards

## Required dates
For every observation, distinguish:
- `period_start`, `period_end`: period described;
- `published_at`: when information became public;
- `retrieved_at`: when captured;
- `as_of_date`: decision date.

A report is eligible for a historical decision only if public by that decision timestamp. Period end is not publication date. Example: 9M26 results published 2026-11-25 cannot inform a 2026-11-17 decision.

## Evidence classes
Label every material statement:
1. Reported fact — issuer filing/release, audited report, regulator, exchange, rating agency.
2. Calculated metric — show formula and input sources/dates.
3. Third-party estimate — provider, date, methodology caveat.
4. Interpretation — analytical reading, not a reported fact.
5. Hypothesis / unverified claim — requires evidence.
6. Unknown / unavailable — not found or not checked.

Attribute company allegations to the company; do not state them as independently verified facts.

## Source hierarchy
Prefer issuer IR and reports; official disclosure and exchange filings; regulators and rating agencies; reputable newswires for chronology; aggregators for discovery/cross-check only. Store direct URLs, source title, publisher, publication date, retrieval date, and the claim supported.

## Comparability
Align period, currency, units, accounting standard, reported vs adjusted, trailing vs forecast, price date and share count. Do not mix stale prices with current statements without flagging it.

Sector metrics:
- Banks: ROE, NIM, cost of risk, NPL/Stage 3, coverage, capital adequacy, loan growth, funding.
- Insurers: underwriting result, combined ratio, investment result, solvency, reserve quality.
- Utilities: tariffs/RAB, capex, debt, cash flow, receivables, dividend constraints.
- Retail: LFL, gross margin, EBITDA margin, net debt/EBITDA, working capital.
- IT/software: recurring revenue, retention, bookings, cash conversion, capitalized development costs.
- Pharma: product mix, pipeline, registrations, capacity, pricing/regulation.
- Metals/mining: realized prices, volumes, cash costs, capex, net debt, cycle sensitivity.
- Food/agro: volumes, input costs, biological-asset accounting, working capital, export access.

## Contradictions and audit
Keep conflicting values with source/date; do not silently select one. Missing data is not evidence of safety. Low P/E/PB or high dividend yield alone does not establish undervaluation or sustainability. A high model score does not override credit, liquidity, governance, or corporate-event risk.

Every dated note records as-of date, ticker/issuer, sources/publication dates, facts/calculations, interpretation, risks, verdict/confidence, missing evidence, and what would change the verdict. Updates create new dated files and reference prior notes.
