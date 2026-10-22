# W04 · Monthly close (Operate)

Fold the latest actuals into the model, refresh the forward forecast from the last closed position, and
explain the variance. **Core principle:** a close that only reports numbers isn't done — the value is the
explanation: what changed, why, and what it means forward.

**Use when:** month-end actuals are available; "how did we do vs plan?"; re-forecast requests.

## Inputs
| Working | Reference |
|---|---|
| `memory/models/workflows.csv` (kind close) | `02_kernel/K01…`, `K03…`, `K04…` |
| champion `models/K01_champion.xlsx`; the period's snapshot in `memory/forecasts/` | `04_domains/D01_epm-planning/` (versions & variance template) |
| closed-month actuals (W03 path), `memory/corrections/` | `01_tamil-nadu/fiscal-and-close-calendar.md`, `03_workflows/W00_cfo-judgment/` |

## Process
1. **Discover the company procedure:** use a registered `close` workflow if one exists; otherwise follow
   this contract with the approved architecture.
2. **Ingest the closed month's actuals** (W03): reconcile before use.
3. **Establish the freeze line:** closed months use actuals; the forecast resumes from the last closed
   balance (cash, AR, AP, inventory, debt). Never let a not-yet-closed month drive conclusions (W00).
4. **Recompute the forecast:** copy the champion to `models/K01_LE-<month>.xlsx`, set start_month to the
   first open month, opening balances to the closed balances, horizon to the remaining months (or 12),
   re-apply corrections; Checks PASS.
5. **Variance:** in a D01 › Versions copy compare actual vs plan (and vs last LE) for revenue, gross
   margin, EBITDA and ending cash. For each material variance state the **driver** — volume, price, cost
   ratio, timing, or one-time (check `type: context` corrections first).
6. **Pick a re-forecast posture and say which you used:**
   - **Plan** — frozen forecast unchanged;
   - **Latest estimate** — actuals for closed months, plan forward from the last closed balance;
   - **Run-rate** — project the year-to-date actual pace forward.
7. **Score the prior forecast** for the closed period (hand to W09) and snapshot the new forecast
   (`memory/forecasts/<label>.snapshot.md` + `.assumptions.xlsx`).
8. **Write the narrative:** the 3 things that moved, the 3 risks forward → `output/<period>-close.md`.

## Judgment checks (always)
Is the "closed" month really closed (COGS/accruals, GSTR-2B ITC, payroll provisions posted)? Did an account
move because of a one-time or timing item (festival pre-buy, year-end push, cyclone days)? Multi-entity:
intercompany eliminated before totalling? Are numbers ex-GST and in one unit?

## Outputs
`models/K01_LE-<month>.xlsx`, D01 variance copy, snapshot files, `output/<period>-close.md`.

## Human check
CFO reviews the narrative and the posture before it goes to the board.

## Next
**W05** (near-term liquidity), **W07** (write-up), **W09** (score the prior forecast). Persistent or
material misses feed **W10** for bounded challenger epochs.
