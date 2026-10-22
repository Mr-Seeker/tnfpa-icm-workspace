# D01 · Enterprise performance management & planning

**Job:** Run budgets, latest estimates and plan-vs-actual on top of the K01 champion: versions, driver trees, variance attribution and materiality.

## Systems of record (Tamil Nadu / India)
Spreadsheets (this module) are the planning system. Common EPM tools in India: Anaplan, Oracle EPM (Hyperion), Planful, Jedox, Board, Zoho Analytics planning; many TN MSMEs run budgets in Excel/Zoho Sheet.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D01_epm-planning/` | `D01_epm-planning.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D01_epm-planning.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D01_epm-planning/`.
2. Replace the sample rows with the company's data (sheets: Versions (budget / LE / actual, variance, driver, explanation, materiality), DriverTree (units × price, units × unit cost), Setup (materiality)). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 channels[i].cogs_pct | DriverTree cogs_pct |
| K01 channels[i].annual_revenue | DriverTree revenue |
| W04 variance narrative | Versions sheet |

## Tamil Nadu notes
- Budget cycle runs Jan–Mar for an April FY; re-forecast after each quarter and before Deepavali stocking.
- Present in ₹ lakh; budget owners often want Tamil labels for plant-level reviews.

## Used in workflows
W02, W04, W07

## Human check
CFO approves the budget version and every re-forecast posture.
