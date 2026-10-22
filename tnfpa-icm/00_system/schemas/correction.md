# Correction (same shape as openfpa)

**File:** `memory/corrections/<slug>.md`, slug = `<YYYY-MM-DD>-<short-name>` (the whole slug is the filename).

```markdown
---
type: parametric        # parametric | structural | context
target: channels[*].seasonality[10]   # driver path, line, or profile area
status: open            # open | applied | superseded
date: 2026-11-02
override:               # parametric only
  path: channels[*].seasonality[10]
  value: 1.9
---
**Was off:** November forecast ignored the Deepavali dealer pre-buy.
**Correction:** November seasonality weight 1.9 on all channels.
**Why:** dealers stock up 3–4 weeks before Deepavali; see [[business-profile]] and [[2026-10 close]].
```

Rules: override paths use openfpa syntax (`name`, `name[n]` 0-based, `name[*]`) over the keys listed in
K01 › ValidKeys; only `applied` + `parametric` corrections change the model (K01 › Corrections).
`structural` → W12 (pre-ratified skill/model change). `context` → W00 one-time screen. Status changes are
reversible; the backtest may *flag* an applied correction as stale but never reverts it.
