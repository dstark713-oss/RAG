# RAG — operational knowledge base for AI Trader

This repository exists exclusively for the AI trading agent. It is the agent's readable operating manual, compact knowledge base, tool directory, and dated decision record. It is not a general assistant memory, research archive, chat archive, or workspace for the user's and assistant's ongoing R&D.

## Sole purpose

Help the trading agent make better practical allocation decisions. Every stored item must help the agent do at least one of the following:
- understand its mandate, authority, constraints, and decision process;
- identify which available tool, script, data source, or research procedure to run for a concrete decision question;
- understand what an existing tool measures, how to invoke it, and its known limitations;
- apply established market, issuer, liquidity, risk, and portfolio knowledge;
- distinguish evidence strength and point-in-time validity;
- construct, explain, review, and learn from actual allocation decisions.

If information cannot change, validate, constrain, or explain a practical agent action, it does not belong here.

## Explicit exclusions

Do not store:
- the assistant's personal memory, preferences, or notes about how to continue research conversations;
- EDA plans, sprint plans, experiment queues, speculative research ideas, or unvalidated model-development notes;
- raw research results that have not been translated into a decision-relevant operational finding;
- research journals, code-development history, debugging transcripts, or duplicated project documentation;
- information included merely to help the assistant remember work that belongs in another repository.

Research projects keep their complete journals, data, scripts, audits, and experiment results in their own `researchN` repositories. A result may enter this RAG only after it has a clear practical implication for the trading agent, with evidence, limitations, and instructions for use.

## Repository boundaries

- `dstark713-oss/RAG` — only the trading agent's operational instructions, tool knowledge, validated decision-relevant knowledge, issuer/event evidence needed for allocation, and dated allocation decisions.
- `dstark713-oss/model1` — production/pilot model, scripts, configuration, and artifacts. Do not change its logic or parameters without explicit approval.
- `dstark713-oss/research`, `research2`, and future `researchN` repositories — research journals, datasets, code, experiments, diagnostics, and full evidence trails. They are not agent memory.

## Admission test

Before adding or retaining a file, ask:
1. Can the agent understand it without access to the original chat?
2. Does it tell the agent what to do, what tool to run, what a result means, or what constraint to respect when allocating?
3. Is the information current or clearly dated, sourced, and qualified?
4. Is it concise enough to retrieve at decision time?
5. Is its detailed source of truth preserved in the appropriate project repository?

If the answer to the practical-use question is no, keep it in the research repository, not here.

## Core rules

1. Point-in-time correctness: use only information public by the decision timestamp.
2. Provenance: preserve source, publisher, publication date, retrieval date, and report period where applicable.
3. Distinguish reported facts, calculations, estimates, interpretations, hypotheses, and unknowns.
4. Never describe backtest results as live performance.
5. Never change production strategy rules without explicit user approval.
6. Never claim an order, script, or local action was executed without confirmation.
7. Do not store credentials, broker secrets, raw datasets, bulky logs, or unnecessary personal information.
8. Keep dated decisions as history; never treat an expired target allocation as a standing instruction.

## Structure

- `context/` — agent mandate, operating instructions, authority, and current workflow.
- `knowledge/` — concise, reusable decision rules, tool descriptions, and established market knowledge.
- `research/` — only dated evidence notes with a direct, current allocation or risk-review use.
- `issuers/<TICKER>/` — issuer facts, events, risks, and dated updates relevant to candidate evaluation.
- `decisions/` — dated allocation proposals, final decisions, and outcome reviews.
- `methodology/` — operational standards the agent applies when evaluating evidence and risk.
- `templates/` — reusable formats for issuer reviews and allocation work.

## Retrieval protocol

At the start of an allocation session:
1. Read `context/PROJECT_MANDATE.md`, `context/RESEARCH_OPERATING_PROTOCOL.md`, and `context/DAILY_AGENT_INSTRUCTIONS.md`.
2. Read relevant canonical files in `knowledge/` and the tool documentation needed for the current question.
3. Retrieve the latest applicable model/system state, issuer/event evidence, and allocation decision. Check for corrections or superseding records.
4. Run only tools that answer a concrete decision question; do not execute a research program merely because it exists elsewhere.
5. Cite the relevant RAG paths and primary sources in the decision. State missing evidence instead of inventing it.

Initialized 2026-11-17. Repository scope clarified on 2026-11-20: this is exclusively the trading agent's practical knowledge base.
