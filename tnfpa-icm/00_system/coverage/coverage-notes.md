# Coverage notes — how openfpa was replaced, and where behaviour differs

`openfpa-coverage-map.csv` lists all 206 files of `openfpa-main` (README, contracts, 12 skills, 2 generated
skills, the `pyfpa` package, the CLI, 58 test files, CI, docs, both examples) with the file(s) that replace
each one here and the treatment: **rewritten** (contract text ported), **replaced** (code → workbook /
procedure), **converted** (data or YAML → CSV/markdown), **carried** (copied as is), **superseded**
(development plans for Python code), **summarised**, **not needed** (packaging only).

## Method
1. Every `pyfpa` function was re-expressed as spreadsheet formulas (K01–K11) or as a written decision rule.
2. Each workbook was evaluated by an independent formula engine and compared with an independent
   re-implementation of openfpa's maths and with openfpa's own published outputs (Ridgeline briefing and
   13-week runway; Fox Factory reconciliation, both research epochs, FY2026–27 forecast, Marucci grid).
3. Every CLI command became a file procedure (`command-equivalents.md`); every schema validator became a
   `Checks` row or a schema rule enforced by the doctor checklist.

## Deliberate, documented differences
| Area | openfpa | Here | Why |
|---|---|---|---|
| List sizes | unbounded lists | fixed slots (K01: 8 channels, 15 opex, 5 debt, 120 months, 60 corrections; K02: 80 flows, 52 weeks; K03: 1,500 rows) | spreadsheets need a fixed layout; larger companies get a bespoke workbook (operating contract) |
| Two applied corrections on one path | later file silently wins | Checks FAIL until one is superseded; exact path beats wildcard | no silent precedence |
| `holdout_backtest(build_cfg_fn)` | caller passes a Python fit function | the agent fits a K01 copy on fit periods only (W09) and pastes predictions into K04 | fitting is judgement; scoring is deterministic |
| Connector code (`connector.py`, `run.py`, subprocess validation) | generated Python, executed in fixture mode | export recipe + redacted fixture + golden totals; validation = K03 at tolerance 0 | no code execution; same contract (no duplicates, no unmapped, totals tie, never live) |
| CLI JSON envelope + exit codes | machine JSON | a short result block (success / failed / invalid) | agents read text equally well |
| Memory index tokens | every word of every file | the path, title, headings and frontmatter words (index rebuild rule); excerpts read from the file | keeps index.csv small and editable; scoring formula unchanged |
| `validate_prior` re-forecast | automatic per fold | one K01 copy per fold, fitness entered in K09 | same leave-one-out maths; the re-forecast is a workbook copy |
| `verify_workbook` | Python engine compares workbook with pandas frame | the workbook is the engine; identity checks every month + GOLDEN parity rows | nothing outside the workbook to compare with |
| Fox `foxf-forecast.xlsx` | static values export | Phase C K01 workbooks (live formulas, Export_Rows) | strictly more capable |
| Tests and CI | pytest on Python 3.11–3.13 | Checks sheets + GOLDEN rows, recalculated by any engine | no runtime to test |

## Additions beyond openfpa
Tamil Nadu / India localisation (`01_tamil-nadu/`), Indian fiscal-year and quarter roll-ups, ₹/lakh/crore
reporting, Tally Dr/Cr and lakh-comma parsing, TN statutory cash calendar, TN intake questions, the 29
enterprise domains (`04_domains/`), the BI data model and Office templates (`05_bi-and-presentation/`), a
reconcile `allow unmapped` switch (openfpa CLI flag), and a fully worked TN company example.

## Engine notes
Indian digit grouping in report text uses conditional number formats inside `TEXT()`; Excel, LibreOffice and
Google Sheets support them. If an engine does not, set `number_style` to `western` and use `display_divisor`
(₹ lakh) instead. Workbooks are saved with "recalculate on open"; values appear after the first recalculation.

Formulas use direct cell references only. Workbooks still define names (e.g. `start_month`, `tot_revenue`)
as signposts for readers, but no formula depends on them, because some viewers (Google Drive preview)
return `#NAME?` for a name that points at a formula cell. `Checks` OVERALL is PASS only when **every**
numbered check is PASS; an error value in any check (`#NAME?`, `#VALUE!`, ...) makes it FAIL, and the
detail cell counts pass / fail / error. Blank kernel masters (K01, K04, K08, K09, K11) show FAIL until
their minimum inputs are entered; that is intended.

Validated on 2026-10-18/19 in Google Drive (Google's own recalculation of the uploaded .xlsx/.pptx/.docx)
in addition to the independent formula engine.
