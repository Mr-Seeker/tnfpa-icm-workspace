---
schema_version: 1
name: ""                     # = folder name
source_id: ""                # registered in memory/sources/registry.csv
description: ""
auth_method: none            # none | host_environment | mcp  (no credentials stored here)
source_account_column: Account
source_amount_column: Amount
fixture_path: fixtures/source.csv
fixture_procedure: "K03 Reconcile with tolerance 0; expected = expected_totals; fixture mode only"
expected_totals: {}          # golden mapped totals from the scaffold reconciliation
live_ready: false
live_recipe: ""
---
## Export recipe
<exact clicks or the approved MCP call; who performs it; how often; where the file is saved>

## Normalisation
<columns kept, sign convention, Dr/Cr handling, units (full rupees), GST inclusive/exclusive>

## Failure behaviour
Missing file → stop and ask. Duplicate account → FAIL. Unmapped account → FAIL (map or ignore with rationale).
Golden-total mismatch → FAIL. Never access a live system during validation.

## Validation log
See `validation-log.md`.
