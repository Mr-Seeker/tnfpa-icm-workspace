# D15 · Risk & treasury management systems

**Job:** Enterprise risk register with heat-map ratings and owners, bank covenant tests from model outputs, and FX exposure/hedge ratios.

## Systems of record (Tamil Nadu / India)
Spreadsheets, GRC tools, bank portals (balances, limits, drawing power), treasury management systems in larger groups.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D15_risk-treasury/` | `D15_risk-treasury.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D15_risk-treasury.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D15_risk-treasury/`.
2. Replace the sample rows with the company's data (sheets: RiskRegister (likelihood × impact → score, rating, owner, mitigation, D27 link), Covenants (DSCR, current ratio, TOL/TNW, net debt/EBITDA vs limits), FXExposure). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 debt slots (CC/OD as loc, term loans) | facility terms |
| K02 stress (D27) | risk links |
| W07 covenant headroom | Covenants |

## Tamil Nadu notes
- Banks with TN roots (Indian Bank, IOB, TMB, KVB, City Union Bank) and SIDBI commonly use DSCR, current ratio and TOL/TNW covenants plus stock/book-debt drawing power.
- Cyclone/flood and power-outage risks are first-class operational risks in Chennai and the delta.

## Used in workflows
W05, W07

## Human check
Risk owners confirm ratings; treasury confirms covenant definitions from the sanction letter.
