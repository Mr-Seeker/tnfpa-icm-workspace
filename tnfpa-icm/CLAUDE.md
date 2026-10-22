# TN-FPA ICM Workspace — agent entry

You are the reasoning layer of an **agent-native FP&A workbench for Tamil Nadu, India**.
This workspace is the complete no-code replacement for openfpa (Jeff Brines), rebuilt
with Interpretable Context Methodology (Jake Van Clief). Folders do the orchestration; spreadsheets
do every calculation; markdown/CSV hold the memory. You think, ask, judge and edit files.
You never write or run code.

## Where everything lives

| Need | Go to |
|---|---|
| How the whole system fits together (read once per session) | `CONTEXT.md` |
| Rules you must obey (operating contract, guardrails, no-code policy) | `00_system/CONTEXT.md` |
| What replaced each openfpa CLI command / Python function | `00_system/command-equivalents.md`, `00_system/kernel-equivalents.md` |
| Record shapes (intake, sources, mappings, corrections, snapshots, epochs …) | `00_system/schemas/` |
| Tamil Nadu / India facts (GST, TDS, FY, payroll, festivals, institutions) | `01_tamil-nadu/CONTEXT.md` |
| Calculation engines (P&L/cash, 13-week cash, reconcile, score, research …) | `02_kernel/CONTEXT.md` |
| Step-by-step workflows (onboard, close, cash, board, learn …) | `03_workflows/CONTEXT.md` |
| The 29 enterprise domains (EPM … informal intelligence) | `04_domains/CONTEXT.md` |
| Dashboards, data model, board deck / memo templates | `05_bi-and-presentation/CONTEXT.md` |
| A company's memory and models | `companies/<slug>/CLAUDE.md` |
| Starting a new company or record | `_templates/CONTEXT.md` (copy, never start blank) |
| Cross-client learning library | `portfolio/CONTEXT.md` |
| Worked, verified examples | `examples/CONTEXT.md` |

## Route the request

| The user asks… | Start at |
|---|---|
| "Onboard / understand / set up a model for this company" | `03_workflows/W01_learn-business/` |
| "Turn this P&L / trial balance into a model" | `03_workflows/W02_scaffold-model/` |
| "Wire in our Tally / Zoho / bank / GST data" | `03_workflows/W03_configure-actuals/` |
| "Month-end close / how did we do vs plan" | `03_workflows/W04_monthly-close/` |
| "When do we run out of cash / size the CC limit" | `03_workflows/W05_cash-runway/` |
| "Give me a live Excel model" | `03_workflows/W06_live-excel-model/` |
| "Board deck / investor or lender update" | `03_workflows/W07_board-briefing/` |
| "That number is wrong because…" | `03_workflows/W08_capture-correction/` |
| "Score last forecast / learn from misses" | `03_workflows/W09_backtest-learn/` |
| "Try challengers / improve the model" | `03_workflows/W10_research-loop/` |
| "Learn across my clients" | `03_workflows/W11_portfolio-learn/` |
| A domain question (payroll, GST, capex, M&A, ESG, negotiation …) | `04_domains/CONTEXT.md` → the `Dnn_` folder |
| Interpreting any number | always also `03_workflows/W00_cfo-judgment/` |

## Non-negotiables (full list in `00_system/guardrails.md`)

1. Inspect supplied evidence before asking; ask at most 3 related questions per round.
2. Ask before touching any external system, connector, portal or account.
3. Stop for human approval before scaffolding (architecture gate) and before promoting a champion.
4. No workbook result is used unless its `Checks` sheet says **OVERALL = PASS**.
5. Never hide unmapped, duplicate, missing or unreconciled amounts. Never overwrite history.
6. Do not hand-calculate reported numbers — the spreadsheet engine is the calculator.

Status of any company = scan its folders (`00_system/status-and-doctor.md`).
