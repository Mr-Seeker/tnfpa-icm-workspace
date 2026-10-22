# D06 · Incentive compensation management & sales performance management

**Job:** Compute rep/dealer incentive payouts on a threshold–target–accelerator–cap curve and convert them into a variable opex rate and payout cash weeks.

## Systems of record (Tamil Nadu / India)
Spreadsheets, Zoho CRM incentives, Xactly/Varicent (larger firms), dealer scheme registers.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D06_incentive-comp-sales-performance/` | `D06_incentive-comp-sales-performance.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D06_incentive-comp-sales-performance.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D06_incentive-comp-sales-performance/`.
2. Replace the sample rows with the company's data (sheets: Plan (threshold, payout at threshold, accelerator, cap, cadence), Reps (quota, actual, target incentive → attainment, payout %, payout, over-cap flag), ToKernel). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 opex variable 'Sales incentives' pct_of_revenue | ToKernel B6 |
| K02 quarterly payout flows | Plan cadence |

## Tamil Nadu notes
- Incentives are salary: TDS u/s 192 at payout; they may affect PF wages if paid as part of wages under the Code on Wages definition.
- Dealer schemes (cash discounts, gold-coin schemes, trips) are usually revenue deductions under Ind AS 115 — model them in D13, not as opex.

## Used in workflows
W02, W04, W05

## Human check
Sales head and CFO approve the plan curve before the year starts; payouts approved per DoA (D08).
