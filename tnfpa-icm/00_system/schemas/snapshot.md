# Forecast snapshot (replaces `.fpa/forecasts/<period>.snapshot.yaml`)

**Files:** `memory/forecasts/<label>.snapshot.md` (record) and `memory/forecasts/<label>.assumptions.xlsx`
(an untouched copy of the K01 workbook that produced it = the serialised assumptions).

```markdown
---
label: 2026-10
created: 2026-10-05          # supplied by you; never invented
assumptions: forecasts/2026-10.assumptions.xlsx
predicted:                   # K01 › Summary snapshot block
  ending_cash: 18234567.0
  ebitda: 9876543.0
  revenue: 123456789.0
  gross_margin: 0.3912
score:                       # add after close (K04 › Score); omit until then
  fitness: 0.0412
  per_line: {ending_cash: 0.031, ebitda: -0.072, revenue: 0.012, gross_margin: -0.004}
  weights: {ending_cash: 0.4, ebitda: 0.3, revenue: 0.2, gross_margin: 0.1}
---
Notes: posture used (plan / latest estimate / run-rate), caveats, links to the close narrative.
```

Snapshots are immutable except for adding `score` once. Missing or zero actuals → no score.
