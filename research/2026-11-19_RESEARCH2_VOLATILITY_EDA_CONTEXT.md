# Research2 — volatility EDA and forecasting context

Date: 2026-11-19
Status: active research context; EDA not yet executed
Project: `dstark713-oss/research2`
Source of detailed plan and implementation history: `daily_report.txt` and project code/data.

## 1. Current data foundation

The current adjusted daily database contains 727,840 rows across 417 common-share securities, covering 1997-03-24 through 2026-11-16. The historical universe was reconstructed from MOEX ISS rather than selected from today's surviving names. Approved boards are TQBR and EQBR; preferred shares and non-share instruments are excluded from the research universe.

Primary research source: `data/market_data/moex_daily_adjusted.sqlite`. Raw source: `data/market_data/moex_daily_raw.sqlite`; raw data is immutable. Corporate-action adjustments are applied in the adjusted database. The project retains genuine extreme market moves and does not automatically forward-fill, winsorize, or delete observations merely because they are unusual.

These counts and dates describe the current database snapshot, not an assertion that every ticker has continuous coverage or that all panel rows are independent.

## 2. Active question

The next research block is an exploratory, data-science-first study of the dataset for volatility forecasting. Begin as if the data were an unfamiliar panel dataset with a stated forecasting task; do not assume financial-market structure beyond what is established by schema inspection and empirical analysis. Include volume and other available activity variables from the beginning.

Candidate binary targets under consideration:
- FAST: volatility increase over the next 5 trading observations.
- SLOW: volatility increase over the next 20 trading observations.

The target definitions are not frozen. EDA must examine the distribution and stability of future changes in realized volatility and compare economically interpretable thresholds before selecting labels. Do not select a threshold based on downstream trading performance.

The forecast is about volatility/risk, not return direction. Its potential value as an information layer for an AI decision-maker is a separate question from whether it can support a profitable standalone trading strategy. Direct tradability is unproven and is not the premise of the current EDA.

## 3. EDA sequence

The project journal contains the detailed approved EDA plan. Its sequence is:

1. Data structure and coverage.
2. Univariate distributions.
3. Temporal dependence.
4. Scale and distribution dynamics.
5. Cross-sectional structure.
6. Volume and joint dynamics.
7. Non-stationarity and stability.
8. Target exploration, only after the preceding blocks.

The first pass is a data profile and distribution audit. Inspect the actual SQL schema before assuming field names or availability. Treat volume, traded value, and number of trades as distinct measures. Decompose within-security and between-security variation; do not treat 727k panel rows as IID observations. Missing dates can reflect listing history or suspensions rather than corrupt records.

Use the full available historical universe for descriptive EDA initially. A liquidity-filtered universe may be justified for a later economic/portfolio question, but should not silently constrain discovery at the start.

## 4. Methodological constraints

- Preserve point-in-time causality. Features at date t may use only information available by t; future labels must use observations strictly after t.
- For 5D/20D labels, account for overlapping future windows when constructing validation folds. Use chronological walk-forward validation with purging/embargo; never random train/test splitting.
- Separate within-security time dependence, common market shocks, and cross-sectional dependence.
- Report class prevalence, per-security differences, temporal stability, and missingness patterns. Aggregate metrics alone can conceal panel composition effects.
- Do not remove genuine extreme returns simply because they distort plots or summary statistics. Distinguish real market events, illiquid prints, corporate actions, unresolved cases, and confirmed data errors.
- Do not tune target definitions against model or portfolio outcomes.
- No model or portfolio experiment should be inferred from EDA findings without a separate explicit research gate.

## 5. Relevant prior evidence and caveats

### Research1
Research1's stock-selection model failed on its validation period despite attractive in-sample results. Survivorship bias, illiquid names, unstable alpha, turnover, costs, and corrected calculation bugs were material lessons. Its earlier PCA and K-Means work already exists; these are not novel methods for Research2. They may be re-evaluated on the improved historical universe, but prior Research1 results must not be treated as validated facts about the current dataset.

### Research2 risk-control screen
The first R01-R09 portfolio risk-control screen is documented in `research/2026-11-19_RESEARCH2_RISK_CONTROL_FIRST_SCREEN.md`. Subsequent R06 diagnostics suggested that its volatility-regime ratio contains information about future volatility and drawdown, but not future return direction. Placebo results were not uniformly significant and subperiod behavior was unstable. R06 remains RESTRICTED / exploratory, not a validated universal overlay. Do not keep tuning it as part of the volatility EDA sprint.

## 6. Repository boundaries

- Research2 owns the detailed data, scripts, experiment outputs, audits, and EDA journal.
- RAG stores only this compact context and durable findings useful to future reasoning.
- model1 remains the separate pilot/production system. Research2 results do not authorize changes to model1 or its trading rules.

## Provenance

Compiled from the Research2 project journal and user-confirmed project decisions available on 2026-11-19. The assistant did not execute the EDA or independently rerun the local database audits. This note records project state and methodological constraints, not new empirical findings.
