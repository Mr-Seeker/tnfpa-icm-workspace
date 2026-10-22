# Formula reference — the kernel's maths in plain language

Use this to read the workbooks, to explain a number, and to build company-specific workbooks that
behave identically (replaces `pyfpa.excel.toolkit` and the module docstrings).

## Monthly engine (K01), per month m (1…horizon)
- `period_start = EDATE(start_month, m−1)`; `calendar_month = MONTH(period_start)`; `year_offset = INT((m−1)/12)`.
- Channel revenue = annual_revenue × weight[calendar_month] / Σ weights × (1 + growth_rate)^year_offset.
- Channel COGS = channel revenue × cogs_pct. Revenue/COGS totals = sums over channels.
- Gross profit = revenue − COGS. Fixed opex = monthly_amount; variable opex = total revenue × pct_of_revenue.
- EBITDA = gross profit − opex. D&A = da_monthly. Capex = capex_monthly.
- Debt k: opening-of-month balance B (month 1 = opening_balance); interest = B × annual_rate / 12;
  principal = MIN(monthly_principal, B) for term loans, 0 for LOC; closing = B − principal.
- Pre-tax = EBITDA − D&A − interest. Loss carryforward: used = MIN(opening NOL, MAX(0, pre-tax));
  tax = (MAX(0, pre-tax) − used) × tax_rate; NOL closing = opening − used (never grows).
- Net income = pre-tax − tax.
- AR = revenue × DSO/30; AP = COGS × DPO/30; Inventory = COGS × DIO/30.
  WC cash impact = −ΔAR + ΔAP − ΔInventory, month 1 versus opening balances.
- OCF = net income + D&A + WC impact; FCF = OCF − capex; change in cash = FCF − principal;
  ending cash = previous ending cash (month 1: opening cash) + change in cash.

## Scoring lines (K01 Summary → K04)
ending_cash = last month (stock); gross_margin = Σ gross profit / Σ revenue (ratio); every other line =
sum (flow). Actual periods aggregate the same way. Error = predicted/actual − 1 (signed).
Fitness = Σ (renormalised weight × |error|) over lines with a non-zero actual. Lower is better.

## 13-week cash (K02)
A flow hits week w if w ≤ weeks and: once → w = start; weekly → start ≤ w ≤ end; biweekly →
start ≤ w ≤ end and (w − start) even. End defaults to the horizon. Net = receipts − disbursements;
ending cash cumulative from opening cash. Trough = MIN; trough week = first week at the minimum;
first negative week = first week with ending cash < 0. No automatic financing.

## Research evaluation (K05)
See K05 README: per-metric improvement (direction-aware, zero-champion rule), regression guard on the
raw value, clamp ±1, weighted by weight/Σweights, minus complexity_penalty × max(0, Δcomplexity);
eligible = hard checks pass AND guard passes AND gain ≥ min_improvement.

## Building a company-specific workbook (toolkit conventions)
1. Sheets: `README`, `Assumptions` (named input cells, pale yellow), the calculation sheet(s) with one
   row per line and one column per period, `Summary`, `Checks`.
2. Every driver is a single named cell or a named row (e.g. `seasonality_ch1` = 12 cells). Formulas
   reference names, never typed numbers. Never paste computed values into formula cells.
3. Number formats: money `#,##0`, percent `0.0%`, days `0.0`; Indian grouping only in report sheets.
4. Use only the vocabulary in `00_system/no-code-policy.md`. If a function outside it seems necessary,
   restructure with helper rows instead.
5. Add parity rows in `Checks`: the bespoke workbook must reproduce the frame it is meant to reproduce
   (the K01 champion, or its quarterly/weekly aggregation) line by line and period by period, with a
   relative tolerance of 1e-6 (absolute below magnitude 1). A failing parity row means the workbook is
   wrong — fix the formulas, never the tolerance.
6. Register it in `memory/models/workflows.csv` with kind `report` (or forecast/close/cash/custom).
