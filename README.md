# RAG — persistent research memory for AI Trader

This repository is the durable research memory for the AI trading experiment. It is separate from the production trading-system repository (`dstark713-oss/model1`).

## Purpose
Store retrievable, auditable context for future research sessions:
- project mandate, role boundaries, and user-approved constraints;
- model/system state and dated signals;
- issuer fundamentals, corporate events, valuation, and narrative risk;
- allocation proposals, vetoes, post-trade reviews, and lessons;
- methodology and reusable research templates.

## Rules
1. Point-in-time correctness: only use information publicly available by the decision timestamp.
2. Provenance: every material fact needs source, publication date, retrieval date, and report period where applicable.
3. Distinguish reported facts, calculations, third-party estimates, interpretations, hypotheses, and unknowns.
4. Keep dated snapshots; do not silently overwrite old conclusions.
5. Never describe backtest results as live performance.
6. Do not modify the strategy or its parameters without explicit user approval.
7. This repository is external memory, not model training. Future sessions must retrieve relevant files; nothing is automatically loaded into model weights.
8. Do not store credentials, API keys, broker secrets, or unnecessary personal data.

## Structure
- `context/` — project mandate, roles, constraints, current system state.
- `research/` — dated research notes and market context.
- `issuers/<TICKER>/` — durable issuer dossiers and dated updates.
- `decisions/` — allocation proposals and decision log.
- `methodology/` — point-in-time, evidence, and risk-review standards.
- `templates/` — reusable templates.

## Retrieval protocol
At the start of a relevant session, retrieve this README, the project mandate, latest system state, and the exact dated research/decision files. Check for later corrections. Cite repository paths in conclusions. If evidence is incomplete, say what is missing rather than inventing it.

Initialized 2026-11-17. The first issuer screen is preliminary, not a complete comparable fundamental database or a final portfolio allocation.
