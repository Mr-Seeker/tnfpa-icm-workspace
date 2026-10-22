# D03 · Statutory & regulatory reporting engines

**Job:** Produce Schedule III statement totals from the mapped TB, check the balance-sheet identity, and track statutory filing deadlines (MCA, GST, income tax, SEBI).

## Systems of record (Tamil Nadu / India)
Tally/Zoho/SAP statutory reports, CA firm working papers, XBRL tools for MCA filings, GST software (ClearTax, Zoho GST, Tally GST).

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D03_statutory-regulatory-reporting/` | `D03_statutory-regulatory-reporting.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D03_statutory-regulatory-reporting.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D03_statutory-regulatory-reporting/`.
2. Replace the sample rows with the company's data (sheets: ScheduleIII (line, section, current, previous, change), TB (mapped signed amounts), Totals (assets, equity+liabilities, profit, difference)). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| W07 board pack (statutory view) | ScheduleIII + Totals |
| 01_tamil-nadu/statutory-calendar.csv | due dates |
| D10 evidence register | filed returns |

## Tamil Nadu notes
- RoC Chennai and NCLT Chennai bench have jurisdiction for TN-registered companies.
- AGM within six months of FY end (30 Sept); AOC-4 within 30 days and MGT-7 within 60 days of the AGM.
- Schedule III requires MSME-separated payables, receivable/payable ageing and CWIP ageing.

## Used in workflows
W04, W07

## Human check
Statutory numbers leave the company only after the auditor/CA signs off; management MIS must be labelled as such.
