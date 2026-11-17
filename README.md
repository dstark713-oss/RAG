# RAG — persistent research memory for AI Trader

This repository is the durable, curated research memory for the AI trading experiment. It is separate from the production trading-system repository (`dstark713-oss/model1`) and the quantitative research/data-engineering repository (`dstark713-oss/research2`).

## Purpose
Store retrievable, auditable context for future research sessions:
- project mandate, role boundaries, and user-approved constraints;
- canonical, reusable research findings and methodology;
- dated model/system state, evidence snapshots, and decisions;
- issuer fundamentals, corporate events, valuation, and narrative risk;
- reusable research templates.

## Rules
1. Point-in-time correctness: only use information publicly available by the decision timestamp.
2. Provenance: every material fact needs source, publication date, retrieval date, and report period where applicable.
3. Distinguish reported facts, calculations, third-party estimates, interpretations, hypotheses, and unknowns.
4. Keep dated snapshots; do not silently overwrite old conclusions.
5. Never describe backtest results as live performance.
6. Do not modify the strategy or its parameters without explicit user approval.
7. This repository is external memory, not model training. Future sessions must retrieve relevant files; nothing is automatically loaded into model weights.
8. Do not store credentials, API keys, broker secrets, raw datasets, bulky logs, or unnecessary personal data.

## Structure
- `context/` — project mandate, roles, constraints, operating protocol.
- `knowledge/` — compact canonical memory and reusable findings.
- `research/` — dated research notes and market context.
- `issuers/<TICKER>/` — durable issuer dossiers and dated updates when needed.
- `decisions/` — dated allocation proposals and decision history.
- `methodology/` — point-in-time, evidence, and risk-review standards.
- `templates/` — reusable research templates.

Detailed raw data, scripts, anomaly registers, and full audit outputs belong in `research2`; only concise findings that can guide future research should be copied here.

## Retrieval protocol
At the start of a relevant session:
1. Read this README, `context/PROJECT_MANDATE.md`, and `context/RESEARCH_OPERATING_PROTOCOL.md`.
2. Read the relevant canonical files in `knowledge/`.
3. Retrieve the latest applicable dated system-state, research, and decision files; check for later corrections or superseding decisions.
4. Use methodology and templates when designing or auditing research.
5. Cite repository paths in conclusions. If evidence is incomplete, say what is missing rather than inventing it.

Canonical knowledge is the compact starting point; dated files preserve provenance and decision history. Do not load every historical note by default.

Initialized 2026-11-17. The first issuer screen and 2026-11-17 allocation documents are dated research snapshots, not a complete comparable fundamental database or a standing portfolio instruction.
