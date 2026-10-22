# 03_workflows — the stage contracts (replaces openfpa `skills/`)

**Job:** one folder per workflow. Each `CONTEXT.md` names exact inputs (working = this company/run,
reference = factory), the process, the outputs it writes into `companies/<slug>/`, the human check, and
what comes next. Load only the contract you are executing plus the files it lists.

| Folder | openfpa skill | Phase | Trigger |
|---|---|---|---|
| `W00_cfo-judgment/` | fpa-cfo-judgment | always | interpreting or reporting any number |
| `W01_learn-business/` | fpa-learn-business | 0 onboard | new company, "understand our business", stale profile |
| `W02_scaffold-model/` | fpa-scaffold-model | 1 build | after Gate 1 approval: turn a P&L / TB into a model |
| `W03_configure-actuals/` | fpa-configure-actuals | 2 wire | connect real numbers (Tally, Zoho, bank, GST, filings, spreadsheets) |
| `W04_monthly-close/` | fpa-monthly-close | operate | month-end actuals, plan-vs-actual, re-forecast |
| `W05_cash-runway/` | fpa-cash-runway | operate | runway, 13-week cash, CC/OD limit sizing |
| `W06_live-excel-model/` | fpa-excel-model | operate | "a workbook that recalculates" for the board/bank |
| `W07_board-briefing/` | fpa-board-briefing | operate | board deck, investor/lender update, CFO briefing |
| `W08_capture-correction/` | fpa-capture-correction | learn | a human says a number or method is off |
| `W09_backtest-learn/` | fpa-backtest-learn | learn | at/after close: score forecasts, propose ratified fixes |
| `W10_research-loop/` | fpa-research-loop | learn | bounded autonomous champion/challenger epochs |
| `W11_portfolio-learn/` | fpa-portfolio-learn | learn (practice) | several same-type clients → shared priors |
| `W12_generate-company-skill/` | learn-business steps 8–10 + `skills/generated/*` | extend | a profile fact needs a bespoke skill or agent |

Order on a new company: W01 → **Gate 1** → W02 → W03 → W04/W05/W06/W07 → W09 → W10 (**Gate 2** for
promotion) → W11 across clients. W08 can happen at any time; W00 is consulted throughout.
Each workflow writes only inside `companies/<slug>/` (W11 also writes `portfolio/library/`).
