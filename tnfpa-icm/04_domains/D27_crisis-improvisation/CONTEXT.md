# D27 · Ad-hoc crisis improvisation

**Job:** Fast, disciplined response when the plan breaks: crisis playbooks, a stressed 13-week cash view from K02, a crisis log of decisions, and stakeholder communication templates.

## Systems of record (Tamil Nadu / India)
K02 copies, this module's stress workbook, crisis log CSV, phone/WhatsApp groups (human-operated).

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D27_crisis-improvisation/` | `D27_crisis-improvisation.xlsx` (template), `crisis-playbooks.md`; `01_tamil-nadu/` |

## Process
1. Copy `D27_crisis-improvisation.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D27_crisis-improvisation/`.
2. Replace the sample rows with the company's data (sheets: Baseline (weekly receipts/disbursements), Shock (loss %, weeks, recovery, extra payment, deferral), Stressed (→ ending cash, negative week), Result). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K02 baseline weekly cash | Baseline |
| D15 risk register | scenario ids |
| W08 context corrections | one-off events |

## Tamil Nadu notes
- Pre-write playbooks for cyclone/flood (Chennai, delta), grid outage, GST portal outage at filing time, bank account freeze, labour unrest in clusters, key-customer default.
- Communicate in Tamil and English to plant staff; keep a single source of truth for numbers.

## Used in workflows
W05, W07

## Human check
Crisis lead (human) decides; every decision is logged with time, data used and owner.
## Playbook
Read `crisis-playbooks.md` before preparing, deciding or debriefing.

