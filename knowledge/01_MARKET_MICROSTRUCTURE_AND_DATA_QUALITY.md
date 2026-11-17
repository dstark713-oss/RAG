# Market microstructure finding: extreme moves in illiquid MOEX shares

Status: preliminary empirical observation from Research2 data-quality audit; not a validated trading edge.
Observed: 2026-11-18
Source project: https://github.com/dstark713-oss/research2

## Finding

During the 2005-2024 audit of MOEX daily share data, the audit identified 72 price changes of at least 50% between consecutive active observations. These are interval changes, not necessarily one-session returns: the gap between observations varies.

Follow-up review showed that some extreme observations are genuine market behavior, including sharp moves and pump-and-dump episodes in illiquid shares. They must not be automatically classified as bad data or removed solely because the magnitude is extreme or the number of trades is small.

User-confirmed examples from the audit:
- AFKS: genuine sharp market move; price rose into exchange price-limit bands.
- LPSB and USBN: genuine price moves in illiquid securities.
- GTRK and BLNG: genuine pump-and-dump episodes.
- Other illiquid names, including YUGK, were noted by the user as exhibiting similar behavior; individual events still require case-by-case review.

Separately confirmed corporate-action examples include VTBR and GMKN reverse/forward share-count adjustments. Such events must be distinguished from ordinary market moves and from data errors. Other unresolved cases remain unresolved until evidence is collected.

## Required classification discipline

For every extreme observation, distinguish:
1. **REAL_MARKET_MOVE** — a genuine market repricing or event-driven move.
2. **REAL_ILLIQUID_MOVE** — a genuine move in an illiquid instrument; the observed price may not represent executable size.
3. **CORPORATE_ACTION_CONFIRMED** — split, consolidation, distribution, or another share-count adjustment supported by evidence.
4. **UNRESOLVED** — insufficient evidence; retain the original data and continue review.
5. **DATA_ERROR_CONFIRMED** — use only when the source record or data construction is demonstrably wrong.

Do not infer a category for one ticker merely because another ticker behaves similarly. Preserve original raw observations and record annotations separately. Do not auto-correct prices, winsorize, or delete extreme returns just for being extreme.

## Interpretation limits

A valid exchange observation, a genuine trade, a representative market price, and an executable price for a meaningful position are different concepts. A low-trade-count print can be real while being economically unrepresentative for portfolio sizing or execution.

This finding does **not** establish:
- how prevalent these episodes are across the full MOEX universe;
- whether they are predictable ex ante;
- whether they offer exploitable alpha after spread, slippage, impact, and exit constraints;
- whether a backtest can realistically capture the displayed close-to-close return.

## Research implications

Treat illiquidity as both a data-interpretation issue and a market-risk dimension. Future research should examine event frequency, persistence/reversal, trading activity, price limits, stale observations, turnover, spreads where available, and realistic entry/exit capacity. Keep market-data validity, return validity, and strategy executability as separate audit dimensions.

Detailed raw data, scripts, anomaly registers, and audit outputs belong in Research2, not this RAG repository. Transfer only concise reusable findings here.
