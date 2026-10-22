# D22 · Cap table management systems

**Job:** Fully diluted cap table, new-round pricing, ESOP pool top-up and a simple liquidation-preference waterfall.

## Systems of record (Tamil Nadu / India)
Spreadsheets, Qapita, Trica Equity, Carta (rare in India), the company's register of members (MGT-1).

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D22_cap-table-management/` | `D22_cap-table-management.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D22_cap-table-management.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D22_cap-table-management/`.
2. Replace the sample rows with the company's data (sheets: Holders (class, shares, preference, invested → pre/post %), Round (pre-money, investment, pool target → price, new shares, top-up), Waterfall). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| D21 accretion/dilution | shares |
| D19 shareholding | categories |
| K01 opening cash | new money |

## Tamil Nadu notes
- StartupTN and the TN Startup & Innovation Policy support early-stage firms; DPIIT recognition affects ESOP taxation timing.
- Share issues and transfers attract stamp duty; preferential allotments need valuation reports (Companies Act s.62/42, FEMA for foreign investors).

## Used in workflows
W07

## Human check
Board and shareholders approve allotments; counsel reviews terms.
