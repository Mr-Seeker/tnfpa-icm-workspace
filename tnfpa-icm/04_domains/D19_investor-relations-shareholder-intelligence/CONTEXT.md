# D19 · Investor relations & shareholder intelligence platforms

**Job:** Shareholding-pattern movements, guidance vs consensus vs model gaps (disclosure risk), and the results/disclosure calendar.

## Systems of record (Tamil Nadu / India)
BSE/NSE filings, RTA reports (Cameo, Integrated Registry — Chennai; KFin; MUFG Intime), IR platforms, analyst consensus providers.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D19_investor-relations-shareholder-intelligence/` | `D19_investor-relations-shareholder-intelligence.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D19_investor-relations-shareholder-intelligence.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D19_investor-relations-shareholder-intelligence/`.
2. Replace the sample rows with the company's data (sheets: Shareholding (Reg 31 categories QoQ), Guidance (guidance, consensus, model, gap, disclosure-risk flag), Calendar (period end + days → deadline)). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| W07 investor update | Guidance gaps |
| K01 champion | model column |
| D28 governance | disclosure discipline |

## Tamil Nadu notes
- Only for listed companies or those preparing to list (SME platforms of NSE Emerge / BSE SME are common routes for TN mid-sized firms).
- Unpublished price-sensitive information is restricted under SEBI PIT — never use or leak it.

## Used in workflows
W07

## Human check
Company secretary and CFO approve every external communication.
