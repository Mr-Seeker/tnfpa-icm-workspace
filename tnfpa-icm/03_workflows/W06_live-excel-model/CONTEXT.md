# W06 · Live-formula Excel model (Operate)

Finance professionals want a workbook where changing an assumption recalculates the model. Here the
champion K01 copy already **is** that workbook: an Assumptions sheet of named, editable driver cells and a
Model sheet where every P&L and cash-flow line is a real formula. **Core principle:** no workbook ships
unverified, and the workbook is generated from the model structure — never hand-edited values.

## Inputs
| Working | Reference |
|---|---|
| champion workbook (`memory/models/model-versions.csv`) | `02_kernel/K01_monthly-pnl-cash-model.xlsx`, `02_kernel/formula-reference.md` |
| the audience's layout request (quarterly, weekly, segment tabs, lender view, ₹ lakh MIS) | `05_bi-and-presentation/templates/monthly-mis-inr-lakh.xlsx` |

## Process — standard monthly model
1. Copy the champion to `output/<company>-model-<date>.xlsx`.
2. Confirm Checks OVERALL = PASS after recalculation. Confirm the Assumptions values equal the champion's
   (it is a copy; nothing should differ).
3. If the audience wants ₹ lakh/crore, set `display_divisor`/`display_unit` (reports only — the engine stays
   in rupees) and use Summary/Briefing for the formatted view.

## Process — any other cadence or layout
1. These are company work, not kernel variants. Build a company workbook in `models/` (e.g.
   `models/excel-quarterly.xlsx`) whose calculation sheet references a pasted K01 Export_Rows block or
   rebuilds the lines with the same formulas (`formula-reference.md`), quarterly/weekly/segment columns as
   needed. Keep to the allowed formula vocabulary (helper rows are fine).
2. Add **parity rows** to its Checks: every line and period must reproduce the frame it is meant to
   reproduce (the K01 champion, or its quarterly/weekly aggregation) within 1e-6 relative (absolute below 1).
3. Register it: `memory/models/workflows.csv` kind `report`, procedure = a short runbook in `models/`.

## Verify before delivering (always)
A failing parity or identity row means the workbook is wrong. Fix the formulas, never the tolerance,
and never deliver a workbook with any FAIL. Never paste computed values into formula cells.

## Outputs
`output/<company>-model-<date>.xlsx` (or the bespoke workbook) with Checks PASS.

## Human check
The CFO opens it, changes one driver, and sees the model recalculate before it goes to the board/bank.

## Next
Workbook delivered → **W07 board-briefing** (the narrative that goes with it).
