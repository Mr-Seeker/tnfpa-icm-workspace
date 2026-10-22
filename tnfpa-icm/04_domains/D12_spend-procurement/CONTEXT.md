# D12 · Spend management & strategic procurement

**Job:** Spend cube by category and supplier, days-to-pay evidence for DPO, and MSME 45-day compliance with s.43B(h) tax exposure.

## Systems of record (Tamil Nadu / India)
ERP purchase registers (Tally/Zoho/SAP), Coupa/SAP Ariba (large), GeM (public buyers), supplier Udyam certificates.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D12_spend-procurement/` | `D12_spend-procurement.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D12_spend-procurement.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D12_spend-procurement/`.
2. Replace the sample rows with the company's data (sheets: Setup (MSME limit, as-of), Invoices (supplier, Udyam flag, category, acceptance date, amount, paid date → days, breach, exposure), Cube, ToKernel). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 working_capital.dpo_days | weighted days to pay |
| K02 supplier payment flows | due dates |
| D24 tax (43B(h) disallowance) | exposure |

## Tamil Nadu notes
- Many Coimbatore/Hosur component suppliers are Udyam micro/small units — paying beyond 45 days creates tax disallowance and MSME-1 reporting.
- TDS u/s 194Q on purchases above ₹50 lakh per supplier per year.

## Used in workflows
W02, W05

## Human check
Procurement head confirms Udyam flags; CFO approves any deliberate stretch.
