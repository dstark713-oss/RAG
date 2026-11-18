# Research2 — first portfolio risk-control screen

Date: 2026-11-19
Status: preliminary / no strategy accepted
Project: `dstark713-oss/research2`

## Scope

First exploratory run of portfolio risk-control hypotheses on a fixed basket of eight Russian common shares:

GAZP, LKOH, SBER, ROSN, GMKN, NVTK, MGNT, IRAO.

Source: `data/market_data/moex_daily_adjusted.sqlite`, table `adjusted_daily_bars`.
Observed common sample: 2014-06-09 — 2026-11-16, 3,128 observations.
Strategies screened: R01–R09, plus single-name Buy & Hold references and an equal-weight Buy & Hold reference.

This was a first implementation/screen, not a validated result. No strategy is approved for production or live allocation.

## Preliminary observations

- R06 Volatility Regime was the strongest portfolio strategy in the reported first screen: at 10 bps, CAGR 8.27%, Sharpe 0.534, MDD -39.18%, average exposure 88.6%, annualized turnover 1.29.
- R05 Drawdown Control showed the shallowest reported portfolio-strategy MDD: -32.67%, with CAGR 6.06%, Sharpe 0.476 and average exposure 65.0%.
- R07 Correlation Control produced CAGR 6.72%, Sharpe 0.473, MDD -41.88%, average exposure 80.5%.
- R03 Portfolio Volatility Target produced CAGR 6.12%, Sharpe 0.454, MDD -38.51%.
- At the reported 5 bps versus 10 bps runs, R06 metrics changed only modestly (CAGR 8.34% to 8.27%; Sharpe 0.538 to 0.534). This is only a preliminary cost-sensitivity indication, not a reliable cost conclusion until the execution/turnover accounting is corrected.
- Single-name Buy & Hold references varied widely. SBER had the highest CAGR (10.15%) but a very deep MDD (-73.81%). These are concentration references, not fair diversified benchmarks.

## Critical implementation caveats — results are not decision-grade

1. The current backtest engine charges turnover from changes in target weights rather than trades against drifted pre-trade holdings. This misstates actual turnover and transaction costs.
2. The equal-weight Buy & Hold baseline is represented by drifting weights but passed through an engine that treats weights as targets. It therefore incorrectly incurs trading/turnover costs. Implement passive holdings/shares separately.
3. R05's first implementation computes drawdown from the underlying equal-weight reference portfolio, not from the controlled strategy's own equity curve. It does not yet test a fully self-referential/adaptive drawdown-control strategy.
4. Initial price preparation forward-fills missing prices. Stale-price valuation and false zero returns need an explicit treatment before trusting results.
5. R04's volatility cap appears largely inactive for this basket/parameterization; inspect its cap logic and exposure behavior before interpreting its near-equality to R01.
6. Reported 5 and 10 bps runs are not a realistic MOEX execution model. Spread, slippage, market impact, liquidity and execution timing are not modeled.

## Interpretation and next research gates

- R06 is the leading candidate for forensic analysis, not a declared winner.
- R05 is a candidate for drawdown-risk research, but must first be redefined to use its own equity curve.
- R07 remains a useful distinct hypothesis: it adjusts total portfolio exposure based on average pairwise correlation, unlike R09 which redistributes weights within the basket.
- Do not tune parameters on this sample based on the observed ranking.
- Before further performance interpretation: repair holdings/drift-aware turnover and transaction-cost accounting; implement true Buy & Hold; then analyze R06 exposure timing and subperiod behavior.
- No conclusion about durable alpha, out-of-sample robustness, or live applicability has been established.

## Provenance

User-reported local run output in the 2026-11-19 conversation. The assistant did not execute the local scripts and has not independently inspected the generated CSVs. Reported metrics are treated as provisional observations, not independently verified facts.
