# Connector contract (replaces `connectors/generated/<name>/connector.yaml + .py + run.py + README.md`)

**Folder:** `connectors/<name>/` containing `connector.md`, `fixtures/source.csv` (redacted) and
`validation-log.md`. `connector.md` frontmatter:

```yaml
schema_version: 1
name: tally-pl-monthly            # = folder name, ^[a-z][a-z0-9-]*$
source_id: tally-pl-monthly       # registered source
description: Monthly P&L from Tally Prime, normalised to Account,Amount
auth_method: none                 # none | host_environment | mcp  (credentials never stored here)
source_account_column: Particulars
source_amount_column: Closing Balance
fixture_path: fixtures/source.csv # relative, inside the folder
fixture_procedure: K03 Reconcile, tolerance 0, expected = expected_totals   # never live
expected_totals: {income_statement.revenue: 98500000, income_statement.cogs: -61200000}
live_ready: false                 # true only with a documented, approved live recipe
live_recipe: ""                   # e.g. "Tally Prime > Gateway > Display > Trial Balance > Ctrl+E > CSV" or "Zoho Books MCP: report=profit_and_loss"
```

Body sections: **Export recipe** (exact clicks / MCP call / who exports), **Normalisation** (columns kept,
sign convention, Dr/Cr handling), **Failure behaviour** (missing file → stop; duplicate account → fail;
unmapped account → fail; total mismatch → fail), **Validation log** (date, result, by whom).
Rules: source columns must differ; fixture must have no duplicate or unmapped accounts and ≥ 1 mapped
total at scaffold time; validation uses tolerance 0 and never touches a live system.
