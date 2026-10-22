# 02_kernel — the no-code finance kernel (factory, read-only masters)

**Job:** the stable, verified calculation engines. Each workbook replaces a part of openfpa's `pyfpa`
package with live formulas and a `Checks` sheet. **Never type into these masters** — copy the workbook
into `companies/<slug>/models/` (or `memory/sources/evidence/` for reconciliations) first.

| Workbook | Replaces (pyfpa) | Used by |
|---|---|---|
| `K01_monthly-pnl-cash-model.xlsx` | config schemas, revenue/cogs/opex/debt/working-capital/tax models, `cashflow_from_config`, `apply_corrections`, `model_to_excel`, `verify_workbook`, `extract_lines`, `to_briefing_md`, `forecast_to_excel` | W02, W04, W06, W07, W09, W10 |
| `K02_13-week-cash.xlsx` | `cash13` (`WeeklyFlow`, `expand_flow`, `cash13_forecast`), `runway_summary` | W05, W07, D27 |
| `K03_source-reconcile.xlsx` | `inspect_data_files`, `profile_table`, `read_pl_csv`/`_parse_amount`, `reconcile_account_table`, connector scaffold/validate checks | W01, W03 |
| `K04_scoring-backtest.xlsx` | `score_forecast`, `extract_lines`, `aggregate_periods`, `holdout_backtest`, snapshots, `render_scorecard`, `persistent_miss`, `magnitude_cap`, `recover_actuals`, `best_snapshot` | W09, W10, W11 |
| `K05_research-evaluator.xlsx` | `ResearchObjective`, `evaluate_challenger`, epoch status rules, `promote_challenger` (with recompute guard) | W10 |
| `K06_sku-profitability.xlsx` | `sku_profitability`, `pareto_breakpoint` | W12 generated skill `sku-profitability` |
| `K07_segment-rollup.xlsx` | `segment_pnl`, `roll_up_segments`, `segments_to_channels`, segment forecast | W02, W12 `segment-rollup` |
| `K08_divestiture.xlsx` | `Carveout`, `divest`, `net_debt_to_ebitda` | D21, capital-allocation questions |
| `K09_portfolio-learning.xlsx` | `mine_priors`, `validate_prior`, `find_recurring_skills` | W11 |
| `K10_intake-onboarding.xlsx` | intake bank, `record_intake_fact`, `intake_ready`, `next_intake_questions`, `render_business_profile`, `render_architecture_proposal` | W01 |
| `K11_memory-retrieval.xlsx` | `build_memory_index`, `search_memory`, `build_context_pack` | every broad task |

**Inputs:** pale-yellow cells only. **Process:** the spreadsheet engine recalculates on open.
**Outputs:** the named result cells/sheets listed in each README. **Human check:** `Checks` › OVERALL
must be PASS; copy results out only then.

## How the kernel was verified
Each workbook was evaluated with an independent formula engine and compared against an independent
re-implementation of openfpa's maths and against openfpa's published outputs:
K01/K02 reproduce Ridgeline to < 1e-12 relative error (and the board briefing text exactly); K05
reproduces both Fox Factory epochs (objective gains 0.05497 discarded / 0.61420 proposed); K07 and K08
reproduce the Fox FY2026–27 segment forecast and the full Marucci divestiture table; K03, K04, K06, K09,
K10 and K11 match the reference logic on test cases. See `examples/` for the reproducible copies.

## Capacity (slots) and what to do when exceeded
K01: 8 channels, 15 opex lines, 5 debt instruments, 120 months, 60 corrections. K02: 80 flows, 52 weeks.
K03: 1,500 source rows, 500 mapping rules, 500 inspected files, 1,000 profiled rows × 15 columns.
If a company needs more, build a company-specific workbook following `formula-reference.md` — do not
edit the master, and do not merge channels just to fit (that changes the economics).
