# Fox Factory pipeline runbook (replaces `pull_edgar.py`, `foxf_model.py`, `run_foxf.py`)

1. **Pull actuals (recipe, no code):** for each concept listed in `data/raw/SOURCES.md` open
   `https://data.sec.gov/api/xbrl/companyconcept/CIK0001424929/us-gaap/<TAG>.json` in a browser (SEC asks for a
   descriptive User-Agent — a normal browser session is fine), read the FY values for the listed accessions, and
   transcribe them into `data/raw/income_statement.csv`, `balance_sheet.csv`, `cash_flow.csv`; segment figures come
   from the FY2025 10-K segment footnote (R106), Q1 prints from the latest 10-Q. Record the date in
   `memory/sources/registry.csv` (refreshed_at). The committed CSVs are the values openfpa pulled.
2. **Phase A — actual-driver reproduction:** `phaseA_FY2024.xlsx`, `phaseA_FY2025.xlsx` (K01 copies). Drivers:
   segment net sales as channels (flat seasonality, blended COGS% = cost of sales / net sales), one fixed
   `adjusted_opex` = (gross profit − total segment Adjusted EBITDA)/12, term loan sized as interest / 7% at 7%,
   WC days = balance / flow × 360, opening balances = prior year-end, D&A and capex /12, tax 0. GOLDEN checks tie
   net sales, gross profit, Adjusted EBITDA, D&A, capex and OCF-before-tax to reported within 1%.
   Narrative and the impairment/discrete-tax bridge: `output/reconciliation.md`.
3. **Phase B — FY2025 holdout research:** three K01 candidates fitted on FY2023–FY2024 only
   (`phaseB_champion-flat-fy2024.xlsx`, `phaseB_ch1-broad-mean-reversion.xlsx` (50%/50%),
   `phaseB_ch2-slow-margin-recovery.xlsx` (50% revenue / 5% margin reversion)). Paste their predictions into
   `phaseB_holdout-metrics.xlsx`; copy the four metrics into `phaseB_K05_epochs.xlsx`. Result: epoch 001
   discarded (Adjusted-EBITDA error 1.0% → 20.4%, regression guard fails), epoch 002 proposed (objective gain
   +61.4%, all hard checks pass) and **not promoted** pending human approval. Narrative: `output/historical-holdout.md`.
4. **Phase C — FY2026–FY2027 forecast:** `phaseC_K07_segments.xlsx` grows FY2025 segments (FY2026 anchored to
   the Q1 FY2026 print +3.8% YoY); `phaseC_FY2026.xlsx` and `phaseC_FY2027.xlsx` (FY2027 opens from FY2026
   modelled closing cash/AR/AP/inventory; debt amortises $25M/yr at 8%). GOLDEN checks equal `output/forecast-briefing.md`.
5. **Phase D — Marucci divestiture sensitivity:** paste the 24 months of Phase C Export_Rows into
   `phaseD_K08_marucci.xlsx` (already done); carve-out = $300M sales, 50% gross margin, 25% EBITDA margin,
   $22M D&A, $5M capex per year; proceeds retire debt at 8%. Grid reproduces `output/divestiture.md`
   (hold $239.6M / 2.09x … sell at 24 months $239.6M / 0.89x; at-cost, 8x and 12x proceeds → net cash).
