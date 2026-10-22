# D14 · Macroeconomic & market intelligence systems

**Job:** A dated register of macro and market indicators linked to the drivers they move, with sensitivities and staleness flags.

## Systems of record (Tamil Nadu / India)
RBI (policy rate, DBIE), MoSPI (CPI, IIP, GDP), FBIL (reference rates), TN Department of Economics & Statistics (GSDP), IMD Chennai (monsoon), GSTN state collections, commodity exchanges, industry reports.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D14_macroeconomic-market-intelligence/` | `D14_macroeconomic-market-intelligence.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D14_macroeconomic-market-intelligence.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D14_macroeconomic-market-intelligence/`.
2. Replace the sample rows with the company's data (sheets: Indicators (value, unit, as-of, source, baseline, deviation, driver, sensitivity → suggested shift, stale?)). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 debt[ALL].annual_rate | repo-linked lending |
| K01 opex escalation | CPI |
| K01 seasonality / growth | monsoon, GSDP |
| W08 corrections (context) | shocks |

## Tamil Nadu notes
- Track NE monsoon (Oct–Dec) rainfall vs normal for agri, construction and logistics clients.
- TN's GST collections and power demand are fast proxies for state activity.

## Used in workflows
W02, W04, W10

## Human check
Any driver shift suggested here is a hypothesis — it goes through W09/W10, never straight into the champion.
