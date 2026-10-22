---
label: ""               # period or cycle, e.g. 2026-10 or LE-Oct-FY2026-27
created: YYYY-MM-DD     # supplied, never invented
assumptions: forecasts/<label>.assumptions.xlsx
predicted:              # from K01 › Summary snapshot block
  ending_cash: 0
  ebitda: 0
  revenue: 0
  gross_margin: 0
# score:                # add once after close (K04 › Score); never edit predicted afterwards
#   fitness: 0
#   per_line: {ending_cash: 0, ebitda: 0, revenue: 0, gross_margin: 0}
#   weights: {ending_cash: 0.4, ebitda: 0.3, revenue: 0.2, gross_margin: 0.1}
---
Posture: plan | latest estimate | run-rate. Caveats (W00):
