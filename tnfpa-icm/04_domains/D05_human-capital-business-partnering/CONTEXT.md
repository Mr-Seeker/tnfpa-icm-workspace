# D05 · Human capital & business partnering

**Job:** Workforce analytics that finance business partners use with unit heads: attrition, revenue per FTE, cost per hire, span of control — and a cadence of documented BP conversations.

## Systems of record (Tamil Nadu / India)
HRIS exports (D04), recruitment trackers, the BP conversation log (decision files).

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D05_human-capital-business-partnering/` | `D05_human-capital-business-partnering.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D05_human-capital-business-partnering.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D05_human-capital-business-partnering/`.
2. Replace the sample rows with the company's data (sheets: Workforce (opening, hires, exits, closing, attrition, revenue/FTE, cost per hire, span, BP log link)). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 opex payroll (growth assumptions) | Workforce trends |
| D26 calibration log | hiring predictions |
| W04 narrative | productivity commentary |

## Tamil Nadu notes
- Post-Pongal and post-Deepavali attrition spikes are common in Tiruppur/Coimbatore manufacturing; plan hiring around them.
- Naan Mudhalvan / TNSDC and ITI/polytechnic pipelines lower cost per hire for technician roles.

## Used in workflows
W04, W07

## Human check
Unit heads review the analytics; finance BP records agreed actions as decisions.
