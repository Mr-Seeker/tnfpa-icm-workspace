# D21 · M&A systems

**Job:** Target valuation (DCF from a K01 copy of the target, trading/transaction multiples), accretion/dilution, and divestiture via K08.

## Systems of record (Tamil Nadu / India)
Spreadsheets, virtual data rooms, CA/merchant-banker valuation reports, NCLT scheme documents.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D21_mergers-acquisitions/` | `D21_mergers-acquisitions.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D21_mergers-acquisitions.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D21_mergers-acquisitions/`.
2. Replace the sample rows with the company's data (sheets: DCF (WACC, g, FCF Y1–Y5 → EV, equity), Comps (EV/EBITDA → median), Multiples, AccretionDilution (financing mix → pro-forma EPS)). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 copy of target | FCF |
| K08 divestiture | carve-outs |
| D22 cap table | share-funded deals |

## Tamil Nadu notes
- Schemes of arrangement for TN companies go to the NCLT Chennai bench; CCI approval needed above asset/turnover or deal-value thresholds.
- Valuations for FEMA/Companies Act purposes need registered valuers/merchant bankers.

## Used in workflows
W07, W10

## Human check
Board approves any offer; regulatory steps per counsel.
