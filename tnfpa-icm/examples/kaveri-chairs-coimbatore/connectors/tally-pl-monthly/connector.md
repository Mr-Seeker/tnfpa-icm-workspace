---
schema_version: 1
name: tally-pl-monthly
source_id: tally-pl-monthly
description: Monthly/annual P&L from Tally Prime, normalised to Account,Amount (Cr
  negative)
auth_method: none
source_account_column: Particulars
source_amount_column: Closing Balance
fixture_path: fixtures/source.csv
fixture_procedure: K03 Reconcile with tolerance 0; expected = expected_totals; fixture
  mode only
expected_totals:
  da: 10200000.0
  income_statement.cogs: 170700000.0
  income_statement.revenue: -293800000.0
  opex.admin: 4600000.0
  opex.freight: 10900000.0
  opex.marketing: 16800000.0
  opex.payroll: 28440000.0
  opex.rent_facilities: 7800000.0
live_ready: true
live_recipe: 'Accountant: Tally Prime > Gateway > Profit & Loss A/c > F2 period >
  Ctrl+E Export > CSV, ledger-wise closing balances > save as data/raw/tally-pl-<YYYY-MM>.csv'
---
## Export recipe
Performed by the company accountant on working day 4 each month (no credentials pass through this workspace).

## Normalisation
Keep Particulars and Closing Balance; Cr = −1, Dr = +1; ₹ full rupees; amounts excl. GST (output GST ledgers ignored with rationale).

## Failure behaviour
Missing file → stop and ask. Duplicate ledger → FAIL. New unmapped ledger → FAIL until mapped or ignored with rationale. Golden-total mismatch on the fixture → FAIL.

## Validation log
See `validation-log.md`.
