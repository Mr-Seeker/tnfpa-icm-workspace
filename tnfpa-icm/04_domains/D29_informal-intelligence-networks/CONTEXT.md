# D29 · Informal corporate intelligence networks

**Job:** Capture lawful weak signals from dealers, suppliers, bankers and associations; grade source reliability and information credibility; route strong signals into intake evidence or context corrections.

## Systems of record (Tamil Nadu / India)
This module's signal log and relationship map; meeting notes.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D29_informal-intelligence-networks/` | `D29_informal-intelligence-networks.xlsx` (template), `intelligence-ethics.md`; `01_tamil-nadu/` |

## Process
1. Copy `D29_informal-intelligence-networks.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D29_informal-intelligence-networks/`.
2. Replace the sample rows with the company's data (sheets: Signals (source type, pseudonymous id, reliability A–F, credibility 1–6, signal, driver, corroborations, lawful? → confidence, route), Network (contact map, staleness)). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| memory/intake.csv (evidence) | Signals route |
| W08 context corrections | high-confidence signals |
| D14 macro register | market signals |

## Tamil Nadu notes
- Useful lawful sources: CII/FICCI TN, Madras Chamber, TNCCI (Madurai), CODISSIA/SIEMA (Coimbatore), Tiruppur Exporters' Association, HOSTIA (Hosur), bank relationship managers, dealer meets.
- Never solicit confidential competitor data or unpublished price-sensitive information; discard anything not lawfully shared.

## Used in workflows
W01, W08, W00

## Human check
A signal never changes the champion directly — it becomes evidence for W09/W10 or a human-confirmed context correction.
## Playbook
Read `intelligence-ethics.md` before preparing, deciding or debriefing.

