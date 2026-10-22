# D02 · ERP & core accounting systems

**Job:** Bring the books in cleanly: trial balance integrity (Dr = Cr), ledger → Schedule III → kernel-target mapping, and the export recipe per ERP.

## Systems of record (Tamil Nadu / India)
Tally Prime (dominant among TN MSMEs), Zoho Books (Chennai), SAP S/4HANA / Business One, Oracle NetSuite, Microsoft Dynamics, Ramco ERP (Chennai), Marg, Busy.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D02_erp-core-accounting/` | `D02_erp-core-accounting.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D02_erp-core-accounting.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D02_erp-core-accounting/`.
2. Replace the sample rows with the company's data (sheets: TrialBalance (ledger, group, debit, credit, net, Schedule III line, kernel target, mapped?), Summary (Dr, Cr, difference, unmapped)). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| memory/mappings/registry.csv | TrialBalance mapping columns |
| K03 Reconcile | mapped TB |
| K01 opening_balances.* | balance-sheet ledgers |

## Tamil Nadu notes
- Accounting software must keep an audit trail (Companies (Accounts) Rules, Rule 3(1)) — confirm it is switched on before relying on exports.
- Tally exports Dr/Cr suffixes and Indian digit grouping; K03 parses both.
- One Tally company per FY is common — register each FY as its own source period.

## Used in workflows
W03, W02

## Human check
Controller confirms the TB balances and the mapping before the first model is fitted.
