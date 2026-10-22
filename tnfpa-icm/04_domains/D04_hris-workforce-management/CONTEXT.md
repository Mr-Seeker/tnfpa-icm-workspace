# D04 · HRIS & workforce management systems

**Job:** Turn the headcount plan into fully loaded payroll cost (EPF, EDLI, ESI, gratuity, bonus, LWF) and dated statutory cash flows.

## Systems of record (Tamil Nadu / India)
Zoho People/Payroll (Chennai), Ramco HCM (Chennai), greytHR, Keka, Darwinbox, SAP SuccessFactors; biometric attendance; contract-labour registers.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D04_hris-workforce-management/` | `D04_hris-workforce-management.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D04_hris-workforce-management.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D04_hris-workforce-management/`.
2. Replace the sample rows with the company's data (sheets: Rates (statutory rates — verify), People (id, location, department, gross, basic %, start/end month → loaded cost), ToKernel). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 opex fixed 'Payroll & benefits' monthly_amount | ToKernel B4 |
| K02 salary, PF (15th), ESI (15th) flows | ToKernel month-1 lines |
| D16 gratuity valuation | People basic/service |

## Tamil Nadu notes
- TN professional tax (half-yearly) and Labour Welfare Fund (31 January) are TN-specific employer items.
- The 2025 Labour Codes make basic + DA at least 50% of remuneration — set basic % accordingly.
- Use employee ids only; never store names with salaries.

## Used in workflows
W02, W05

## Human check
HR head confirms headcount and hiring dates; payroll controller confirms rates.
