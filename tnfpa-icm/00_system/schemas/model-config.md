# Model configuration (the EntityConfig contract inside K01 › Assumptions)

| field | rule (K01 › Checks) |
|---|---|
| name | text |
| start_month | a date on the 1st of a month (YYYY-MM) |
| horizon_months | integer 1–120 (openfpa allowed up to 120) |
| tax_rate | 0–1 (TN default 25.168% under s.115BAA; set 0 to bridge tax outside the engine) |
| da_monthly, capex_monthly | ≥ 0 |
| channels (1–8) | name non-empty, unique (case-insensitive), not `total`; annual_revenue ≥ 0; growth_rate > −100%; cogs_pct 0–1; exactly 12 seasonality weights (calendar Jan–Dec) with a positive sum |
| opex (0–15) | name unique, not `total`; kind fixed (monthly_amount) or variable (pct_of_revenue) |
| debt (0–5) | name unique; kind term_loan (monthly_principal) or loc (interest-only); opening_balance, annual_rate, monthly_principal ≥ 0 |
| working_capital | dso_days, dpo_days, dio_days ≥ 0 (30-day months) |
| opening_balances | cash, ar, ap, inventory; nol ≥ 0 |

A business that needs more slots or a different shape gets a company-specific workbook (operating contract).
Opening AR/AP/inventory should equal month-1 day-count-implied balances (W02 conventions).
