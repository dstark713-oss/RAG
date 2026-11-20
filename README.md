# RAG — operational knowledge base for AI Trader

A compact, agent-readable operating manual, validated decision-relevant knowledge base and dated decision ledger. It is not a general assistant memory, chat archive, research journal or development workspace.

## Admission rule

Keep an item only if it can change, validate, constrain or explain a practical allocation/risk action. Every retained item must be understandable without the original chat, dated/sourced where necessary, and concise. Detailed source-of-truth material belongs in the relevant project repository.

Do not store personal chat memory, research backlogs, EDA plans, debugging history, raw datasets, bulky logs, credentials or duplicated project documentation.

## Repository boundaries

- `RAG`: mandate, operating process, tool limitations, validated decision-relevant knowledge, issuer/event evidence and dated allocation decisions.
- `model1`: production/pilot model, code, configuration and artifacts. No unapproved changes.
- `research`, `research2`, future `researchN`: research journals, data, code, experiments, diagnostics and full evidence trails.

## Core rules

1. Respect point-in-time publication timestamps.
2. Preserve source, publisher, publication date, retrieval/as-of date and report period where applicable.
3. Distinguish reported facts, calculations, estimates, interpretations, hypotheses and unknowns.
4. Never describe backtest results as live performance.
5. Never claim an order, script or local action was executed without confirmation.
6. Dated decisions are immutable history, not standing allocations.
7. Keep model1 and the assistant's discretionary portfolio separate.

## Structure

- `context/PROJECT_MANDATE.md`: compact mandate, authority and system boundaries.
- `context/DAILY_AGENT_INSTRUCTIONS.md`: current operational workflow, evidence discipline, tool limitations and current decision pointer.
- `knowledge/`: concise reusable findings with practical allocation/risk implications.
- `methodology/POINT_IN_TIME_AND_EVIDENCE.md`: evidence and temporal-validity standard.
- `research/`: dated evidence notes only when directly relevant to current allocation/risk review.
- `decisions/`: dated proposals, final allocations and outcome reviews; historical records are not overwritten.
- `templates/`: reusable issuer-review format.

## Retrieval protocol

At the start of an allocation session:
1. Read `context/PROJECT_MANDATE.md` and `context/DAILY_AGENT_INSTRUCTIONS.md`.
2. Read the latest final decision and only the relevant knowledge, issuer/event notes and tool documentation.
3. Check whether later corrections or decisions supersede earlier context.
4. Retrieve fresh signal, prices, breadth and user-confirmed holdings/fills. Check each data field's timestamp and universe.
5. Run tools only to resolve a concrete decision question; request/build targeted diagnostics when needed.
6. Cite RAG paths and primary sources in the decision. State missing evidence rather than inventing it.

Initialized 2026-11-17. Scope and curation rules clarified 2026-11-20.
