# W02 · Scaffold a model (Phase 1)

Turn a company's financials (trial balance, P&L export, pasted income statement) into a runnable,
validated model. **Core principle:** convention over invention — map the real numbers onto the existing
engine shape; don't design a new one unless the economics demand it.

**Precondition:** Gate 1 approved (`memory/decisions/initial-model-architecture.md`).

## Inputs
| Working | Reference |
|---|---|
| `memory/business-profile.md`, approved architecture | `02_kernel/K01_monthly-pnl-cash-model.xlsx` |
| the P&L / TB file (registered source) | `02_kernel/K03_source-reconcile.xlsx` (parse & map) |
| `memory/mappings/registry.csv` | `00_system/schemas/model-config.md` |
| applied corrections, portfolio priors (if any) | `01_tamil-nadu/seasonality-library.csv`, `schedule-iii-mapping.csv`, `tax-reference.md` |
| domain records the architecture names (e.g. D04 payroll, D17 capex, D15 debt) | `04_domains/domain-kernel-matrix.csv` |

## Process
1. **Ingest** the financials into a K03 copy (Reconcile): parsed `{account: amount}` with Dr/Cr, ₹ and
   lakh commas handled; every account mapped or deliberately ignored.
2. **Map accounts to model lines** in a K01 copy (`models/K01_champion.xlsx`):
   - revenue accounts → channels (one per channel/segment: annual_revenue, 12 calendar-month seasonality
     weights, growth_rate, cogs_pct). Seed seasonality from company history; if history is thin, start from
     the closest row of `01_tamil-nadu/seasonality-library.csv` and mark it as an assumption to confirm.
   - cost accounts → opex lines: fixed (monthly_amount) or variable (pct_of_revenue).
   - debt → term_loan (monthly_principal) or loc (interest-only: cash credit / overdraft / WCDL).
   - balance-sheet rhythm → DSO/DPO/DIO and opening balances.
   - tax → tax_rate (25.168% under s.115BAA unless the profile says otherwise); unabsorbed losses → nol.
   - D&A and capex → from D17 (or the TB average) as da_monthly / capex_monthly.
3. **Write** the company model: fill only Assumptions (and Corrections). If the business does not fit
   K01 (cohorts, projects, fleets, stores, > 8 channels), build a bespoke workbook per
   `02_kernel/formula-reference.md` instead and keep K01 conventions.
4. **Validate:** recalculate; `Checks` OVERALL = PASS (schema + every accounting identity every month).
5. **Run and validate the workflow:** confirm the model reconciles its inputs (base-year totals tie to the
   mapped TB within tolerance, or the difference is explained) and produces the expected outputs.
6. **Register** it: `memory/models/model-versions.csv` (role champion, artifact `models/K01_champion.xlsx`)
   and `memory/models/workflows.csv` (kind forecast; procedure `03_workflows/W04_monthly-close/CONTEXT.md`
   or a company runbook; inputs/outputs). Registration does not run anything.
7. **Surface assumptions:** list the 6–10 inferences a human must confirm (seasonality shape, fixed vs
   variable splits, cogs_pct per channel, opening balances, DSO/DPO/DIO, tax regime, GST treatment).
   Do not bury them — put them at the top of `memory/decisions/<date>-model-assumptions.md`.

## Conventions (match the engine)
- Keep company numbers in Assumptions cells, never typed into formulas.
- Set opening AR/AP/inventory to the **first forecast month's** DSO/DPO/DIO-implied balances
  (month-1 revenue × DSO/30, month-1 COGS × DPO/30 and × DIO/30), NOT the annual average — otherwise
  month 1 shows a one-time cash swing (W00 working-capital seam). If real opening balances differ, record
  the gap as a known month-1 item.
- `total` is a reserved channel/opex name. All amounts excl. GST.

## Outputs
`models/K01_champion.xlsx` (Checks PASS), registry rows, assumptions decision file.

## Human check
Confirm the surfaced assumptions. A live-formula edition for the board is W06.

## Next
Runnable model confirmed → **W03 configure-actuals**, then the operate workflows.
