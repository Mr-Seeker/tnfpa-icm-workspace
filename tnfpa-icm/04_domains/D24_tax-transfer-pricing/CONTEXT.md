# D24 · Specialised tax & transfer pricing engines

**Job:** Monthly GST cash payable (output − eligible ITC + RCM), advance-tax instalments, TDS register, and the transfer-pricing arm's-length range.

## Systems of record (Tamil Nadu / India)
GST portal (GSTR-1/2B/3B), TRACES, Tally/Zoho GST modules, ClearTax/other GST software, CA firm TP studies, Prowess/Capitaline comparables.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D24_tax-transfer-pricing/` | `D24_tax-transfer-pricing.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D24_tax-transfer-pricing.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D24_tax-transfer-pricing/`.
2. Replace the sample rows with the company's data (sheets: GST (state code 33: CGST+SGST vs IGST, ITC, RCM → cash payable, carry-forward), AdvanceTax (15/45/75/100%), TDS (section, payee, amount, rate → TDS), TPComparables, TPRange (35th/median/65th, adjustment)). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K02 GST (20th), TDS (7th), advance tax (15th) disbursements | GST, TDS, AdvanceTax sheets |
| K01 tax_rate | AdvanceTax effective rate |
| D21/D03 | TP adjustments |

## Tamil Nadu notes
- Intra-TN supplies carry CGST+SGST; supplies to Puducherry or Karnataka carry IGST even if a few km away.
- From 1 April 2026 the Income-tax Act 2025 applies — map section numbers with the CA.

## Used in workflows
W05, W02

## Human check
Tax manager/CA confirms every return figure; the workspace never files anything.
