# D26 · Qualitative strategic intuition and judgement

**Job:** Make judgement explicit and improvable: falsifiable dated predictions with probabilities, reference-class base rates, pre-mortems, and a calibration (Brier) score.

## Systems of record (Tamil Nadu / India)
This module's calibration workbook, decision journal and pre-mortem template.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D26_strategic-intuition-judgement/` | `D26_strategic-intuition-judgement.xlsx` (template), `judgement-toolkit.md`; `01_tamil-nadu/` |

## Process
1. Copy `D26_strategic-intuition-judgement.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D26_strategic-intuition-judgement/`.
2. Replace the sample rows with the company's data (sheets: Predictions (statement, decision, probability, base rate, resolution, outcome → Brier, bucket), Calibration (observed frequency by bucket), Summary). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| W08 context corrections | judgement calls that proved right |
| W10 hypotheses | probabilities |
| W00 reflexes | base rates |

## Tamil Nadu notes
- Keep TN-specific reference classes (festival seasons, monsoon years, cluster cycles) — they are better base rates than national averages.

## Used in workflows
W01, W09, W10

## Human check
Executives own their predictions; the agent keeps the score honestly.
## Playbook
Read `judgement-toolkit.md` before preparing, deciding or debriefing.

