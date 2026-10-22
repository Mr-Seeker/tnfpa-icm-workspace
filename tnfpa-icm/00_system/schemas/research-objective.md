# Research objective (replaces `.fpa/research/objective.yaml`)

**File:** `memory/research/objective.md` with frontmatter:

```yaml
metrics:                 # unique names, weight > 0, direction lower|higher
  - {name: ending_cash_error, weight: 0.4, direction: lower}
  - {name: ebitda_error, weight: 0.3, direction: lower}
  - {name: revenue_error, weight: 0.2, direction: lower}
  - {name: gross_margin_error, weight: 0.1, direction: lower}
hard_checks: [source reconciliation, accounting invariants, holdout separation]   # unique
min_improvement: 0.02    # >= 0
complexity_penalty: 0.01 # >= 0
max_metric_regression:   # > 0 or blank (off)
```

These are the openfpa defaults written by `init`. The company owns its objective; K05 › Objective mirrors it.
