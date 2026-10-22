# Fiscal year and close calendar

- **Financial year (FY):** 1 April – 31 March (Companies Act 2013 s.2(41); Income-tax). Label `FY2026-27`.
  From 1 April 2026 the Income-tax Act, 2025 uses the term **tax year** for the same April–March period.
- **Quarters:** Q1 Apr–Jun, Q2 Jul–Sep, Q3 Oct–Dec, Q4 Jan–Mar. K01 › Model computes FY and quarter for
  every month; K01 › Summary rolls up by Indian FY and fiscal quarter.
- **K01 start month:** for an annual budget use April (`2026-04-01`). Seasonality weights stay by
  calendar month (Jan…Dec), so a festival maps to the same weight whatever the start month.
- **Typical close timetable (adapt in intake › planning_cadence):**

| Working day | Activity | Why it matters here |
|---|---|---|
| WD-2 to WD0 | cut-off: invoices raised (e-invoice IRN where applicable), GRNs booked | GST outward supply = invoice date |
| WD1–WD3 | bank reconciliation, sales/purchase registers, GSTR-2B download (available ~14th) | ITC is claimable only if in GSTR-2B |
| WD3–WD5 | payroll provisions (PF/ESI/PT/LWF), accruals, depreciation, inventory valuation | COGS posts late → pre-close margin trap (W00) |
| by 7th | TDS of previous month deposited | cash outflow (K02) |
| by 11th | GSTR-1 (monthly filer) | — |
| by 15th | PF and ESI remittance | cash outflow (K02) |
| by 20th | GSTR-3B + GST cash payment (monthly filer) | cash outflow (K02) |
| WD5–WD8 | flash P&L → **freeze line** → re-forecast (W04) | closed months use actuals |
| WD8–WD10 | MIS / board pack in ₹ lakh (W07) | — |

- **Year-end:** physical stock count & fixed-asset verification (CARO 2020), MSME dues review (s.43B(h)),
  advance tax true-up by 15 March, audit (statutory by 30 Sept AGM cycle; tax audit report by 30 Sept).
