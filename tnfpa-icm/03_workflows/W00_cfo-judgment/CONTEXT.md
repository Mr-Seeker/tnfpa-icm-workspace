# W00 · CFO judgment (always on)

A forecast that is arithmetically correct can still be wrong about reality. Consult this during **any**
analysis — close, briefing, runway, scenario, domain work. **Core principle:** numbers lie by omission.
Before reporting a figure, ask what is *not* in it yet.

## Inputs
- Working: the number(s) about to be reported and the workbook/sheet they came from;
  `memory/corrections/*.md` with `type: context`; the close calendar status of each month.
- Reference: `tn-reflexes.md` (Tamil Nadu-specific traps), `01_tamil-nadu/tax-reference.md`.

## The reflexes (openfpa, unchanged)
| Trap | What a CFO checks |
|---|---|
| Pre-close months look great | COGS and accruals post late. A high gross margin in a not-yet-closed month is usually unposted cost. Exclude pre-close months from conclusions or flag them loudly. |
| A suspiciously profitable month | Almost always a timing/posting artefact. Reconcile before celebrating. |
| Data seams | Where two sources or periods meet (actuals → forecast) look for double counts and gaps. |
| Flash cash vs GL cash | Bank balance and GL cash rarely tie intraday (in-flight receipts, uncleared cheques/NEFT/RTGS). Say which you quote. |
| Intercompany not eliminated | Multi-entity totals double count unless IC revenue/expense is eliminated. A "profitable" entity may be billing its sibling. |
| Working-capital seam | K01 assumes opening AR/AP/inventory sit at the modelled steady state. If real opening balances differ, the gap lands in month 1 as a one-time cash swing — investigate before calling it operating performance. |
| D&A is a real expense | K01 EBITDA is true EBITDA; EBIT = EBITDA − D&A; D&A is added back in OCF only after being expensed. |
| Impairments are non-cash | A goodwill/asset impairment craters reported operating income but not cash. Bridge it outside the operating model. |
| Cash is raw | K02 shows the unfinanced position: a negative trough means "needs a draw", not "insolvent". |
| Known one-offs are flagged | Read `type: context` corrections and exclude those items before attributing a miss or quoting run-rate. |

## How to apply
1. Before stating a conclusion, run the relevant rows (and `tn-reflexes.md`) against the number.
2. If a figure depends on a not-yet-closed month or an un-eliminated total, **lead with the caveat**.
3. When a result looks too good, assume a timing artefact until proven otherwise.

## Red flags — stop and reconcile
"Margin jumped this month" (closed?) · "We're profitable" (intercompany eliminated? D&A included? GST
excluded?) · "We have ₹X in cash" (bank flash or GL? unfinanced or after CC draw?) · a month-1 cash swing
far larger than operating activity (WC seam) · revenue that includes GST · numbers in lakh and crore mixed.

## Output
No file of its own: the caveats go into the close narrative, the briefing or the answer. **Human check:**
none — this is the agent's own discipline.
