# Mapping rule (replaces `.fpa/mappings/registry.yaml`)

**File:** `memory/mappings/registry.csv`, sorted by (source_id, source_value). Header:
`source_id,source_value,target,status,rationale`

| column | rule |
|---|---|
| source_id | registered source, `^[a-z][a-z0-9-]*$` |
| source_value | exact account / field text as it appears in the source (trimmed) |
| target | normalised model target (e.g. `income_statement.revenue`, `opex.payroll`, `channels.dealer`, `balance_sheet.ar`) — required when mapped |
| status | mapped or ignored |
| rationale | required when ignored ("interest modelled in debt schedule", "GST control account – not P&L") |

(source_id, source_value) is unique. Never infer an unmapped account silently.
