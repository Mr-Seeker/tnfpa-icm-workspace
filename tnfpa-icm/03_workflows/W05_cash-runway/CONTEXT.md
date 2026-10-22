# W05 · Cash runway — 13-week direct cash (Operate)

Build the operator's near-term liquidity view: schedule the known weekly receipts and disbursements,
show the **raw** cash position (no automatic cash-credit/overdraft draws), report the trough and the first
negative week. **Core principle:** show the unfinanced position — a visible shortfall is the whole point;
it sizes the line.

**Use when:** "when do we run out of money?"; sizing or stress-testing a CC/OD/WCDL limit; lumpy
near-term events (inventory purchases, GST/TDS/advance tax, payroll and bonus, festival stocking).

## Inputs
| Working | Reference |
|---|---|
| workflows of kind `cash`; bank balance (state flash or GL) | `02_kernel/K02_13-week-cash.xlsx` |
| AR invoice register / collections pattern (D07 Collections) | `01_tamil-nadu/statutory-calendar.csv` |
| payroll (D04), supplier dues incl. MSME 45-day (D12), GST/TDS/advance tax (D24), rent (D18), debt service (D15), capex (D17) | `04_domains/D27_crisis-improvisation/` (stress) |

## Process
1. **Discover the company procedure** (workflows kind `cash`).
2. **Build the schedule** in a K02 copy (`models/K02_<date>.xlsx`): opening cash, weeks (default 13), week-1
   start date; flows with name, amount (positive), start week, recurrence once/weekly/biweekly, end week.
   Model what you actually know: AR collections in their expected weeks (D07 → DateToWeek), payroll on its
   cadence (salary ~1st, PF/ESI 15th), supplier POs on due dates, GST on the 20th, TDS on the 7th, advance
   tax on the 15th of Jun/Sep/Dec/Mar, bonus before Deepavali, loan EMIs, rent.
3. **Forecast:** recalculate; Checks PASS. Read Runway: min_cash, min_week, first_negative_week.
4. **Interpret** (W00): a negative min_cash means "needs a draw of at least this much", not "insolvent".
   first_negative_week is the deadline to act. Size the line to the trough plus a buffer (Runway › B10);
   compare with sanctioned limit **and** current drawing power.
5. **Stress it** when the trough is close to zero or the user asks "what if": D27 Shock levers (lost or
   delayed receipts, cyclone/flood days, a one-off payment) on the same weekly baseline.
6. **Report:** trough amount and week, first negative week, recommended line size / action
   (Runway report lines) → `output/<date>-cash-runway.md`; feed `runway` into W07.

## Common mistakes
Smoothing monthly numbers into weeks instead of scheduling the real lumpy items — the lumps are the signal.
Auto-covering the shortfall with a draw and hiding the gap — don't; show it.

## Outputs
`models/K02_<date>.xlsx`, `output/<date>-cash-runway.md`.

## Human check
Treasury/CFO confirms the flow list (especially collections timing) before a limit request goes to a bank.

## Next
Runway → **W07 board-briefing** (runway section) and D15 covenant tests.
