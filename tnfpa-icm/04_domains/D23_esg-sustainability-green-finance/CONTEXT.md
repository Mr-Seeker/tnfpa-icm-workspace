# D23 · ESG & sustainability accounting / green finance platforms

**Job:** Scope 1/2 GHG inventory from activity data and dated emission factors, intensity per ₹ crore, BRSR KPIs, and green-finance use of proceeds.

## Systems of record (Tamil Nadu / India)
Spreadsheets, ESG platforms, utility bills (TNPDCL), DG-set logs, solar generation meters, TNPCB consent records.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D23_esg-sustainability-green-finance/` | `D23_esg-sustainability-green-finance.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D23_esg-sustainability-green-finance.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D23_esg-sustainability-green-finance/`.
2. Replace the sample rows with the company's data (sheets: Factors (activity, unit, kgCO2e/unit, scope, source & year), Activity (site, month, quantity → kgCO2e, scope), BRSR, GreenFinance). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 opex (energy costs) | Activity |
| D09 projects (solar/efficiency) | GreenFinance |
| D19 BRSR disclosures | BRSR |

## Tamil Nadu notes
- Tamil Nadu has India's largest wind fleet and strong solar; green open access and rooftop solar materially cut Scope 2 when backed by evidence (RECs/green tariff).
- Chennai's 2019 water crisis makes water withdrawal a material KPI; TNPCB consents set waste and effluent limits.

## Used in workflows
W02, W07

## Human check
Sustainability lead verifies factors and evidence; assurance provider reviews BRSR Core where applicable.
