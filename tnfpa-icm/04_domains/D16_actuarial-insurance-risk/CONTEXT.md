# D16 · Actuarial & insurance / risk modelling engines

**Job:** Simplified projected-unit-credit gratuity liability, insurance programme register, and catastrophe business-interruption loss estimate.

## Systems of record (Tamil Nadu / India)
Actuary's Ind AS 19 / AS 15 report (authoritative), insurer/broker schedules (New India, United India, Oriental, National, ICICI Lombard, Bajaj Allianz, Tata AIG).

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D16_actuarial-insurance-risk/` | `D16_actuarial-insurance-risk.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D16_actuarial-insurance-risk.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D16_actuarial-insurance-risk/`.
2. Replace the sample rows with the company's data (sheets: Assumptions (discount, escalation, withdrawal, mortality, retirement age, ceiling, vesting), Employees (→ DBO proxy), Results, Insurance (sum insured, premium, BI scenario → insured/uninsured loss)). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 opex payroll benefits | service cost |
| K02 gratuity payouts on exit | Employees |
| D27 crisis scenarios | BI loss |

## Tamil Nadu notes
- Reference events for BI scenarios: Chennai floods (2015), Cyclone Vardah (2016), Cyclone Michaung (2023).
- Use the actuary's report for statutory numbers; this proxy is for planning only.

## Used in workflows
W02, W05

## Human check
CFO uses the actuarial report for accounts; insurance renewals approved per DoA.
