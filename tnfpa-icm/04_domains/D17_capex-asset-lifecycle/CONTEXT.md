# D17 · Capex & asset lifecycle management systems

**Job:** Fixed asset register with Schedule II book depreciation and income-tax WDV depreciation, CWIP ageing, and a capex plan that sets K01 capex_monthly and da_monthly.

## Systems of record (Tamil Nadu / India)
ERP fixed-asset modules, Tally FA registers, CMMS/EAM for maintenance, physical verification sheets.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D17_capex-asset-lifecycle/` | `D17_capex-asset-lifecycle.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D17_capex-asset-lifecycle.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D17_capex-asset-lifecycle/`.
2. Replace the sample rows with the company's data (sheets: Setup (FY start, residual %), Assets (life, block rate, cost, date → SLM/month, months used, book & tax depreciation, timing difference), CapexPlan, CWIP (ageing buckets), ToKernel). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 capex_monthly | ToKernel |
| K01 da_monthly | ToKernel |
| D24 deferred tax view | timing difference |

## Tamil Nadu notes
- Additional depreciation is not available under the s.115BAA regime — check the tax regime before using it.
- CARO 2020 requires periodic physical verification of fixed assets; record the date per asset.

## Used in workflows
W02, W04

## Human check
Plant/finance confirm the capex plan; board approves per DoA (D08/D09).
