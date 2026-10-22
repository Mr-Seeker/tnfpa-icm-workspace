# D08 · Workflow & budget collaboration orchestration systems

**Job:** Run the budget/re-forecast cycle and approvals without code: a delegation-of-authority matrix, a submission tracker and a cycle summary.

## Systems of record (Tamil Nadu / India)
Kissflow (Chennai), Zoho Creator/Flow, Microsoft Power Automate / SharePoint lists (configured by clicks), Google Forms + Sheets, email.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D08_workflow-budget-collaboration/` | `D08_workflow-budget-collaboration.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D08_workflow-budget-collaboration.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D08_workflow-budget-collaboration/`.
2. Replace the sample rows with the company's data (sheets: DoA (decision type, amount limit, approver, second approver, evidence), BudgetTracker (owner, dates → status), Summary (completion %, overdue)). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| W10 Gate 2 approvals | DoA 'Forecast champion promotion' |
| D09 capex approvals | DoA capex rows |
| W01 planning_cadence | BudgetTracker |

## Tamil Nadu notes
- Family-owned TN businesses often have the MD approve everything — capture that honestly in the DoA rather than an aspirational matrix.

## Used in workflows
W04, W07, W10

## Human check
Board/MD approves the DoA; FP&A owns the tracker.
