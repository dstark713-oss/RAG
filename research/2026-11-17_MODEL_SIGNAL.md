# Model signal — 2026-11-17
As-of date: 2026-11-17  
Model version: `v_2026-11-17`  
Regime: stocks; regime observation date 2026-11-16 (IMOEX data lagged one session). Signal date follows latest TOP100/prices date.

## Selected portfolio
| Rank | Ticker | p_tp | p_sl | score | weight |
|---:|---|---:|---:|---:|---:|
| 1 | MGKL | 0.3506 | 0.0500 | 0.3331 | 0.1894 |
| 2 | MSNG | 0.5942 | 0.4662 | 0.3172 | 0.1894 |
| 3 | BSPB | 0.3506 | 0.2224 | 0.2726 | 0.1894 |
| 4 | ASTR | 0.4800 | 0.4662 | 0.2562 | 0.1894 |

Cash 0.2424; exposure 0.7576. Score = `p_tp * (1 - p_sl)`, a ranking statistic, not a probability of positive return.

## Candidate ranking
| Rank | Ticker | Score | Selected |
|---:|---|---:|---|
|1|MGKL|0.3331|yes|
|2|MSNG|0.3172|yes|
|3|BSPB|0.2726|yes|
|4|ASTR|0.2562|yes|
|5|MTLR|0.2357|no|
|6|GCHE|0.2179|no|
|7|OZPH|0.2161|no|
|8|T|0.2110|no|
|9|MSRS|0.2084|no|
|10|DIAS|0.2021|no|
|11|AQUA|0.1967|no|
|12|X5|0.1903|no|
|13|RENI|0.1793|no|
|14|TGKN|0.1786|no|
|15|MRKZ|0.1778|no|

Universe scored 96; threshold passed 96; selected 4; threshold 0.0000.

## Inspection caveats
User ran `tools/inspect_signal.py` for these 15 names. Raw probabilities differed; calibrated probabilities repeated due to piecewise-constant isotonic mapping, not identical feature vectors. No identical feature_hash among inspected names. Maximum absolute 20-session correlation among these 15 was below 0.8 (largest noted X5/TGKN +0.7168). This does not prove the full 96-name greedy selection path; do not infer why all other candidates were excluded without reproducing it.

Signal-date bug was corrected: signal date now follows latest TOP100 date; regime uses latest IMOEX observation <= signal date and reports `regime_date`.
