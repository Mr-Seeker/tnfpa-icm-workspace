---
metrics:
  - {name: ending_cash_error, weight: 0.4, direction: lower}
  - {name: ebitda_error, weight: 0.3, direction: lower}
  - {name: revenue_error, weight: 0.2, direction: lower}
  - {name: gross_margin_error, weight: 0.1, direction: lower}
hard_checks: [source reconciliation, accounting invariants, holdout separation]
min_improvement: 0.02
complexity_penalty: 0.01
max_metric_regression:
---
# Research objective
openfpa defaults. The CFO owns this file: re-weight metrics by decision importance (e.g. raise
ending_cash_error for a company living inside its cash-credit limit).
