# Fox Factory (FOXF) — public-company proof, rebuilt without code

openfpa's real-data example on **Fox Factory Holding Corp.** (NASDAQ: FOXF, SEC CIK 1424929), using only public
SEC filings, converted into a company workspace with workbooks instead of Python. It separates accounting
reproduction from independent historical validation, exactly as openfpa did. Currency USD; fiscal year ≈ calendar.

| Phase | Files | Result (verified equal to openfpa's published outputs) |
|---|---|---|
| A · actual-driver reproduction | `models/phaseA_FY2024.xlsx`, `phaseA_FY2025.xlsx`, `output/reconciliation.md` | net sales, gross profit, Adjusted EBITDA, D&A, capex, OCF-before-tax tie within 1% (FY2024 $1,393.9M sales; FY2025 $1,467.3M) |
| B · FY2025 holdout research | `models/phaseB_*.xlsx`, `memory/research/`, `output/historical-holdout.md` | epoch 001 discarded (gain +5.5%, regression guard fails), epoch 002 proposed (+61.4%), not promoted |
| C · forward forecast | `models/phaseC_*.xlsx`, `output/forecast-briefing.md` | FY2026 $1,520.5M sales / $236.7M Adj EBITDA / $114.2M FCF; FY2027 $1,576.2M / $250.3M / $125.4M |
| D · Marucci divestiture | `models/phaseD_K08_marucci.xlsx`, `output/divestiture.md` | hold $239.6M 2-yr FCF at 2.09x; sell at 6/12/18/24 months; at-cost / 8x / 12x proceeds → net cash |

## Where the engine strains (surfaced, not hidden — unchanged from openfpa)
1. No segment layer in the base engine → generated `segment-rollup` skill + K07.
2. The $557M FY2025 goodwill impairment (non-cash) → documented bridge, not forced through the engine.
3. Discrete tax benefits → bridged, not reconciled.
4. Marucci is not disclosed standalone → Phase D is a labelled sensitivity anchored to the $567M acquisition.
5. Monthly engine vs quarterly reporting → annual resolution anchored to Q1.
6. Three annual observations demonstrate discipline, not statistical certainty.

Run order and recipes: `models/pipeline-runbook.md`. Memory: `memory/` (converted from openfpa `.fpa/`).
