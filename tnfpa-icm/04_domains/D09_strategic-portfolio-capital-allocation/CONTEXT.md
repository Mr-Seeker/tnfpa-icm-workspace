# D09 · Strategic portfolio & capital allocation systems

**Job:** Rank projects by NPV at the hurdle rate, IRR, profitability index and strategic/risk scores, and fund within the capital budget.

## Systems of record (Tamil Nadu / India)
Spreadsheets (this module), PPM tools (Planview, Microsoft Project), board capex papers.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D09_strategic-portfolio-capital-allocation/` | `D09_strategic-portfolio-capital-allocation.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D09_strategic-portfolio-capital-allocation.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D09_strategic-portfolio-capital-allocation/`.
2. Replace the sample rows with the company's data (sheets: Setup (hurdle, budget, weights), Projects (year-0 to year-10 cash flows → NPV, IRR, PI, composite score, rank, cumulative capex, funded?)). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| D17 CapexPlan → K01 capex_monthly, da_monthly | funded projects |
| D23 green finance | eligible projects |
| W07 the ask | funding decisions |

## Tamil Nadu notes
- Include TN capital subsidies and SIPCOT land costs explicitly as cash flows (with sanction evidence), not as hurdle-rate tweaks.
- Rooftop/open-access solar and wind repowering projects are common in Coimbatore/Tirunelveli belts.

## Used in workflows
W02, W07

## Human check
Board/MD approves the funded list (DoA).
