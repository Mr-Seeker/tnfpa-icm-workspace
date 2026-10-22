# D07 · Customer relationship management systems

**Job:** Use pipeline and invoice data to sanity-check K01 revenue and to schedule K02 collections by week; derive DSO evidence.

## Systems of record (Tamil Nadu / India)
Zoho CRM (Chennai), Freshsales (Freshworks), Salesforce, HubSpot, dealer/distributor management systems, Tally receivables.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D07_crm-customer-relationship/` | `D07_crm-customer-relationship.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D07_crm-customer-relationship.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D07_crm-customer-relationship/`.
2. Replace the sample rows with the company's data (sheets: Stages (probabilities), Pipeline (stage, amount, expected month → weighted), WeightedByMonth, Collections (invoice date + credit days + slip days → K02 week), Setup). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 channels revenue (sanity check) | WeightedByMonth |
| K02 receipts by week | Collections K02 week |
| K01 working_capital.dso_days | collection history |

## Tamil Nadu notes
- Dealer credit of 30–60 days with festival-season extensions is common; record actual slip days per customer.
- E-invoice IRN dates are the cut-off evidence for B2B revenue.

## Used in workflows
W03, W05

## Human check
Sales ops confirms stage probabilities quarterly from won/lost history.
