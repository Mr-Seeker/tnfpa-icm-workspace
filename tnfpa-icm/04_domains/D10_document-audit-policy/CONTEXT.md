# D10 · Document management, audit & policy repositories

**Job:** Keep a controlled register of policies, contracts, minutes, returns and evidence with retention and review dates, so every number has an auditable trail.

## Systems of record (Tamil Nadu / India)
This workspace's folders, SharePoint/OneDrive, Google Drive, Zoho WorkDrive, DMS of the ERP.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D10_document-audit-policy/` | `D10_document-audit-policy.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D10_document-audit-policy.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D10_document-audit-policy/`.
2. Replace the sample rows with the company's data (sheets: Documents (id, type, title, owner, location, date, retention years → destroy-not-before, review cycle → due, overdue), Summary). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| memory/sources/evidence/ | evidence rows |
| D28 governance scorecard | policy reviews |
| doctor checklist | missing locations |

## Tamil Nadu notes
- Books of account: preserve at least 8 years (Companies Act s.128); GST records for the period prescribed (72 months from the annual-return due date).
- Keep GST, TDS, PF/ESI challans as evidence rows linked to K02 actual outflows.

## Used in workflows
all

## Human check
Company secretary/controller owns the register; reviews overdue are escalated.
