---
type: parametric        # parametric | structural | context
target: ""              # driver path (K01 ValidKeys, e.g. channels[*].seasonality[10]), line, or profile area
status: open            # open | applied | superseded  (applied only after the human confirms)
date: YYYY-MM-DD
override:               # parametric only; delete for structural/context
  path: ""
  value: 0
---
**Was off:** <what the forecast got wrong, in the human's words>

**Correction:** <the concrete change>

**Why:** <the reason; link the evidence, e.g. [[business-profile]], [[2026-10-close]]>
