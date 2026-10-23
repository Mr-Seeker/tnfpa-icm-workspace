# TN-FPA ICM Workspace — User Manual

> 📘 **User Manual** (this page) · 📄 [Project README](tnfpa-icm/README.md) · ⚖️ [License — Apache 2.0](LICENSE)

**Built on** [openfpa](https://github.com/JeffBrines/openfpa) by Jeff Brines (MIT, © 2026 Guiderail) and [Interpretable Context Methodology](https://arxiv.org/abs/2603.16021) by Jake Van Clief and David McDermott (MIT). See [NOTICE](NOTICE) and [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

### 🚀 Get started in 3 steps

1. **Download:** go to **Releases → v1.0 → Source code (zip)** and unzip it. If you have a GitHub account, you can click **Use this template** instead to get your own copy.
2. **Open the `tnfpa-icm` folder with your AI agent** (Claude, Codex or any agent that can read and edit files). You also need a spreadsheet app that recalculates `.xlsx` files: Excel, LibreOffice Calc, Google Sheets, OnlyOffice, Zoho Sheet or WPS. There's nothing to install and no code to run.
3. **Tell the agent:** *"Help me onboard our company. Our Tally exports are in ./company-data. Inspect them first, then ask me only what you cannot determine."*

Full walkthrough: [§2 Quick start](#2-quick-start)

### 🔍 See it working first

- **[Kaveri Chairs, Coimbatore](tnfpa-icm/examples/kaveri-chairs-coimbatore)**: a complete synthetic Tamil Nadu company, from Tally export and GST/TDS/PF/ESI cash calendar to a board deck.
- **[Fox Factory public proof](tnfpa-icm/examples/foxfactory-public-proof)**: rebuilt from real public SEC filings and reproduces the published figures.
- **[Ridgeline parity](tnfpa-icm/examples/ridgeline-parity)**: reproduces openfpa's published outputs exactly.

### ✅ Check it yourself

Open the workbook in any spreadsheet app, let it recalculate, go to the cell, and compare it with openfpa's published figure. Each workbook's **Checks** sheet should also read **OVERALL = PASS**.

| Example | Figure | Published by openfpa | Where to find ours |
| --- | --- | --- | --- |
| Ridgeline | Revenue | [$6,000,000](https://github.com/JeffBrines/openfpa/blob/ddac4e90edc7b93392d94f33c8f579100fe3f7e7/docs/demo/briefing.md) | [`K01_ridgeline.xlsx`](tnfpa-icm/examples/ridgeline-parity/models/K01_ridgeline.xlsx) › Summary › B5 |
| Ridgeline | EBITDA | [$824,000](https://github.com/JeffBrines/openfpa/blob/ddac4e90edc7b93392d94f33c8f579100fe3f7e7/docs/demo/briefing.md) | `K01_ridgeline.xlsx` › Summary › B9 |
| Ridgeline | Net income | [$572,651](https://github.com/JeffBrines/openfpa/blob/ddac4e90edc7b93392d94f33c8f579100fe3f7e7/docs/demo/briefing.md) | `K01_ridgeline.xlsx` › Summary › B14 (572,651.25 before rounding) |
| Ridgeline | Ending cash | [$720,418](https://github.com/JeffBrines/openfpa/blob/ddac4e90edc7b93392d94f33c8f579100fe3f7e7/docs/demo/briefing.md) | `K01_ridgeline.xlsx` › Summary › B21 (720,417.92 before rounding) |
| Ridgeline | 13-week cash trough | [−$146,000 in week 7](https://github.com/JeffBrines/openfpa/blob/ddac4e90edc7b93392d94f33c8f579100fe3f7e7/docs/demo/briefing.md) | [`K02_ridgeline.xlsx`](tnfpa-icm/examples/ridgeline-parity/models/K02_ridgeline.xlsx) › Runway › B4 and B5 |
| Ridgeline | First negative week | [Week 3](https://github.com/JeffBrines/openfpa/blob/ddac4e90edc7b93392d94f33c8f579100fe3f7e7/docs/demo/briefing.md) | `K02_ridgeline.xlsx` › Runway › B6 |
| Fox Factory | Epoch 001 objective gain (discarded) | [0.0549689](https://github.com/JeffBrines/openfpa/blob/ddac4e90edc7b93392d94f33c8f579100fe3f7e7/examples/foxfactory/.fpa/research/foxf-fy2025-001-broad-mean-reversion.epoch.yaml#L50) | [`phaseB_K05_epochs.xlsx`](tnfpa-icm/examples/foxfactory-public-proof/models/phaseB_K05_epochs.xlsx) › Epochs › AW5 |
| Fox Factory | Epoch 002 objective gain (proposed) | [0.6141956](https://github.com/JeffBrines/openfpa/blob/ddac4e90edc7b93392d94f33c8f579100fe3f7e7/examples/foxfactory/.fpa/research/foxf-fy2025-002-slow-margin-recovery.epoch.yaml#L50) | `phaseB_K05_epochs.xlsx` › Epochs › AW6 |

### ⚠️ Disclaimer

This workspace is a planning and analysis tool. It is not tax, legal, accounting or investment advice. Statutory rates, thresholds and due dates (GST, TDS, PF/ESI, professional tax and others) change, so confirm them against current rules and with your CA or tax adviser, and record confirmations in `tnfpa-icm/01_tamil-nadu/verification-register.md`. The example companies use synthetic data. Provided "as is" under the Apache 2.0 License, without warranty.

### 🛡️ Why a CFO can trust it

- **You approve what matters.** Two human gates: the model architecture, and every promotion of a new champion forecast model. Each gate passes only with a named human approver and a date.
- **The agent asks before it reaches out.** It asks before reading any live system (Tally, Zoho, SAP, NetSuite, bank portals, tax portals, email) and prefers files you hand it. It also asks before any other external access, before writing any generated skill or agent, and before any message is sent. Sending an email or message always needs your separate, explicit instruction.
- **No hidden code.** The agent never writes or runs code. Every number comes from a live-formula spreadsheet your team can open and audit.
- **Changes are bounded.** A forecast tweak must improve holdout fitness and can move a driver by at most 25% per cycle.
- **Rates are checked, not assumed.** Statutory rates and due dates are logged with their official source and last-verified date.

Full rules: [The two human gates](#the-two-human-gates) · [All 18 guardrails](#guardrails-all-18-from-guardrailsmd) · [Data handling](DATA-HANDLING.md)

---

## 1. Introduction

The TN-FPA ICM workspace is a folder-based, agent-native FP&A system: an AI agent reads its markdown contracts, spreadsheets do every calculation, and humans approve two gates. This reference build ships with an India and Tamil Nadu localisation layer (Indian fiscal year, GST, TDS, PF/ESI, lakh and crore reporting). It replaces the open-source openfpa toolkit (Python, CLI, tests) with folders, markdown, CSV registries and formula-driven workbooks, laid out using Interpretable Context Methodology (ICM).

**What it does for one company:** learns the business, builds a monthly P&L and cash model, wires in actuals from Tally, Zoho or bank exports, runs month-end closes and 13-week cash runways, produces board decks and memos, and improves the forecast over time from its own misses.

**What it adds beyond openfpa:** Tamil Nadu and India localisation (Indian fiscal year, GST, TDS, PF/ESI, ₹ lakh/crore, festival seasonality), 29 enterprise finance domains, and a BI data model with Office templates.

### Who uses it

| Role | What they do |
| --- | --- |
| AI agent (Claude, Codex or any file-editing agent) | The primary operator. Reads the contracts, inspects data, asks questions, fills workbooks, writes memory files and reports. Never writes or runs code. |
| CFO / finance lead | Answers intake questions, approves Gate 1 (architecture) and Gate 2 (champion promotion), confirms corrections, signs off narratives. |
| MD / board | Second approver in family-owned firms; receives briefings. |
| Accountant / controller | Exports data from Tally or the ERP, confirms mappings and trial balance. |
| CA / tax adviser | Confirms statutory rates and dates in the verification register. |

### The ideas behind it

- **Folders are the orchestration.** Each folder has a `CONTEXT.md` saying what it is for, its inputs, outputs and the human check. The agent reads only what the task needs.
- **The filesystem is the state.** There is no database. Whether a company is onboarded, which model is live and how accurate it is are all answered by reading files.
- **Spreadsheets are the calculator.** Every number that gets reported comes from a recalculated workbook whose `Checks` sheet says OVERALL = PASS. Nobody hand-calculates reported figures.
- **Factory vs product.** Numbered folders `00_`–`05_` plus `_templates/` are the stable factory. `companies/<slug>/` and `portfolio/library/` are the product that changes every run.
- **Humans keep control.** The agent can experiment on its own after Gate 1, but cannot promote a new model, touch an external system or apply a correction without a named human.

### How to use this manual

Read sections 2–4 once to get oriented. Use section 5 when running a workflow, sections 6–11 as reference while working, section 12 to find the exact procedure for a task, and section 13 when something fails. Folder and file names are written as `code`; sheet names inside workbooks are written as Workbook › Sheet (for example K01 › Checks).

## 2. Quick start

You need two things: an AI agent that can read and edit files in this folder, and a spreadsheet engine that recalculates `.xlsx` files (Microsoft Excel, LibreOffice Calc, Google Sheets, OnlyOffice, Zoho Sheet or WPS). Nothing is installed and nothing is run from a command line.

### First time in a new organisation

Ask the agent to run the setup questionnaire (`00_system/setup-questionnaire.md`). It records ten answers in `00_system/setup-answers.md`, which does not exist yet in this workspace.

| # | Question | Default if unanswered |
| --- | --- | --- |
| 1 | Spreadsheet engine | Microsoft Excel (Google Sheets: upload, recalculate, download as .xlsx) |
| 2 | BI tool | None (Excel charts) |
| 3 | Office suite for decks and memos | Microsoft 365 |
| 4 | Report units and digit grouping | ₹ lakh, Indian grouping |
| 5 | Board-pack language | English (Tamil labels optional) |
| 6 | Default approver for Gate 1 and Gate 2 | CFO (Gate 2 also MD for family-owned firms) |
| 7 | CA / tax adviser to confirm rates | None — every rate flagged "to confirm" |
| 8 | External systems the agent may ever access (with approval) | None — humans supply files |
| 9 | One company or several clients (practice / CA firm) | One company |
| 10 | Fiscal year start and close deadline | April; working day 6 |

### Onboard your first company

1. Put your exports (Tally P&L or trial balance, AR ageing, bank statement, payroll summary) in a folder the agent can see.
2. Tell the agent, for example: *"Help me onboard our company. Our Tally exports are in ./company-data. Inspect them first, then ask me only what you cannot determine."*
3. The agent reads `CLAUDE.md`, copies `_templates/company/` to `companies/<your-slug>/`, inspects and profiles your files, and records every fact it can find.
4. It asks at most three related questions per round until all 11 core intake facts are known, then the five Tamil Nadu statutory questions.
5. It writes a business profile and an architecture proposal, then **stops for Gate 1**. You approve by ticking "Approved to scaffold" and adding `Approved by: <name>, <date>` in `memory/decisions/initial-model-architecture.md`.
6. After approval it scaffolds the K01 model, wires in actuals, and from then on runs closes, cash runways, board briefings and the learning loop on request.

### What to say to the agent

| You say | The agent starts at |
| --- | --- |
| "Onboard / understand / set up a model for this company" | W01 learn-business |
| "Turn this P&L / trial balance into a model" | W02 scaffold-model |
| "Wire in our Tally / Zoho / bank / GST data" | W03 configure-actuals |
| "Month-end close" / "How did we do vs plan?" | W04 monthly-close |
| "When do we run out of cash?" / "Size the CC limit" | W05 cash-runway |
| "Give me a live Excel model" | W06 live-excel-model |
| "Board deck" / "Investor or lender update" | W07 board-briefing |
| "That number is wrong because…" | W08 capture-correction |
| "Score the last forecast" / "Learn from misses" | W09 backtest-learn |
| "Try challengers" / "Improve the model" | W10 research-loop |
| "Learn across my clients" | W11 portfolio-learn |
| A domain question (payroll, GST, capex, M&A, ESG, negotiation…) | `04_domains/CONTEXT.md`, then the `Dnn_` folder |
| "Where are we?" | Status and doctor (section 13) |

W00 CFO judgment is applied to every number the agent interprets, whatever the request.

### The six non-negotiables

1. Inspect supplied evidence before asking; ask at most 3 related questions per round.
2. Ask before touching any external system, connector, portal or account.
3. Stop for human approval before scaffolding (Gate 1) and before promoting a champion (Gate 2).
4. No workbook result is used unless its `Checks` sheet says OVERALL = PASS.
5. Never hide unmapped, duplicate, missing or unreconciled amounts. Never overwrite history.
6. Do not hand-calculate reported numbers — the spreadsheet engine is the calculator.

## 3. Workspace map

Everything lives under `tnfpa-icm/` (361 files, about 6 MB). The numbered folders are the factory and are configured once; `companies/` and `portfolio/library/` hold the product and grow with every run.

### Top-level entry files

| File | Purpose |
| --- | --- |
| `README.md` | What the workspace is, who uses it, how to start, proof table, licence and credits (openfpa MIT; ICM MIT). |
| `CLAUDE.md` | The agent's single entry point: where everything lives, request routing table, the six non-negotiables. Wins if anything disagrees with it. |
| `AGENTS.md` | A pointer so other agent runtimes (Codex etc.) find `CLAUDE.md`. Holds no routing content of its own. |
| `CONTEXT.md` | "The system in one screen": openfpa-to-workspace mapping, factory vs product layers, lifecycle, gates, state machine, how a calculation happens. |

### Folders

| Folder | Layer | What it holds | Changes per company? |
| --- | --- | --- | --- |
| `00_system/` | Factory | Operating contract, guardrails, no-code policy, naming rules, setup questionnaire, status/doctor checklist, command and function equivalents, 16 record schemas, coverage map of all 206 openfpa files | No — changes are method changes and need a decision file |
| `01_tamil-nadu/` | Factory | Fiscal and close calendar, statutory calendar, tax, labour and payroll, reporting framework, Schedule III mapping, seasonality priors, sector clusters, institutions, data-source recipes, number and language rules, verification register | No — re-verify when law changes |
| `02_kernel/` | Factory (read-only masters) | Eleven calculation workbooks K01–K11 and `formula-reference.md` | Never edited; copied into company folders |
| `03_workflows/` | Factory | Thirteen workflow contracts W00–W12 (one folder each) | No |
| `04_domains/` | Factory | 29 enterprise domain modules D01–D29, each a contract plus a template workbook (and playbooks for D25–D29); `domain-kernel-matrix.csv` | No; copied into company `domains/` |
| `05_bi-and-presentation/` | Factory | BI star-schema data model, five dashboard specs, chart standards, BI theme, board deck / memo / MIS templates, communication templates | No; templates copied into company `output/` |
| `_templates/` | Factory | Stamps for a new company and every record type (correction, decision, snapshot, experiment, epoch, connector, domain record, generated skill and agent) | No |
| `companies/` | Product | One folder per company, created from `_templates/company/`. Currently empty. | Yes |
| `portfolio/` | Product | `portfolio.csv` (client list, currently header only) and `library/` of human-ratified priors and skills (currently empty) | Yes |
| `examples/` | Reference | Three verified worked examples plus two example generated skills. Read-only. | No |

### Inside a company folder

Created by copying `_templates/company/` to `companies/<slug>/`.

| Path | Contents |
| --- | --- |
| `CLAUDE.md` | Company entry: name, slug, business-type tag, FY, currency, and a map of the folders below |
| `memory/MEMORY.md` | Index of the company's memory vault |
| `memory/intake.csv`, `intake-notes.md` | Onboarding facts with status, confidence and sources; free-text notes |
| `memory/business-profile.md` | Durable business context rendered from intake by K10 |
| `memory/sources/registry.csv`, `sources/evidence/` | Registered data sources; K03 profiles and reconciliations |
| `memory/mappings/registry.csv` | Exact account-to-model-target rules, including deliberate ignores |
| `memory/corrections/` | One file per human correction |
| `memory/forecasts/` | Immutable forecast snapshots (`.snapshot.md` + `.assumptions.xlsx`) |
| `memory/scorecard.md` | Forecast track record rendered by K04 (never hand-edited) |
| `memory/learnings.md` | Every accepted model change with evidence |
| `memory/experiments/` | Tested model changes and their decisions |
| `memory/decisions/` | Gate approvals and material CFO decisions |
| `memory/models/` | `model-versions.csv`, `promotions.csv`, `workflows.csv` |
| `memory/research/` | `objective.md` (CFO-owned fitness function) and `epochs/` |
| `memory/index.csv` | Rebuildable memory index for K11 retrieval |
| `models/` | Company workbook copies: `K01_champion.xlsx`, challengers, LE copies, K02 runs, bespoke workbooks |
| `connectors/` | One folder per recurring data source: recipe, redacted fixture, validation log |
| `data/raw/`, `data/normalized/` | Files exactly as received (never edited); normalised tables produced by a recipe |
| `domains/` | Instantiated domain records `Dnn_<slug>/` |
| `skills/`, `agents/` | Company-specific generated skills and agent briefs (written only after approval) |
| `output/` | Deliverables: close narratives, cash-runway notes, briefings, decks, memos, workbooks, `bi/` fact files |

## 4. Rules of the house

Three documents in `00_system/` bind every agent and every run: the operating contract, the guardrails and the no-code policy. Breaking one of them makes the output invalid as evidence.

### The two human gates

| Gate | When | Passed only when |
| --- | --- | --- |
| Gate 1 — architecture approval | After W01 intake is ready and the proposal is written; before any model, connector, skill or agent is generated | `memory/decisions/initial-model-architecture.md` has "Approved to scaffold" ticked and `Approved by: <name>, <date>` |
| Gate 2 — champion promotion | When a W10 challenger is eligible to replace the live model | K05 › Promotion says PROMOTE with a named human approver and date, and a `promotions.csv` row is written |

Other approvals the agent must ask for: any external access, a correction's interpretation before it becomes `applied`, every generated skill or agent before it is written, and any message actually being sent.

### Guardrails (all 18, from `guardrails.md`)

**Human control at consequential boundaries**

1. Ask before reading any live system: Tally, Zoho, SAP, NetSuite, bank portals, GST portal, income-tax e-filing, TRACES, EPFO/ESIC, MCA21, MCP servers, email. Prefer files the user supplies.
2. Gate 1 before generating any model, connector, skill or agent.
3. Gate 2 only with a named approver and date.
4. Echo a correction's interpretation once; set `status: applied` only after the human confirms.
5. Propose each generated skill or agent with the profile facts that justify it; write only after approval.

**No hidden gaps**

6. Missing, duplicate, conflicting and unmapped data fail visibly (K03). Never fill with defaults.
7. Missing or zero actuals are never perfect forecast performance (K04 refuses to score them).
8. Never overwrite source data, correction history, forecast snapshots, experiments or epochs. Supersede with a new file and change the old one's `status`.
9. A workbook with any FAIL on `Checks` is not evidence. Fix inputs or structure; never edit a formula to force a pass or loosen a tolerance.

**Evidence before promotion**

10. No evidence, no experiment. No holdout, no promotion. Never score on periods used to fit.
11. A parametric change must improve holdout fitness and move a driver by at most ±25% per cycle. A structural change needs a persistent same-signed miss over at least 2 closes that survived the one-time screen, or a human-authored structural correction.
12. Accounting and reconciliation checks override metric improvement. Complexity is a cost.

**Numbers you report**

13. Read reported figures from a recalculated workbook; do not hand-calculate them.
14. Apply W00 CFO judgment before any conclusion.
15. Check every statutory rate or date against `01_tamil-nadu/verification-register.md`, and record changes there with source and date.

**Privacy and safety**

16. Never store credentials, passwords, OTPs, PAN/Aadhaar of individuals, bank account numbers or salary-by-name. Payroll uses employee ids; fixtures are redacted.
17. Informal intelligence (D29) is limited to public or lawfully shared information — no insider information (SEBI PIT), no confidential competitor data, no pretexting.
18. Keep data local. Cross-client learning shares only ratified, abstracted priors, never raw client data.

### No-code policy

The workspace contains no programming languages, scripts, macros, notebooks, containers, package managers or command lines. Determinism comes from spreadsheet recalculation and written rules.

| Purpose | Allowed file types |
| --- | --- |
| Contracts, memory, narrative, records | `.md` (YAML frontmatter as plain data) |
| Registries, fact tables, BI data model | `.csv` (UTF-8, comma, header row; files with ₹ or Tamil text start with a UTF-8 BOM), `.tsv` |
| Calculation engines and templates | `.xlsx` without macros (`.ods` / Google Sheets copies are equivalent) |
| Decks and memos | `.pptx`, `.docx`, `.pdf` (and `.odp` / `.odt`) |
| BI theme | `.json` theme files (data only) |
| Images | `.png`, `.svg` |

**Forbidden:** `.py`, `.js`, `.ts`, `.sh`, `.ps1`, `.bat`, VBA, macro-enabled `.xlsm`/`.pptm`/`.docm`, `.ipynb`, Power Query M, DAX/SQL script files, Dockerfiles, package manifests, YAML as program configuration, add-ins, and auto-refreshing external data connections.

**Allowed formula vocabulary:** arithmetic, `^`, comparisons and `SUM SUMIF SUMIFS SUMPRODUCT COUNT COUNTA COUNTIF COUNTIFS AVERAGE MEDIAN STDEVP MIN MAX SMALL LARGE ABS ROUND ROUNDUP INT MOD IF IFERROR AND OR NOT ISNUMBER N INDEX MATCH EDATE DATEDIF DAY MONTH YEAR TODAY TEXT LEFT RIGHT MID LEN TRIM LOWER UPPER SUBSTITUTE SEARCH REPT CODE VALUE NPV IRR PV`. No `UNIQUE`, `FILTER`, `LET`, `LAMBDA` or `XLOOKUP`, and no whole-column references like `A:A`, so files behave the same in Excel 2016+, LibreOffice, Google Sheets and Zoho Sheet.

### Workbook conventions

- Pale-yellow cells with blue text are the only cells anyone types into. White cells are formulas.
- Every workbook has a `README` sheet and a `Checks` sheet with an OVERALL PASS/FAIL cell.
- Workbooks recalculate on open. Values appear only after the first recalculation.
- Kernel masters in `02_kernel/` are read-only: always copy into a company folder first.
- To take results out, copy the rendered text or values (Briefing, Scorecard, Pack sheets) verbatim into the target markdown file.
- Defined names such as `start_month` exist as signposts only; formulas use direct cell references, because some viewers (e.g. Google Drive preview) show `#NAME?` for names.
- An error value in any check (`#NAME?`, `#VALUE!`) makes OVERALL fail. Blank kernel masters (K01, K04, K08, K09, K11) show FAIL until their minimum inputs are entered — that is intended.
- If no spreadsheet engine is reachable, the agent stops and asks a human to open and recalculate the file.

## 5. The lifecycle and the workflows (W00–W12)

A company moves through onboarding (W01), Gate 1, build (W02, W03), a monthly operating loop (W04–W07), and a learning loop (W08–W11) with Gate 2 before any new model goes live. Each workflow is a folder in `03_workflows/` whose `CONTEXT.md` lists its inputs (working = this company, reference = factory), process, outputs, human check and next step. The agent loads only the contract it is executing plus the files it names, and writes only inside `companies/<slug>/` (W11 also writes `portfolio/library/`).

| Workflow | Phase | Trigger | Main outputs (in `companies/<slug>/`) | Human check |
| --- | --- | --- | --- | --- |
| W00 cfo-judgment | Always | Interpreting or reporting any number | Caveats inside other outputs | None (agent discipline) |
| W01 learn-business | 0 Onboard | New company; "understand our business"; stale profile | `intake.csv`, sources, `business-profile.md`, architecture proposal | Gate 1 |
| W02 scaffold-model | 1 Build | After Gate 1 | `models/K01_champion.xlsx`, registry rows, assumptions decision | Confirm surfaced assumptions |
| W03 configure-actuals | 2 Wire | Connect real numbers | Sources, mappings, evidence, connectors | Approve external access; confirm fixtures are redacted |
| W04 monthly-close | Operate | Month-end actuals; plan vs actual | `K01_LE-<month>.xlsx`, variance, snapshot, `output/<period>-close.md` | CFO reviews narrative and posture |
| W05 cash-runway | Operate | Runway; CC/OD sizing; lumpy events | `models/K02_<date>.xlsx`, `output/<date>-cash-runway.md` | Treasury confirms flow list |
| W06 live-excel-model | Operate | "A workbook that recalculates" | `output/<company>-model-<date>.xlsx` | CFO changes one driver and sees it recalculate |
| W07 board-briefing | Operate | Board, investor or lender pack | Briefing `.md`, deck `.pptx`, memo `.docx` | CFO signs off narrative and ask |
| W08 capture-correction | Learn | "That number is wrong because…" | `memory/corrections/<slug>.md` | Confirm interpretation |
| W09 backtest-learn | Learn | At and after each close | Scores, scorecard, experiments, learnings | Ratify proposals |
| W10 research-loop | Learn | Persistent or material miss | Challenger workbooks, epochs, registry rows | Gate 2 |
| W11 portfolio-learn | Learn (practice) | Several same-type clients | `portfolio/library/` priors and skills | Ratify every promotion |
| W12 generate-company-skill | Extend | Profile shows a gap | `skills/<name>/`, `agents/<name>/` | Approve before writing |

Order for a new company: W01 → Gate 1 → W02 → W03 → W04 / W05 / W06 / W07 → W09 → W10 (Gate 2) → W11 across clients. W08 can happen at any time.

&#91;embedded content: company lifecycle · 10 workflows, 2 human gates\]

Onboarding and build run once; the close, cash, model and briefing loop runs every month; only a Gate 2 approval changes the live model. Corrections (W08) can arrive at any time and feed every forecast, W11 carries learning across clients, and W12 adds company-specific skills.

### W00 · CFO judgment (always on)

A forecast can be arithmetically right and wrong about reality. Before any figure is reported, the agent asks what is *not* in it yet, leads with caveats on pre-close or un-eliminated numbers, and assumes a timing artefact when a result looks too good.

| Trap | What to check |
| --- | --- |
| Pre-close months look great | COGS and accruals post late; exclude or flag unclosed months |
| Suspiciously profitable month | Usually a timing or posting artefact; reconcile first |
| Data seams | Double counts or gaps where sources or actuals/forecast meet |
| Flash vs GL cash | Bank and GL rarely tie intraday; say which one you quote |
| Intercompany not eliminated | Multi-entity totals double count |
| Working-capital seam | Real opening AR/AP/inventory that differ from modelled levels create a one-time month-1 cash swing |
| D&A is a real expense | K01 EBITDA is true EBITDA; EBIT = EBITDA − D&A |
| Impairments are non-cash | Bridge them outside the operating model |
| Cash is raw | K02 is unfinanced: negative means "needs a draw", not insolvent |
| Known one-offs | Read `type: context` corrections and exclude those items |

Tamil Nadu reflexes (`W00_cfo-judgment/tn-reflexes.md`): GST inside revenue (model ex-GST, GST cash separately via D24); ITC is claimable only once in GSTR-2B; festive pull-forward before Deepavali and Pongal; Aadi, Purattasi and Margazhi demand effects; NE monsoon and cyclones as one-offs; March year-end push reversing in April; bonus, advance tax, PF/ESI, GST and TDS as dated lumps; MSME dues beyond 45 days disallowed for tax (s.43B(h)); cash-credit drawing power vs sanctioned limit; promoter and related-party flows; lakh/crore slips (a 100× error); subsidy receivables that pay late.

**Red flags — stop and reconcile:** "margin jumped this month", "we're profitable", "we have ₹X in cash", a month-1 cash swing far larger than operations, revenue that includes GST, lakh and crore mixed.

### W01 · Learn the business

Produces the durable business profile every other workflow reads, and the architecture proposal for Gate 1.

1. Check status; if uninitialised copy `_templates/company/` to `companies/<slug>/`, set the business name, run the doctor.
2. Inspect local evidence first: list files into K03 › Inspect, profile the tables you will rely on (K03 › Profile, evidence saved), register sources, read financials, MIS packs and board notes. Record each fact via K10 › RecordFact with `source_type: local_file` and honest confidence.
3. Paste `intake.csv` into K10 › Facts and ask the Readiness "next round" (≤ 3 related questions, one topic). Record replies as `source_type: user` (confirmed, 1.0).
4. Repeat until `intake_ready` = TRUE, then clear the `tn_statutory` questions.
5. Fill K10 › Proposal (objective, connectors, model components, domain feeds, generated skills, risks, validation checks). Copy Profile → `business-profile.md` and Proposal → `decisions/initial-model-architecture.md`.
6. **Stop for Gate 1.**
7. After approval, seed from `portfolio/library/priors/<type>.csv` if it exists.
8. Propose bespoke skills or agents for gaps (W12), e.g. `sku-profitability`, `segment-rollup`, ARR/cohort, dealer-credit and scheme accrual.
9. Generate approved artefacts, each citing the profile facts that justify it and carrying a `Checks` sheet or reconciliation.
10. Apply existing corrections (parametric into K01 › Corrections; structural via W12).

### W02 · Scaffold a model

Maps the company's real numbers onto the K01 engine shape (convention over invention). Precondition: Gate 1 approved.

1. Ingest the P&L or trial balance in a K03 copy; every account mapped or deliberately ignored.
2. Fill a K01 copy (`models/K01_champion.xlsx`): revenue accounts → channels (annual revenue, 12 calendar-month seasonality weights, growth, COGS %); costs → fixed or variable opex; debt → `term_loan` or `loc` (cash credit, OD, WCDL); DSO/DPO/DIO and opening balances; tax rate (25.168% under s.115BAA unless stated) and unabsorbed losses (`nol`); D&A and capex from D17 or the TB average.
3. If the business does not fit K01 (cohorts, projects, fleets, stores, more than 8 channels), build a bespoke workbook per `02_kernel/formula-reference.md`.
4. Recalculate; Checks OVERALL = PASS.
5. Confirm base-year totals tie to the mapped TB within tolerance, or the gap is explained.
6. Register in `model-versions.csv` (champion) and `workflows.csv` (kind forecast).
7. Surface the 6–10 assumptions a human must confirm at the top of `memory/decisions/<date>-model-assumptions.md`.

Conventions: numbers only in Assumptions; opening AR/AP/inventory = month-1 implied balances (not the annual average); `total` is reserved; all amounts exclude GST. Thin history → start seasonality from the closest row of `seasonality-library.csv` and mark it as an assumption.

### W03 · Configure actuals and data sources

Everything normalises to one shape, `Account, Amount`, so the engine never cares where numbers came from. Sources: local exports (always works), an accounting system via an approved MCP server or its own export, public filings (MCA21, BSE/NSE, SEC), or a recipe written for anything else.

1. Discover existing connectors (`workflows.csv` kind connector; `connectors/*/connector.md`).
2. Pull actuals via the fitting path (with approval for anything external).
3. Profile the table (K03 › Profile) into an evidence file.
4. Register the source (id, entity with GSTIN state code, currency, periods, extraction method, location).
5. Map every account (seed from `schedule-iii-mapping.csv`); register ignores with a rationale.
6. Reconcile (K03 › Reconcile / Results). Richer tables (aged AR/AP, item-level stock, GSTR-2B) get a company reconciliation workbook with its own Checks; derive DSO from AR ageing, DIO from inventory, DPO from AP ageing.
7. For recurring, approved access: copy `_templates/connector/`, add a redacted fixture, run K03 (must pass with ≥ 1 mapped total), store golden totals, write the recipe and failure behaviour, validate at tolerance 0, log it, register a `connector` workflow. `live_ready: true` only with a documented, approved live recipe.
8. Apply W00 (pre-close months, flash vs GL cash, one-offs, GST-inclusive figures).

### W04 · Monthly close

The value of a close is the explanation: what changed, why, and what it means forward.

1. Use a registered `close` workflow if one exists.
2. Ingest and reconcile the closed month (W03).
3. Set the freeze line: closed months use actuals; the forecast resumes from the last closed balances.
4. Copy the champion to `models/K01_LE-<month>.xlsx`; start month = first open month; opening balances = closed balances; horizon = remaining months (or 12); re-apply corrections; Checks PASS.
5. Compare actual vs plan and last LE in a D01 › Versions copy for revenue, gross margin, EBITDA and ending cash. Attribute each material variance to volume, price, cost ratio, timing or one-time (check context corrections first).
6. State the posture used: **Plan** (frozen), **Latest estimate** (actuals + plan forward), or **Run-rate** (YTD pace projected).
7. Score the prior forecast (W09) and snapshot the new one.
8. Write the three things that moved and three forward risks to `output/<period>-close.md`.

Always ask: is the month really closed (COGS, accruals, GSTR-2B ITC, payroll provisions)? Was a move one-time or timing? Is intercompany eliminated? Are numbers ex-GST and in one unit?

### W05 · Cash runway (13-week direct cash)

Shows the raw, unfinanced position; a visible shortfall is the point because it sizes the line.

1. Use a registered `cash` workflow if one exists.
2. In a K02 copy (`models/K02_<date>.xlsx`) enter opening cash (state flash or GL), weeks (default 13) and week-1 start date. Schedule what you actually know: collections by expected week (D07), salary around the 1st, PF/ESI on the 15th, supplier dues (D12, MSME 45-day), GST on the 20th, TDS on the 7th, advance tax on 15 Jun/Sep/Dec/Mar, bonus before Deepavali, EMIs, rent (D18), capex (D17).
3. Recalculate; Checks PASS; read min\_cash, min\_week, first\_negative\_week.
4. Interpret: negative min\_cash = "needs a draw of at least this much"; first negative week = the deadline to act; size the line to trough + buffer and compare with the sanctioned limit and current drawing power.
5. Stress with D27 shock levers when the trough is near zero or the user asks "what if".
6. Report trough, week, first negative week and the recommended action to `output/<date>-cash-runway.md`; feed W07.

Common mistakes: smoothing monthly numbers into weeks instead of scheduling the real lumps; auto-covering the shortfall with a draw.

### W06 · Live-formula Excel model

The champion K01 copy already is the live workbook. Standard monthly model: copy it to `output/<company>-model-<date>.xlsx`, confirm Checks PASS and that Assumptions match the champion, and set `display_divisor` / `display_unit` for ₹ lakh or crore. Any other cadence or layout (quarterly, weekly, segment tabs, lender view, ₹ lakh MIS) is a company workbook in `models/` with parity rows reproducing K01 within 1e-6 relative (absolute below 1), registered as kind `report`. Never deliver a workbook with any FAIL; never paste values into formula cells.

### W07 · Board briefing

A board wants the story and the three things that matter.

1. Use a registered `report` workflow if one exists.
2. Take the champion K01 and the latest K02; enter runway values in K01 › Briefing B3:B6.
3. Copy K01 › Briefing column D (headline, optional runway, monthly table) as the data spine.
4. Prepend `## What changed` (3 movers); append `## Risks` (3) and `## The ask`. Save `output/<date>-board-briefing.md`.
5. Caveat pre-close months, state bank flash vs GL, state amounts exclude GST, state the unit in every table header.
6. Copy the deck and memo templates into `output/` and replace every `{{placeholder}}`; add Tamil labels if wanted.
7. Deliver the W06 workbook alongside if the audience wants the model.

Sending any email or message is a separate, explicit user instruction.

### W08 · Capture a correction

A human reviewer is the highest-signal feedback there is. Three types:

| Type | Example | Effect |
| --- | --- | --- |
| parametric | "November runs \~1.9× a normal month" | Override `path` + `value` applied via K01 › Corrections to every future forecast |
| structural | "Model dealer schemes as a revenue deduction, not marketing" | Pre-ratified method change routed to W12 |
| context | "That Q3 spike was a one-off TNEB tender" | Annotation so W00's one-time screen excludes it from learning |

Steps: classify; identify the target path (e.g. `channels[*].seasonality[10]` for November, 0-based); write `memory/corrections/<YYYY-MM-DD>-<short-name>.md` from the template with **Was off / Correction / Why**; echo the concrete change and set `status: applied` only on confirmation; for parametric, add the row to the champion's Corrections sheet and confirm Checks PASS; update `MEMORY.md` and rebuild `index.csv`. Status is reversible (open / applied / superseded); the backtest may flag a stale correction but never reverts it.

### W09 · Backtest and learn

Self-experimenting, never self-promoting.

1. Snapshot every forecast: K01 › Summary snapshot block → `forecasts/<label>.snapshot.md` with the supplied `created` date, plus the untouched workbook as `<label>.assumptions.xlsx`.
2. At close, score it in K04 › Score, write the score into the snapshot, re-render `scorecard.md`. Missing or zero actuals → no score.
3. Attribute each material miss to a driver after the one-time screen. Flag stale applied corrections for the human.
4. Create an experiment (status draft) before any model change.
5. Propose: **parametric** only if it lowers holdout fitness (K04 › Holdout with a fit-only K01 copy), clamped to ±25%; **structural** only when persistent\_miss is TRUE (same sign over ≥ 2 closes) → W12 on approval.
6. Record before/after metrics and checks; a change that breaks an accounting invariant fails.
7. On acceptance: decision, `status: accepted`, new champion via W10 promotion if it replaces the champion, line in `learnings.md`. Rejected and reverted experiments stay.
8. Escalate to W10 when a miss warrants several challengers.

Day one bootstrap: with 12+ months of actuals, run a holdout immediately (fit early months, hold out recent ones).

### W10 · Research loop (champion vs challenger)

Bounded, autonomous research after Gate 1; promotion needs Gate 2.

1. Use a registered `research` workflow if one exists.
2. Rebuild `index.csv`, build a K11 context pack for the miss, read prior failed epochs.
3. Load `research/objective.md` and the registry into K05 › Objective.
4. Run at most five challengers per run. Each: one falsifiable hypothesis; the smallest change in `models/K01_challenger-<slug>.xlsx`; fit on training periods only; score on holdout periods (K04); run every hard check; enter metrics, complexity and checks in K05 › Epochs; write `research/epochs/<epoch_id>.md`.
5. Mark weak or failed candidates `discarded` and keep them with the reason.
6. Register only promotion-eligible challengers (role challenger, `source_epoch` = epoch\_id), mark the epoch `proposed`, explain gain, trade-offs and complexity.
7. With explicit human acceptance, fill K05 › Promotion. Only on PROMOTE: challenger → champion, old champion → retired, append `promotions.csv`, epoch → `promoted`, append `learnings.md`.

### W11 · Portfolio learn (practice level)

For firms holding several clients. `portfolio/portfolio.csv` lists `client_path,business_type,notes`.

1. Load each client into K09 › Clients with its best scored snapshot and six mineable drivers (DSO, DIO, DPO, tax\_rate, da\_monthly, capex\_monthly), overridden by an applied parametric correction on the exact path.
2. For each business type with at least 3 clients: K09 › Mine finds tight clusters (CoV ≤ 0.15, support ≥ 3) at the median; K09 › Validate runs leave-one-out re-forecasts; K09 › Skills finds generated-skill names recurring in ≥ 3 clients. Recurring structural corrections are extra signal.
3. Present candidates ranked by evidence.
4. On acceptance append to `portfolio/library/priors/<type>.csv`, copy skills to `portfolio/library/skills/<name>/`, log in `library-log.md`.

Priors are seeds: new clients inherit them at W01 step 7, recorded as assumptions.

### W12 · Generate a company skill or agent

Self-extending, not self-executing. Find the gap with evidence (a profile fact, a human structural correction, or a W09 persistent miss); propose name, justification, workbook, proving check and model impact; wait for approval; copy `_templates/generated-skill/` or `generated-agent/` into `skills/<name>/` or `agents/<name>/`; build or copy the workbook (K06 for SKUs, K07 for segments, or bespoke with Checks and parity rows); record an experiment and register a workflow if recurring. Never write company skills into factory folders.

| Business shape | Skill | Workbook |
| --- | --- | --- |
| D2C / dealer product company with discrete SKUs | `sku-profitability` | K06 |
| Multi-segment group | `segment-rollup` | K07 → K01 |
| SaaS / IT services | `arr-waterfall-cohorts` | Bespoke |
| Trucking / logistics | `fleet-driver-cost-scorecard` | Bespoke |
| Knitwear exporter | `order-book-and-export-incentive-cash` | Bespoke + K02 |
| Dealer network with schemes | `dealer-scheme-accrual-and-credit` | D06 / D07 |
| Fireworks (extreme seasonality) | `extreme-seasonality-working-capital` | K01 + K02 |

## 6. The calculation kernel (K01–K11)

The kernel in `02_kernel/` is eleven read-only workbooks that replace openfpa's Python package. Copy a workbook into `companies/<slug>/models/` (or `memory/sources/evidence/` for reconciliations), type only into pale-yellow cells, recalculate, and use results only when Checks OVERALL = PASS.

| Workbook | Does | Sheets | Used by |
| --- | --- | --- | --- |
| K01 monthly P&L + cash | Monthly P&L, indirect cash flow, debt, working capital, tax, corrections, briefing, export | README, Checks, Assumptions, Corrections, Effective, ValidKeys, Model, Summary, Briefing, Export\_Rows | W02, W04, W06, W07, W09, W10 |
| K02 13-week cash | Weekly direct cash and runway | README, Checks, Setup, Flows, Grid, Weekly, Runway, DateToWeek | W05, W07, D27 |
| K03 source reconcile | Inspect folders, profile tables, map and reconcile accounts, validate connectors | README, Checks, Setup, Inspect, Classifiers, Inspect\_Summary, Profile, Mapping, Reconcile, Results | W01, W03 |
| K04 scoring & backtest | Score forecasts, holdout, snapshots, scorecard, learning guards | README, Checks, Score, Holdout, Snapshots, Scorecard, Learning\_Guards | W09, W10, W11 |
| K05 research evaluator | Champion vs challenger evaluation and promotion gate | README, Checks, Objective, Epochs, Promotion | W10 |
| K06 SKU profitability | Per-SKU gross profit and Pareto | README, Checks, SKUs, Ranked | W12 `sku-profitability` |
| K07 segment roll-up | Segment P&L, roll-up, segments → K01 channels, segment forecast | README, Checks, Segments, ToChannels, SegmentForecast | W02, W12 `segment-rollup` |
| K08 divestiture | Carve-out scenarios and leverage sensitivity | README, Checks, Setup, Forecast, S0–S10, Grid | D21, capital allocation |
| K09 portfolio learning | Mine and validate cross-client priors; recurring skills | README, Checks, Setup, Clients, Mine, Validate, Skills | W11 |
| K10 intake & onboarding | Intake readiness, next questions, fact recording, profile and proposal rendering | README, Checks, QuestionBank, Facts, Readiness, RecordFact, Profile, Proposal | W01 |
| K11 memory retrieval | Memory index and task context pack | README, Checks, Task, Index, Pack | Every broad task |

**Capacity:** K01 has 8 channels, 15 opex lines, 5 debt instruments, 120 months and 60 corrections. K02 has 80 flows and 52 weeks. K03 takes 1,500 source rows, 500 mapping rules, 500 inspected files and 1,000 profiled rows × 15 columns. K06 takes 300 SKUs; K07 12 segments; K08 10 scenarios; K09 50 clients; K10 60 facts; K11 400 index rows. If a company needs more, build a company-specific workbook — never edit the master and never merge channels just to fit.

### K01 · Monthly P&L and cash-flow engine

**How to use:** copy to `models/`; fill Assumptions; transcribe every parametric correction into Corrections (path, value, status, type); recalculate; read Checks first; take results from Summary (headline, Indian-FY and quarterly roll-ups, scoring lines) and Briefing (board markdown). Export\_Rows is the month-per-row fact table for K08 and the BI layer.

**Assumptions inputs:**

| Block | Fields |
| --- | --- |
| Scalars | `name`, `start_month` (1st of a month), `horizon_months` (1–120), `tax_rate` (default 0.2517), `da_monthly`, `capex_monthly` |
| Working capital | `working_capital.dso_days` (default 45), `dpo_days` (45), `dio_days` (60) |
| Opening balances | `opening_balances.cash`, `ar`, `ap`, `inventory`, `nol` (unabsorbed tax loss) |
| Display | `currency_code` (INR), `currency_symbol` (₹), `number_style` (indian/western), `display_divisor` (1, 1000, 100000 = lakh, 10000000 = crore), `display_unit` |
| Channels (8 slots) | name, annual\_revenue, growth\_rate, cogs\_pct, 12 seasonality weights Jan–Dec |
| Opex (15 slots) | name, kind `fixed` (monthly\_amount) or `variable` (pct\_of\_revenue) |
| Debt (5 slots) | name, kind `term_loan` or `loc`, opening\_balance, annual\_rate, monthly\_principal |

**Engine rules (per month m):**

- Period start = EDATE(start\_month, m−1); seasonality uses the calendar month, so a festival keeps its weight whatever the start month.
- Channel revenue = annual revenue × weight / sum of 12 weights × (1 + growth)^INT((m−1)/12).
- Channel COGS = revenue × cogs\_pct. Gross profit = revenue − COGS. Fixed opex = monthly amount; variable opex = total revenue × pct.
- EBITDA = gross profit − opex; EBIT = EBITDA − D&A.
- Debt: interest = opening-of-month balance × rate / 12; term-loan principal = MIN(monthly\_principal, balance); LOC is interest-only.
- Pre-tax = EBIT − interest. Loss used = MIN(opening NOL, positive pre-tax); tax = (positive pre-tax − used) × rate. In-period losses do not create new carry-forward; MAT, deferred tax and set-off limits are bridged outside the engine.
- AR = revenue × DSO/30; AP = COGS × DPO/30; inventory = COGS × DIO/30 (30-day months). WC cash impact = −ΔAR + ΔAP − Δinventory, with month 1 compared to opening balances.
- OCF = net income + D&A + WC impact; FCF = OCF − capex; change in cash = FCF − principal; ending cash rolls forward from opening cash.

**Correction precedence:** exact path (e.g. `channels[0].seasonality[11]`) beats a partial wildcard (`channels[*].seasonality[11]`), which beats a full wildcard. Indexes are 0-based. Only `applied` + `parametric` rows change the model; two applied rows on the same path fail Checks. Valid paths are listed on K01 › ValidKeys.

**Checks (28):** 1–15 validate inputs (start month, horizon, tax rate, non-negative values, at least one channel, reserved `total`, unique names, channel/opex/debt fields, corrections unique, resolvable and numeric). 16–25 test accounting identities every month (revenue, gross profit, EBITDA, pre-tax, net income, OCF, FCF, change in cash, tax ≥ 0, NOL ≥ 0). 26–28 test roll-forwards (cash, debt, cumulative working capital). OVERALL is PASS only when all are PASS.

### K02 · 13-week direct cash and runway

Setup: opening\_cash, weeks (default 13, max 52), week-1 start date. Flows: direction (receipt / disbursement), name, amount (positive), start\_week, recurrence (once / weekly / biweekly), optional end\_week. DateToWeek converts a due date (GST 20th, TDS 7th, PF/ESI 15th, advance tax) into a week number.

Rules: once = start week only; weekly = every week start..end; biweekly = every second week; end defaults to the horizon; weeks outside the horizon are ignored. Net = receipts − disbursements; ending cash accumulates from opening cash; no automatic financing. Runway returns min\_cash, min\_week (first week at the minimum), first\_negative\_week (blank = none) and a suggested credit line (trough + buffer). Checks: weeks 1–52, opening cash numeric, valid directions, valid flows, cash roll-forward, grid = weekly totals.

### K03 · Inspect, profile, map and reconcile

- **Inspect:** paste a file listing (relative path, bytes); each file gets extension, candidate flag and a category; missing priority categories (P&L, balance sheet, AR ageing, AP ageing, inventory) are listed in Inspect\_Summary.
- **Profile:** paste a table (header + up to 1,000 rows × 15 columns); returns rows, columns, empty cells per column and duplicate rows.
- **Mapping:** paste `mappings/registry.csv` rows.
- **Reconcile:** paste Account and Amount columns (up to 1,500 rows). Amounts parse ₹, Rs., INR, $, thousands and lakh commas, (parentheses) as negative, blank or "-" as 0, and trailing Dr/Cr (Cr sign set on Setup).
- **Results:** row count, source total, mapped total and totals per target, duplicates, unmapped, ignored, variances vs expected totals, PASSED.

Rules: blank account rows are skipped; any duplicate account fails; any unmapped account fails unless Setup allows unmapped (still listed); ignored rules need a rationale and are excluded. Variance = mapped − expected; within tolerance when |variance %| ≤ tolerance (exact equality when expected is 0); a mapped target missing from the expected list is compared to 0. Connector validation is the same sheet at tolerance 0 against the connector's golden totals — never against a live system.

### K04 · Scoring, holdout and scorecard

- **Score:** lines default to ending\_cash 0.4, ebitda 0.3, revenue 0.2, gross\_margin 0.1. A line is scored only with a predicted value, a non-zero actual and a positive weight. Error = predicted / actual − 1 (signed). Weights renormalise over scored lines. Fitness = Σ weight × |error| (weighted MAPE; lower is better). No scorable line = error, never perfect.
- **Holdout:** paste actuals by period, set N; the last N periods are held out and the model must be fitted only on the rest. Flows are summed, stocks take the last period, gross margin = Σ GP / Σ revenue.
- **Snapshots → Scorecard:** one row per snapshot; Scorecard renders `memory/scorecard.md`.
- **Learning\_Guards:** persistent\_miss is TRUE when the last K errors of a line share a sign and exceed a threshold (default K = 2, threshold 0); magnitude\_cap clamps a proposed driver to ±25% of the old value; recover\_actuals = predicted / (1 + error); best\_snapshot = lowest fitness.

### K05 · Research evaluator

For each objective metric: improvement = (champion − challenger) / |champion| for lower-is-better (reversed for higher-is-better); if the champion is 0, improvement is 0 when the challenger is also 0, else −1 or +1. The regression guard fails if any raw improvement < −max\_metric\_regression. Improvements are clamped to \[−1, +1\], weighted by weight / total weight; complexity cost = complexity\_penalty × max(0, Δcomplexity); objective\_gain = weighted improvement − cost. Promotion-eligible = all hard checks pass AND guard passes AND gain ≥ min\_improvement. Promotion requires a named approver, epoch status `proposed`, eligibility on recompute, matching challenger ids and `source_epoch` = epoch\_id.

### K06 · SKU profitability

Up to 300 SKUs: annual units, selling price, unit cost → revenue, COGS, gross profit, gross margin. Ranked sorts by gross profit (ties keep input order) with revenue share and cumulative revenue %; pareto\_breakpoint = SKUs reaching 80% of revenue. Margin here excludes marketplace commission, GST leakage, returns, freight and fulfilment — weigh contribution rupees, not just %.

### K07 · Segment roll-up

Segment = net sales + Adjusted-EBITDA margin (+ growth). Consolidated margin is recomputed from totals, never averaged. ToChannels turns each segment into a K01 channel with flat seasonality, its own growth and the consolidated blended cogs\_pct. SegmentForecast applies yearly growth and margin assumptions for up to 5 years.

### K08 · Divestiture and leverage

Paste K01 Export\_Rows values into Forecast; enter the unit's monthly contribution (revenue, gross profit, opex, D&A, capex), rate on retired debt, tax rate, debt and cash on Setup; define up to 10 scenarios (sale\_month = months retained, proceeds), slot 0 = Hold. After the sale month the carve-out is removed, interest falls by proceeds × rate / 12, tax = max(0, pre-tax) × rate, one-time proceeds are excluded from FCF. Leverage = (debt − proceeds − cash) / final-12-month EBITDA; negative = net cash.

### K09 · Portfolio learning

Clients: business type, best snapshot and six mineable drivers. Mine: a driver is a candidate when ≥ min\_support clients have it (default 3) and CoV ≤ dispersion\_max (default 0.15); value = median. Validate: leave-one-out with peer medians; validated when ≥ 2 folds and mean delta ≤ tolerance (default 0). Skills: a skill folder recurring in ≥ 3 same-type clients.

### K10 · Intake readiness and onboarding renderer

Facts: paste `intake.csv`. A key is **known** when it is not a conflict and is confirmed or has confidence ≥ 0.70; `intake_ready` = all 11 core keys known. Readiness walks the question bank in order, takes the topic of the first pending question, and returns up to 3 pending questions of that topic. RecordFact applies progressive authority: a user answer is confirmed at 1.0; disagreeing non-user evidence creates a conflict at the lower confidence with the alternative appended; agreeing evidence raises confidence to the max and merges sources; a new key from non-user evidence is inferred at the given confidence (default 0.8). Profile and Proposal render the two onboarding files. TN questions do not block readiness but must be answered before W03.

### K11 · Memory index and context pack

Index = `memory/index.csv` (path, category, title, keywords). Task tokens = lowercase words of the task (up to 12). Score = (tokens found in entry / task tokens) + 0.5 × (tokens in title) + 0.25 × (tokens in path); zero-overlap entries dropped; ties by path; default limit 8. Pack renders the temporary `memory/context-pack.md`.

### Building a company-specific workbook

Follow `02_kernel/formula-reference.md`: sheets README, Assumptions, calculation sheet(s) with one row per line and one column per period, Summary, Checks. Every driver is a single cell or row; formulas never contain typed numbers. Formats: money `#,##0`, percent `0.0%`, days `0.0`; Indian grouping only in report sheets. Use only the allowed vocabulary (restructure with helper rows otherwise). Add parity rows reproducing the K01 frame within 1e-6 relative; a failing parity row means the workbook is wrong. Register it in `workflows.csv`.

### How the kernel was verified

Each workbook was evaluated by an independent formula engine and compared with an independent re-implementation of openfpa and with openfpa's published outputs: K01/K02 reproduce Ridgeline to < 1e-12 relative error, that is, a difference of less than one part in a trillion (and the briefing text exactly); K05 reproduces both Fox Factory epochs (gains 0.05497 discarded, 0.61420 proposed); K07 and K08 reproduce the Fox FY2026–27 segment forecast and the Marucci divestiture table. Files were also re-checked in Google Drive's own recalculation on 2026-10-18/19.

## 7. The 29 domain modules (D01–D29)

Domains extend the kernel to every system a finance function touches. They never replace the kernel's accounting identities; they produce driver evidence (K01/K02 inputs, intake facts, corrections) that goes through the normal gates. Each `04_domains/Dnn_<slug>/` folder holds a `CONTEXT.md` contract and a template workbook with `Checks`; D25–D29 also carry playbooks. The full feed map (87 rows) is `04_domains/domain-kernel-matrix.csv`.

### How to use a domain

1. Copy the domain workbook and `_templates/domain-record/notes.md` into `companies/<slug>/domains/Dnn_<slug>/`.
2. Replace the sample rows with the company's data, typing only into pale-yellow cells.
3. Recalculate; Checks OVERALL must be PASS. Verify any statutory rate against the verification register.
4. Apply W00 judgment; set `notes.md` status to `reviewed` once the owner confirms (statuses: draft, reviewed, in-use).
5. Transfer the feed values into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

A domain record feeds the kernel only when its Checks = PASS and its status is `reviewed` or `in-use`.

### Domain reference

| # | Domain | Job | Key sheets | Feeds | Workflows | Human check |
| --- | --- | --- | --- | --- | --- | --- |
| D01 | EPM & planning | Budgets, LEs, plan vs actual, driver trees, materiality | Versions, DriverTree, Setup | K01 channel revenue and cogs\_pct; W04 variance narrative | W02, W04, W07 | CFO approves budget and every re-forecast posture |
| D02 | ERP & core accounting | TB integrity (Dr = Cr), ledger → Schedule III → kernel target | TrialBalance, Summary | Mapping registry; K03 Reconcile; K01 opening balances | W03, W02 | Controller confirms TB and mapping |
| D03 | Statutory & regulatory reporting | Schedule III totals, balance-sheet identity, filing deadlines | ScheduleIII, TB, Totals | W07 statutory view; statutory calendar; D10 evidence | W04, W07 | Auditor/CA signs off; MIS labelled as such |
| D04 | HRIS & workforce | Headcount → loaded payroll (EPF, EDLI, ESI, gratuity, bonus, LWF) and dated flows | Rates, People, ToKernel | K01 opex "Payroll & benefits"; K02 salary, PF, ESI; D16 | W02, W05 | HR head confirms headcount; payroll controller confirms rates |
| D05 | Human capital & business partnering | Attrition, revenue/FTE, cost per hire, span, BP log | Workforce | K01 payroll growth; D26 log; W04 narrative | W04, W07 | Unit heads review; BP records actions |
| D06 | Incentive comp & sales performance | Threshold–target–accelerator–cap payouts | Plan, Reps, ToKernel | K01 variable "Sales incentives"; K02 payouts | W02, W04, W05 | Sales head and CFO approve the curve |
| D07 | CRM | Pipeline sanity check, weekly collections, DSO evidence | Stages, Pipeline, WeightedByMonth, Collections, Setup | K01 revenue check; K02 receipts; K01 DSO | W03, W05 | Sales ops confirms stage probabilities quarterly |
| D08 | Workflow & budget collaboration | Delegation of authority, submission tracker, cycle summary | DoA, BudgetTracker, Summary | W10 Gate 2; D09 capex approvals; W01 planning cadence | W04, W07, W10 | Board/MD approves DoA |
| D09 | Strategic portfolio & capital allocation | Rank projects by NPV, IRR, PI and scores within budget | Setup, Projects | D17 → K01 capex and D\&A; D23; W07 ask | W02, W07 | Board/MD approves funded list |
| D10 | Document, audit & policy | Register of policies, contracts, minutes, returns with retention and review dates | Documents, Summary | Evidence folder; D28 scorecard; doctor | All | Company secretary/controller owns it |
| D11 | FinOps & cloud | Cloud/SaaS spend in ₹, RCM GST leakage, unit cost | Setup, CloudCosts, Unit | K01 "Cloud & software"; D24 RCM; D13 | W02, W04 | IT head confirms; CFO approves commitments |
| D12 | Spend & procurement | Spend cube, days-to-pay for DPO, MSME 45-day and s.43B(h) exposure | Setup, Invoices, Cube, ToKernel | K01 DPO; K02 supplier flows; D24 | W02, W05 | Procurement confirms Udyam flags |
| D13 | Revenue operations & pricing | Price–volume–mix bridge, MRP → pocket price | PVM, Bridge, Waterfall | K01 growth and cogs\_pct; W04 drivers; K06 | W04, W07, W12 | Pricing head reviews bridge |
| D14 | Macro & market intelligence | Dated indicator register linked to drivers, staleness flags | Indicators | K01 debt rates, opex escalation, seasonality/growth; W08 context | W02, W04, W10 | Any suggested shift is a hypothesis for W09/W10 |
| D15 | Risk & treasury | Risk register heat map, covenant tests, FX exposure | RiskRegister, Covenants, FXExposure | K01 debt slots; K02 stress; W07 covenant headroom | W05, W07 | Risk owners and treasury confirm |
| D16 | Actuarial & insurance | Simplified PUC gratuity, insurance register, BI loss | Assumptions, Employees, Results, Insurance | K01 benefits; K02 gratuity payouts; D27 | W02, W05 | Use the actuary's report for accounts |
| D17 | Capex & asset lifecycle | Asset register, Schedule II and tax WDV depreciation, CWIP ageing, capex plan | Setup, Assets, CapexPlan, CWIP, ToKernel | K01 capex\_monthly and da\_monthly; D24 deferred tax | W02, W04 | Plant/finance confirm plan |
| D18 | Real estate & facilities | Lease register, Ind AS 116 view, utilisation, cash rent | Leases, ToKernel | K01 "Rent & facilities"; K02 rent; D03 | W02, W05 | Admin head confirms lease terms |
| D19 | Investor relations | Shareholding movements, guidance vs consensus vs model, disclosure calendar | Shareholding, Guidance, Calendar | W07 investor update; D28 | W07 | Company secretary and CFO approve communications |
| D20 | Corporate development | Partnership, JV, licence, stake and greenfield pipeline | Pipeline, Summary | D21; D09; W01 CFO priorities | W01, W07 | CEO/board decide stage gates |
| D21 | M&A | DCF from a K01 copy of the target, multiples, accretion/dilution, K08 divestiture | DCF, Comps, Multiples, AccretionDilution | K01 target copy; K08; D22 | W07, W10 | Board approves any offer |
| D22 | Cap table | Fully diluted table, round pricing, ESOP top-up, preference waterfall | Holders, Round, Waterfall | D21; D19; K01 opening cash | W07 | Board and shareholders approve allotments |
| D23 | ESG & green finance | Scope 1/2 GHG, intensity per ₹ crore, BRSR KPIs, use of proceeds | Factors, Activity, BRSR, GreenFinance | K01 energy opex; D09; D19 BRSR | W02, W07 | Sustainability lead verifies factors |
| D24 | Tax & transfer pricing | GST cash payable, advance tax, TDS register, TP arm's-length range | GST, AdvanceTax, TDS, TPComparables, TPRange | K02 GST (20th), TDS (7th), advance tax (15th); K01 tax\_rate | W05, W02 | Tax manager/CA confirms; the workspace never files |
| D25 | Boardroom negotiation | BATNA, reservation values, ZOPA, weighted issues, concessions | Issues, Deal | K01 debt terms; D12 → DPO; D26 | W05, W07 | The human negotiates; agent prepares and records |
| D26 | Strategic intuition & judgement | Dated predictions, base rates, pre-mortems, Brier calibration | Predictions, Calibration, Summary | W08 context; W10 hypotheses; W00 base rates | W01, W09, W10 | Executives own predictions |
| D27 | Crisis improvisation | Playbooks, stressed 13-week cash, crisis log, comms | Baseline, Shock, Stressed, Result | K02 baseline; D15; W08 context | W05, W07 | Human crisis lead decides; every decision logged |
| D28 | Ethics & governance culture | Governance scorecard, RPT register, CSR obligation | Scorecard, Index, RPT, CSR | D10; W10 Gate 2; K01 CSR opex | W04, W07, W10 | Audit committee reviews annually; RPTs approved before execution |
| D29 | Informal intelligence networks | Lawful weak signals graded for reliability and credibility, routed to evidence | Signals, Network | Intake evidence; W08 context; D14 | W01, W08, W00 | A signal never changes the champion directly |

### Tamil Nadu notes worth knowing (selected)

- D01: budget cycle Jan–Mar for an April FY; re-forecast each quarter and before Deepavali stocking.
- D02: accounting software must keep an audit trail (Rule 3(1)); one Tally company per FY is common — register each FY as its own source period.
- D03: RoC Chennai and NCLT Chennai have jurisdiction; AGM by 30 Sept, AOC-4 within 30 days and MGT-7 within 60 days of the AGM.
- D04: TN professional tax (half-yearly) and Labour Welfare Fund (31 Jan); basic + DA ≥ 50% under the Labour Codes; employee ids only.
- D06: incentives are salary (TDS u/s 192); dealer schemes are revenue deductions, modelled in D13.
- D07: dealer credit 30–60 days with festival extensions; e-invoice IRN dates are B2B cut-off evidence.
- D08: if the MD approves everything, record that honestly in the DoA.
- D10: keep books at least 8 years (s.128); GST records 72 months from the annual-return due date.
- D12: many Coimbatore/Hosur suppliers are Udyam micro/small; TDS u/s 194Q above ₹50 lakh per supplier per year.
- D13: MRP is GST-inclusive — strip GST before margin analysis.
- D15: TN-rooted banks commonly test DSCR, current ratio and TOL/TNW plus drawing power.
- D18: register tenancies with the Rent Authority (TN tenancy Act 2017).
- D24: intra-TN supplies carry CGST + SGST; supplies to Puducherry or Karnataka carry IGST.
- D28: register promoter-family job work and leases as RPTs (s.188) rather than netting them away.

### Playbooks for the judgement domains (D25–D29)

These qualitative disciplines are made deterministic with structured records and scoring rules: the agent prepares and records; humans decide.

| File | What it says |
| --- | --- |
| `D25_…/negotiation-playbook.md` | Before: define decision rights, value and improve your BATNA, weight issues (sum 100%) with target and walk-away, check ZOPA, plan small reciprocal concessions, anchor with a justified first offer. In the meeting: listen, summarise their interests, trade rather than split, write down agreed points. After: update Issues → Deal decides accept/continue/walk; record in `memory/decisions/`; log predictions in D26. No deception, no fabricated offers. |
| `D26_…/judgement-toolkit.md` | Decision journal, reference class first, pre-mortem, red team, separate signal from story, calibration via Brier score. |
| `D26_…/decision-journal.md` | Table: date, decision, alternatives, key uncertainties, expected outcome (D26 id), what would change my mind, review date. |
| `D27_…/crisis-playbooks.md` | First 72 hours: safety, a crisis lead and single numbers owner, freeze non-essential payments, run D27 stress on the latest K02, call the bank RM before the trough week, log every decision, communicate facts and next update time. Scenarios: cyclone/flood, grid outage, GST portal outage, bank freeze/fraud, key customer default, labour unrest, key person loss, cyber attack. |
| `D27_…/crisis-log.csv` | `timestamp,decision,data_used,owner,expected_effect,review_at,outcome` |
| `D28_…/governance-habits.md` | Eight habits: named approver for every promotion; accuracy shown to the board with misses; corrections and rejected experiments never deleted; RPTs approved before execution; vigil mechanism and POSH; audit trail on; CSR per plan; ethics dilemmas logged. |
| `D28_…/ethics-log.csv` | `date,situation,options,decision,decided_by,principle` |
| `D29_…/intelligence-ethics.md` | Allowed vs never; Admiralty grading (reliability A–F, credibility 1–6) → confidence 0–1; ≥ 0.7 → context-correction proposal + intake evidence; 0.4–0.7 → watch; below → note only; unlawful → discard without recording. |
| `D29_…/stakeholder-map.csv` | `contact_pseudonym,organisation_type,city,topics,relationship_owner,last_contact,notes` — pseudonymous, refreshed quarterly, no personal phone numbers. |

## 8. Tamil Nadu and India reference layer (`01_tamil-nadu/`)

This folder makes openfpa-style FP&A correct for a Tamil Nadu company. Every rate, threshold and due date in it is a starting value "as recorded" on the date in `verification-register.md` (currently 2026-10-18). If the register is older than the period being modelled, the agent asks the human or their CA to confirm, then updates the register — it never guesses.

| File | Contents | Used in |
| --- | --- | --- |
| `fiscal-and-close-calendar.md` | FY April–March (label `FY2026-27`; "tax year" under the Income-tax Act 2025); quarters Q1 Apr–Jun … Q4 Jan–Mar; typical close timetable; year-end tasks | W01, W02 start month, W04 |
| `statutory-calendar.csv` | 32 obligations with law/portal, frequency, due rule and day, months, who it applies to, whether it is a K02 cash flow, linked domain | W05, D03, D24 |
| `tax-reference.md` | GST structure and cash treatment, company income tax, advance tax, tax depreciation, MSME s.43B(h), TDS sections, transfer pricing, TN state levies | W02 tax\_rate, W05, D24 |
| `labour-and-payroll.md` | Labour Codes (in force Nov 2025), EPF, EDLI, ESI, gratuity, bonus, TN professional tax, LWF, minimum wages, overtime, workforce questions | D04, D05, K02 |
| `reporting-framework.md` | Ind AS vs AS, Schedule III, audit and CARO, tax and cost audit, SEBI LODR, revenue recognition, leases, employee benefits; FP&A vs statutory | D03, W07 |
| `schedule-iii-mapping.csv` | 27 Tally groups → typical ledgers → Schedule III line → kernel target → Dr/Cr sign | W03 mapping seeds |
| `seasonality-library.csv` | 15 sector priors (Jan–Dec weights) with drivers; all marked "prior — validate with 24+ months of company data" | W02 |
| `sector-clusters.md` | 12 TN clusters with places and the FP&A questions worth asking | W01, W12, D14 |
| `institutions-and-ecosystem.md` | Regulators, industrial-development bodies, TN-rooted banks and NBFCs, TN-built software, industry associations | D15, D20, D29 |
| `data-sources-india.md` | Export recipes for Tally, Zoho, SAP, NetSuite, Ramco/Marg/Busy, banks, GST portal, TRACES, EPFO/ESIC, MCA21, BSE/NSE, public data, marketplaces | W03 |
| `number-and-language.md` | Indian grouping, lakh/crore, the Indian number format, Tamil board labels | Every report |
| `verification-register.md` | 22 values with where used, official source, last verified | Before relying on any rate |

### Close calendar

| When | Activity |
| --- | --- |
| WD-2 to WD0 | Cut-off: invoices (e-invoice IRN) and GRNs booked |
| WD1–WD3 | Bank reconciliation, sales/purchase registers, GSTR-2B download (\~14th) |
| WD3–WD5 | Payroll provisions (PF/ESI/PT/LWF), accruals, depreciation, inventory valuation |
| By 7th | TDS of previous month deposited |
| By 11th | GSTR-1 (monthly filer) |
| By 15th | PF and ESI remittance |
| By 20th | GSTR-3B and GST cash payment (monthly filer) |
| WD5–WD8 | Flash P&L → freeze line → re-forecast (W04) |
| WD8–WD10 | MIS / board pack in ₹ lakh (W07) |

Year-end: physical stock and fixed-asset verification (CARO 2020), MSME dues review, advance tax true-up by 15 March, statutory audit and tax audit report by 30 September.

### Tax essentials used by the models

- **GST:** intra-TN = CGST + SGST; inter-state and imports = IGST; TN state code 33 (Puducherry 34). Main slabs after Sept 2025: 5% and 18%, 40% for specified goods. Model revenue and COGS **excluding GST**; model **net GST cash** (output − eligible ITC per GSTR-2B + reverse charge) as a K02 disbursement via D24. Blocked or ineligible ITC becomes cost. GST-inclusive AR matters for drawing power — scale DSO in a company workbook if needed. E-commerce TCS 0.5% and TDS 194-O 0.1% are receivable credits.
- **Company income tax:** the Income-tax Act 2025 applies from 1 April 2026 (map old section numbers with the CA). s.115BAA effective 25.168% (K01 default). Normal regime 25% or 30% plus surcharge and cess, MAT 15%.
- **Advance tax:** cumulative 15% by 15 June, 45% by 15 Sept, 75% by 15 Dec, 100% by 15 March.
- **Tax depreciation (WDV):** plant & machinery 15%, computers 40%, buildings 10%, furniture 10%; half rate if used < 180 days.
- **MSME s.43B(h):** dues to Udyam micro/small suppliers are deductible only if paid within the agreed term (max 45 days).
- **TDS:** 192 salary, 194C contractors 1%/2%, 194J 10%/2%, 194I rent 10%/2%, 194H, 194Q 0.1% above ₹50 lakh, 194-O. Deposit by the 7th (March: 30 April).
- **Transfer pricing:** arm's-length range is the 35th–65th percentile with 6+ comparables (D24 › TPRange).
- **TN levies:** professional tax (half-yearly, max ₹2,500/yr), Labour Welfare Fund (31 Jan), stamp duty and registration, TNERC tariffs via TNPDCL.

### Payroll rules (verify)

| Item | Rule used | Cash timing |
| --- | --- | --- |
| EPF employer | 12% of PF wage (EPS on wage capped at ₹15,000) | 15th of next month |
| EPF employee | 12%, deducted | 15th |
| EDLI + admin | ≈ 1% of PF wage | 15th |
| ESI | Employer 3.25%, employee 0.75% up to ₹21,000/month | 15th |
| Gratuity | 15/26 × monthly basic+DA × years (≥ 5), ceiling ₹20 lakh; accrue ≈ 4.81% of basic | On exit |
| Statutory bonus | 8.33%–20% of capped wage, up to ₹21,000/month | Within 8 months of FY end, usually before Deepavali |
| TN professional tax | Half-yearly slabs, max ₹2,500/yr | Half-yearly |
| TN Labour Welfare Fund | Fixed employer + employee amounts (template ₹40 / ₹20) | 31 January |
| Overtime | Twice the ordinary rate | With payroll |

### Reporting framework

Ind AS applies to listed companies and unlisted companies with net worth ≥ ₹250 crore (and their group); AS applies otherwise. Statements follow Schedule III (Division I or II) with MSME-separated payables, ageing, CWIP ageing and ratio disclosures with explanations for > 25% change. K01 is a management model: it does not produce Schedule III statements (D03 does). Label board numbers as management (MIS) unless they tie to audited statements.

### Numbers and language

- Indian grouping 12,34,56,789; lakh = 1,00,000; crore = 1,00,00,000. Board packs state "₹ in lakh" or "₹ in crore" in the header with 2 decimals.
- Spreadsheet format for Indian grouping: `[>=10000000]##\,##\,##\,##0;[>=100000]##\,##\,##0;##,##0`.
- Files store full rupees without separators; only reports format. Write ₹ ("Rs." acceptable in plain text); never mix "INR" and "₹" in one table.
- English is primary for statutory and board documents. Tamil labels are available for 16 common terms (for example Revenue வருவாய், Cash ரொக்கம், Budget வரவு செலவுத் திட்டம்). A fluent reviewer checks Tamil text before it goes out.

### Seasonality priors available

General TN default; consumer durables & furniture retail; knitwear export (Tiruppur); home textiles & handloom; pumps & motors (Coimbatore); automotive components; electronics (EMS); construction & building materials; agri-processing; poultry & egg (Namakkal); fireworks & printing (Sivakasi); hospitality & tourism; education & coaching; IT/ITeS; jewellery retail. They are priors, never facts.

### The verification register

It tracks 22 values, including the s.115BAA rate, Income-tax Act 2025 commencement, advance-tax schedule, GST slabs and due days, QRMP group (22nd), e-commerce TCS/TDS, TDS due day, EPF and ESI rates and ceilings, gratuity ceiling, bonus wage, Labour Codes, MSME 45-day limit, TN PT cap, TN LWF amounts (to confirm), CSR thresholds, grid emission factor (replace with latest CEA value), TP range, Ind AS applicability, SEBI LODR timelines, and the USD/INR placeholder in D11 (always replace). When a value changes, update both the file that uses it and the register.

## 9. Company memory, record schemas and naming

A company's memory is plain markdown and CSV that the user owns. `00_system/schemas/` holds one contract per record type; when a schema and a file disagree, both are fixed in the same change. The templates in `_templates/` are the schemas in usable form — if a record drifts, re-stamp it.

### Registries (CSV)

| File | Header | Rules |
| --- | --- | --- |
| `memory/intake.csv` | `key,topic,question,answer,status,confidence,source_type,sources,alternatives` | Key unique; status confirmed / inferred / conflict; confidence 0–1 (user = 1.0, other evidence default 0.8); source\_type user / local\_file / external / inference; sources and alternatives ` ;  `-separated; answer non-empty |
| `memory/sources/registry.csv` | `source_id,kind,location,entity,currency,periods,extraction_method,refreshed_at,notes` | id `^[a-z][a-z0-9-]*$` and unique; kind local\_file / shared\_folder / accounting\_system / operating\_system / api / public\_filing / manual; entity with GSTIN state code; currency 3 upper-case letters; periods ` ;  `-separated; sorted by id; overwrite needs explicit intent |
| `memory/mappings/registry.csv` | `source_id,source_value,target,status,rationale` | (source\_id, source\_value) unique; mapped needs a target (e.g. `income_statement.revenue`, `opex.payroll`, `balance_sheet.ar`); ignored needs a rationale; source must be registered |
| `memory/models/model-versions.csv` | `model_id,role,created,artifact,source_epoch,description,retired_at` | Role champion (at most one) / challenger / retired; model\_id unique; artifact a relative path |
| `memory/models/promotions.csv` | `from_model,to_model,epoch_id,approved_by,approved_at,notes` | Written only when K05 says PROMOTE; approved\_by a named human |
| `memory/models/workflows.csv` | `name,kind,description,procedure,workbook,working_directory,inputs,outputs,registered_at` | Kind forecast / close / cash / research / report / connector / custom; procedure = runbook path; paths relative without `..`; registration never runs anything |
| `memory/index.csv` | `path,category,title,keywords` | Derived and rebuildable; one row per `.md`/`.csv`/`.yaml` under `memory/` except itself and `context-pack.md` |
| `portfolio/portfolio.csv` | `client_path,business_type,notes` | Business type is the clustering tag (e.g. `tn-furniture-d2c-dealer`) |
| `portfolio/library/priors/<type>.csv` | `driver,value,support,cross_client_holdout_delta,n_folds,promoted_at,approved_by` | Human-ratified only |

### Intake keys

**11 core keys (all must be known for readiness):** business\_model, revenue\_model, customer\_channels, collections, supplier\_payments, seasonality, entities, financing, data\_sources, planning\_cadence, cfo\_priorities.

**5 Tamil Nadu keys (topic `tn_statutory`, before W03):** gst\_profile, tds\_and\_tax\_regime, payroll\_statutory, msme\_and\_incentives, seasonal\_calendar\_tn.

Topics: business, cash\_cycle, finance\_structure, planning, tn\_statutory, other. Any other key is allowed (topic `other`).

### Markdown records

| Record | Location | Key fields and rules |
| --- | --- | --- |
| Correction | `memory/corrections/<YYYY-MM-DD>-<name>.md` | type parametric / structural / context; target; status open / applied / superseded; date; override {path, value} for parametric. Body: Was off / Correction / Why. |
| Snapshot | `memory/forecasts/<label>.snapshot.md` + `<label>.assumptions.xlsx` | label; created (supplied, never invented); assumptions path; predicted {ending\_cash, ebitda, revenue, gross\_margin}; score added once after close {fitness, per\_line, weights}. Immutable otherwise. |
| Experiment | `memory/experiments/<slug>.experiment.md` | status draft / proposed / accepted / rejected / reverted; hypothesis, snapshot, cfo\_question, rationale, evidence, training and holdout periods, files\_changed, metrics before/after, checks, decision. Accepted needs evidence, files\_changed and all checks pass; draft/proposed have no decision. |
| Research objective | `memory/research/objective.md` | metrics (name, weight > 0, direction), hard\_checks, min\_improvement ≥ 0, complexity\_penalty ≥ 0, max\_metric\_regression > 0 or blank. Defaults: ending\_cash\_error 0.4, ebitda\_error 0.3, revenue\_error 0.2, gross\_margin\_error 0.1; min 0.02; penalty 0.01. The CFO owns it. |
| Research epoch | `memory/research/epochs/<epoch_id>.md` | status generated / evaluated / discarded / proposed / promoted; champion and challenger ids, memory sources, files, periods, checks, evaluation from K05. Discarded epochs are kept forever. |
| Decision | `memory/decisions/<YYYY-MM-DD>-<slug>.md` | date, decision, decided\_by (named human), status proposed / approved / rejected / superseded, evidence. Body: context, options, decision, consequences, review date. |
| Connector | `connectors/<name>/connector.md` + `fixtures/source.csv` + `validation-log.md` | name = folder; source\_id; auth\_method none / host\_environment / mcp; account and amount columns (must differ); fixture path; expected\_totals; live\_ready; live\_recipe. Body: export recipe, normalisation, failure behaviour, validation log. |
| Domain record | `domains/Dnn_<slug>/notes.md` + workbook | domain, owner, refreshed\_at, feeds, status draft / reviewed / in-use |
| Model config | K01 › Assumptions | See section 6 (the EntityConfig contract) |

### Naming and ids

| Thing | Rule | Example |
| --- | --- | --- |
| Company slug | lowercase letters, digits, hyphens; optional city suffix | `kaveri-chairs-coimbatore` |
| source\_id, connector, workflow name | `^[a-z][a-z0-9-]*$` | `tally-pl-monthly` |
| Correction slug | `<YYYY-MM-DD>-<short-name>` (= filename) | `2026-11-02-deepavali-spike` |
| Experiment slug, epoch\_id | `^[a-z0-9][a-z0-9._-]*$` | `kvr-fy2627-003-pongal-lag` |
| model\_id | `<company>-<what>-<version>` | `kvr-k01-v2-dealer-dso` |
| Snapshot label | the period or cycle | `2026-10`, `LE-Oct-FY2026-27` |
| Fiscal year / quarter | `FY<start>-<end yy>`; Q1 = Apr–Jun | `FY2026-27 Q3` |
| Dates | ISO `YYYY-MM-DD` in files | `2026-10-18` |
| Amounts in files | full rupees, no separators, `-` for negative | `-146000` |
| Amounts in reports | ₹ with Indian grouping or a stated unit | `₹1,46,000` · `₹1.46 lakh` |
| Workbook copies | `<kernel id>_<purpose>.xlsx` in `models/` | `K01_champion.xlsx`, `K01_challenger-dso.xlsx` |
| Domain records | `domains/Dnn_<slug>/` | `domains/D24_tax-transfer-pricing/` |

Paths are always relative to the company root, never absolute, never containing `..`. Reserved names: `total` (channel/opex), `index.csv` and `context-pack.md` (never indexed).

### Answering "where are we?" from files

| Question | Read |
| --- | --- |
| Is the company onboarded? | `intake.csv` readiness via K10 and the decision box in `initial-model-architecture.md` |
| Which sources are trusted? | Source and mapping registries plus reconciliation evidence |
| What is the live model? | `model-versions.csv` (role = champion) |
| How accurate are we? | `scorecard.md` (rendered by K04) |
| What did we learn or reject? | `learnings.md`, `experiments/`, `research/epochs/` |
| What has a human corrected? | `corrections/*.md` |

## 10. BI, dashboards and board templates (`05_bi-and-presentation/`)

Kernel outputs become things people look at without code: BI tools read a CSV star schema, office suites open the templates. Before anything is published, the CFO compares headline tiles with K01 › Summary and K02 › Runway.

### Feeding a dashboard

1. After each refresh, copy K01 › Export\_Rows (values) into `companies/<slug>/output/bi/fact_monthly_model.csv`, K02 › Weekly into `fact_cash13.csv`, and mapped actuals into `fact_actuals.csv`.
2. Point the BI tool's file or folder connector at `output/bi/` and press refresh.
3. Configure relationships and measures by clicks from `relationships.csv` and `measures.csv`. No scripts are stored.

### Data model (`data-model/`)

| Table | Columns (headers only; filled per company) |
| --- | --- |
| `fact_monthly_model` | company\_slug, model\_id, scenario, month\_no, period, indian\_fiscal\_year, fiscal\_quarter, revenue, cogs, gross\_profit, opex, ebitda, da, interest, pretax\_income, tax, net\_income, wc\_cash\_impact, operating\_cash\_flow, capex, principal, free\_cash\_flow, change\_in\_cash, ending\_cash, ending\_debt, ar\_balance, ap\_balance, inv\_balance |
| `fact_actuals` | company\_slug, source\_id, period, account, target, amount |
| `fact_cash13` | company\_slug, run\_date, week, week\_starting, receipts, disbursements, net\_cash, ending\_cash |
| `fact_scorecard` | company\_slug, label, created, fitness, err\_ending\_cash, err\_ebitda, err\_revenue, err\_gross\_margin |
| `dim_period_india` | Complete Indian fiscal calendar Apr 2020 – Mar 2036 (192 months): period, month start/end, calendar year and month, month name, fiscal year, fiscal quarter, fiscal month no, days, festival flags |
| `dim_account` | target, statement, line group, sign, Schedule III line, description |
| `dim_channel` | company\_slug, channel, channel\_type, notes |
| `dim_entity` | company\_slug, entity, gstin\_state\_code, city, district, business\_type, functional\_currency |

Scenarios in `fact_monthly_model`: `champion`, `LE-<month>`, `challenger-<slug>`, `stress-<id>`. Relationships: facts join `dim_period_india` on period (YYYY-MM), `dim_account` on target, and `dim_entity` on company\_slug (all many-to-one). `data-dictionary.csv` describes each column.

**Measures (`measures.csv`):** Revenue (ex-GST), Gross margin % (ratio of sums, never an average of monthly %), EBITDA, EBITDA margin %, Net income, Free cash flow (excludes one-time proceeds), Ending cash (last period — never summed), Net debt, DSO (implied), Forecast fitness, 13-week trough (raw, unfinanced), First negative week, Budget variance.

### Dashboard specifications (`dashboards/`)

| Dashboard | Audience | Refresh | Headline tiles | Charts |
| --- | --- | --- | --- | --- |
| CFO cockpit | CFO, MD, board | After every close and cash run | Revenue FYTD vs budget, GM %, EBITDA and margin, ending cash and net debt, 13-week trough and first negative week, fitness and trend | Revenue and EBITDA actual vs LE vs budget; ending cash with CC limit line; fitness over time |
| 13-week cash runway | CFO, treasury, bank | Weekly | Opening cash, trough and week, first negative week, suggested line, headroom vs drawing power | Receipts vs disbursements; ending cash with zero and limit lines; top 10 disbursements |
| Close and variance | CFO, business heads | Monthly | Actual vs plan and LE for revenue, GM, EBITDA, cash; count of material variances; variance by driver | Budget → actual waterfall; PVM bridge (D13); variance table |
| Forecast accuracy and learning | CFO, audit committee | After each scored close | Latest fitness, lines with persistent misses, experiments accepted/rejected, promotions with approver | Per-line error heatmap; fitness trend |
| TN statutory compliance | Controller, company secretary | Weekly | Due dates next 30 days, GST due (20th), TDS (7th), PF/ESI (15th), MSME dues > 45 days, overdue document reviews | Obligation calendar strip; MSME ageing; GST payable vs ITC |

Shared rules: follow the chart standards; state the unit in every title; stocks take the last period, flows sum, ratios are ratios of sums; mark pre-close months.

### Chart standards

1. The title states the takeaway; the subtitle states unit and scope.
2. Trend → line; few categories → bars; composition → stacked columns (≤ 5 series); bridge → waterfall; error distribution → heatmap or dot plot. No pies over 3 slices, no 3-D, no dual axes unless the unit is shared.
3. Colour roles from `theme/tnfpa-bi-theme.json`: actual navy `#1F3864`, latest estimate teal `#1B998B`, budget grey `#8C8C8C`, challenger amber `#E09F3E`, alert red `#9E2A2B`, ok green `#3D9970`. Fonts Segoe UI / Segoe UI Semibold.
4. Reference lines for zero, CC/OD limit and covenants.
5. Indian grouping or a stated unit, 2 decimals in ₹ lakh / crore.
6. Pre-close months lighter or hatched with a footnote; forecast visually distinct from actuals.
7. Text contrast ≥ 4.5:1; never rely on red/green alone.
8. Optional Tamil second line under English axis titles.

### Templates (`templates/`) — copy into `output/` before editing

| Template | Contents |
| --- | --- |
| `board-briefing-template.pptx` | 8 slides with native, editable charts (right-click › Edit Data): 1 title and one-line takeaway (with Tamil subtitle); 2 headline tiles (revenue, EBITDA, net income, ending cash); 3 what changed; 4 revenue and EBITDA by month (paste Export\_Rows); 5 13-week cash (trough, first negative week, recommended action); 6 risks; 7 the ask; 8 appendix (fitness, pre-close months, cash basis, unit). Every slide footer: "Management (MIS) numbers · ₹ excl. GST · source: K01 champion / K02 runway". |
| `board-memo-template.docx` | To/From/Date/Unit/Basis header; headline; what changed; 13-week runway; risks; the ask; caveats; resolution sought, approved by, date. |
| `monthly-mis-inr-lakh.xlsx` | Sheets README, Checks, Paste\_K01, Paste\_Budget, MIS\_lakh. Paste Export\_Rows values (and optional budget); MIS\_lakh shows months in ₹ lakh with Indian FY totals; Checks prove the lakh view ties to rupees. |
| `communications.md` | Lender update email (revenue vs plan, EBITDA, unfinanced 13-week trough, the ask, covenants, drawing-power statement attached); internal WhatsApp/Teams note (≤ 6 lines); investor update outline (headline, what changed, cash and runway, risks, asks, accuracy of last forecast). No unpublished price-sensitive information outside the disclosure process. |

Placeholders to replace include `{{company}}`, `{{period}}`, `{{unit}}`, `{{horizon}}`, `{{revenue}}`, `{{ebitda}}`, `{{net_income}}`, `{{ending_cash}}`, `{{what_changed_1–3}}`, `{{trough}}`, `{{trough_week}}`, `{{first_negative_week}}`, `{{recommended_action}}`, `{{risk_1–3}}`, `{{the_ask}}`, `{{fitness}}`, `{{pre_close}}`, `{{cash_basis}}`, `{{caveats}}` and `{{takeaway}}`.

## 11. Templates, examples and the openfpa coverage map

### Templates (`_templates/`) — copy, never start from a blank page

| Template | Copy to | When |
| --- | --- | --- |
| `company/` | `companies/<slug>/` | Init (W01 step 1) |
| `correction.md` | `memory/corrections/<YYYY-MM-DD>-<name>.md` | W08 |
| `snapshot.md` | `memory/forecasts/<label>.snapshot.md` | W04 / W09, every forecast |
| `experiment.md` | `memory/experiments/<slug>.experiment.md` | W09, before any model change |
| `epoch.md` | `memory/research/epochs/<epoch_id>.md` | W10, each challenger |
| `decision.md` | `memory/decisions/<YYYY-MM-DD>-<slug>.md` | Any approval or gate |
| `connector/` (connector.md, fixtures/source.csv, validation-log.md) | `connectors/<name>/` | W03 recurring access |
| `generated-skill/SKILL.md` | `skills/<name>/` | W12 after approval |
| `generated-agent/AGENT.md` | `agents/<name>/` | W12 after approval |
| `domain-record/notes.md` | `domains/Dnn_<slug>/` (plus the domain workbook) | When a domain feeds the model |

The company template ships with empty registries (headers only), a placeholder business profile with five "Not yet known" sections, an empty scorecard and learnings file, the openfpa-default research objective, and a `CONTEXT.md` in every sub-folder explaining its purpose. A generated skill's frontmatter needs `name`, `description` ("Use when…"), `justified_by` and `workbook`; a generated agent needs `name`, `role`, `justified_by`, `reads` (2k–8k tokens), `writes` and `gates`.

### Worked examples (`examples/`) — read-only; never copy their numbers

**Kaveri Chairs, Coimbatore (`kaveri-chairs-coimbatore/`)** is a complete, synthetic Tamil Nadu company workspace and the best pattern to copy for a real TN company.

| Stage shown | Where |
| --- | --- |
| 16 intake facts with citations (11 core + 5 TN) | `memory/intake.csv`, `business-profile.md` |
| Gate 1 approved by S. Meenakshi (CFO) and R. Senthil (MD), 2026-03-22 | `memory/decisions/initial-model-architecture.md` |
| Three registered sources (Tally P&L, AR ageing, bank flash) and 20 mapping rules (4 ignored with rationale: two interest ledgers, two output GST ledgers) | `memory/sources/`, `memory/mappings/` |
| K03 reconciliation of the Tally Dr/Cr export with lakh commas — no duplicates, no unmapped | `memory/sources/evidence/` |
| A fixture-validated, live-ready connector `tally-pl-monthly` (accountant exports on WD4) | `connectors/tally-pl-monthly/` |
| FY2026-27 budget champion `kvr-k01-v1-budget` with one applied parametric correction (dealer November seasonality 1.45) and one context correction (Nov 2025 cyclone) | `models/K01_champion.xlsx`, `memory/corrections/` |
| 13-week cash run with GST/TDS/PF/ESI/advance-tax dates | `models/K02_2026-04-06.xlsx` |
| Domain records D04 payroll, D12 MSME procurement, D24 GST/TDS | `domains/` |
| Budget snapshot, four registered workflows, cash-runway note, board briefing, deck and memo | `memory/forecasts/`, `memory/models/workflows.csv`, `output/` |

Headline results: FY2026-27 revenue ₹35,00,00,000, EBITDA ₹6,29,00,000, net income ₹3,50,22,779, ending cash (unfinanced) ₹4,54,45,776; 13-week trough −₹31,85,000 in week 5 (week starting 4 May 2026), driven by a ₹1.35 crore LC retirement. Recommended action: arrange at least ₹36,63,000 (trough + 15% buffer) before week 5.

**Ridgeline parity (`ridgeline-parity/`)** loads openfpa's synthetic Ridgeline Chair Co. unchanged into K01, K02 and K06 with GOLDEN check rows: revenue 6,000,000; EBITDA 824,000; net income 572,651; ending cash 720,418; 13-week trough −146,000 in week 7 with first negative week 3; SKU Pareto breakpoint 4. It is in USD with western grouping. Its `data/fixtures/` (QuickBooks, NetSuite, Shopify) are for practising K03 reconciliation.

**Fox Factory public proof (`foxfactory-public-proof/`)** rebuilds openfpa's SEC-data example (NASDAQ: FOXF) in four phases: A reproduces FY2024 and FY2025 within 1%; B runs FY2025 holdout research (epoch 001 discarded, gain +5.5% but regression guard failed; epoch 002 proposed at +61.4%, not promoted); C forecasts FY2026–27 with K07 segments; D runs the Marucci divestiture grid in K08. Its `models/pipeline-runbook.md` shows how to pull public data by recipe. It also documents where the engine strains: no segment layer (solved by `segment-rollup`), a non-cash goodwill impairment bridged outside, discrete tax benefits bridged, an undisclosed unit treated as a labelled sensitivity, quarterly reporting vs a monthly engine, and only three annual observations.

**Generated skills (`generated-skills/`)** contains `sku-profitability` (K06) and `segment-rollup` (K07 → K01) as patterns for W12.

To re-verify any example: open each workbook in a spreadsheet engine, let it recalculate, and read Checks → OVERALL = PASS.

### openfpa coverage map

`00_system/coverage/openfpa-coverage-map.csv` lists all 206 files of openfpa with their replacement and treatment: 135 replaced, 21 carried, 19 rewritten, 16 superseded, 11 converted, 3 not needed and 1 summarised. `coverage-notes.md` explains the method and the deliberate differences:

| Area | openfpa | Here |
| --- | --- | --- |
| List sizes | Unbounded | Fixed slots; larger companies get a bespoke workbook |
| Two applied corrections on one path | Later file silently wins | Checks FAIL until one is superseded |
| Holdout fit | Python function passed in | Agent fits a K01 copy on fit periods only |
| Connectors | Generated Python, run in fixture mode | Recipe + redacted fixture + golden totals, validated by K03 at tolerance 0 |
| CLI output | JSON envelope and exit codes | A short result block (success / failed / invalid) |
| Memory index | Every word of every file | Path, title, headings and frontmatter words |
| Prior validation | Automatic per fold | One K01 copy per fold, fitness entered in K09 |
| Workbook verification | Python compares workbook with a data frame | The workbook is the engine; identity checks and GOLDEN parity rows |
| Tests and CI | pytest on Python 3.11–3.13 | Checks sheets recalculated by any engine |

The map also lists `00_system/command-equivalents.md` (24 CLI commands) and `kernel-equivalents.md` (every `pyfpa` function → its workbook and sheet) as the reference for anyone coming from openfpa.

## 12. Task procedures (the 24 file procedures)

Every openfpa command is now a deterministic file procedure in `00_system/command-equivalents.md`. Each one ends with a short result block in the agent's reply:

```markdown
result: success | failed | invalid
command: <name>   company: companies/<slug>
evidence: <workbook + sheet, or file paths read>
data: <the fields the procedure returns>
```

`invalid` = a required input is missing or malformed (fix it before retrying). `failed` = the procedure ran but a check failed (report it; never proceed as if it passed). Below, C = `companies/<slug>`.

### Workspace and data

| # | Procedure | What the agent does | Returns |
| --- | --- | --- | --- |
| 1 | status | If `C/memory/` is missing → not initialised. Else read intake (facts by status), K10 Readiness, profile and proposal existence, model, promotion, workflow, source and mapping registries, connector names. | initialized, business name, intake\_ready, fact counts, next question topic and count, champion, challenger and promotion counts, workflows, source/mapping counts, connectors |
| 2 | init | Copy `_templates/company/` to `companies/<slug>/`; never overwrite an existing company (only add missing files); put the name in `MEMORY.md`, `intake-notes.md` and `CLAUDE.md`. | Path, created files |
| 3 | doctor | Run the 12-line checklist (section 13). Healthy = zero errors. | healthy, checks, error and warning counts |
| 4 | inspect-data | List files under a folder (skipping hidden, `.git`, `node_modules`, `venv`, `__pycache__`, `build`, `dist`, `memory`), paste path + bytes into K03 › Inspect, read Inspect\_Summary; truncate at 500 files and say so. | Files with category, counts, missing priority categories, truncated flag |
| 5 | source-profile | Paste header + rows into K03 › Profile; write `memory/sources/evidence/<source_id>-profile-<date>.md`. Never modify the source. | Rows, columns, empties per column, duplicate rows |
| 6 | source-register | Append a row to `sources/registry.csv`; an existing id without explicit overwrite → failed. Keep sorted. | The record |
| 7 | source-list | Read the source registry (optionally by kind). | Sources |
| 8 | mapping-register | Append to `mappings/registry.csv` (mapped needs target; ignored needs rationale; source must be registered). | The rule |
| 9 | mapping-list | Read and filter the mapping registry. | Mappings |
| 10 | reconcile-source | Copy K03; set source\_id, tolerance (default 0.01), allow-unmapped; paste mapping rows, account/amount columns and expected totals; save as `evidence/<source_id>-reconcile-<date>.xlsx` with a `.md` summary. | Row count, totals, mapped totals, duplicates, unmapped, ignored, variances, passed |

### Connectors and intake

| # | Procedure | What the agent does | Returns |
| --- | --- | --- | --- |
| 11 | connector-list | List `C/connectors/*/connector.md` (optionally by source\_id). | Manifests |
| 12 | connector-scaffold | Preconditions: source registered, mappings complete, architecture approved, fixture explicitly redacted. K03 on the fixture must pass with ≥ 1 mapped total. Copy `_templates/connector/`, store the fixture and golden totals, fill the recipe. | Manifest, reconciliation |
| 13 | connector-validate | Copy K03, tolerance 0, paste `fixtures/source.csv`, expected = `expected_totals`. Must pass. Log the result. Fixture mode only. | Manifest, reconciliation, passed |
| 14 | intake-next | Paste `intake.csv` into K10 › Facts; read Readiness (≤ 3 questions, one topic). | Questions with key, topic, prompt, reason, current answer |
| 15 | intake-record | Compute the new row with K10 › RecordFact and replace that key's row in `intake.csv`. Empty answer → invalid. | Fact, intake\_ready |
| 23 | onboarding-render | Only when `intake_ready` = TRUE (else failed). Fill K10 › Proposal; copy Profile → `business-profile.md` and Proposal → `initial-model-architecture.md`. Then stop for approval. | Profile and proposal paths |

### Models, corrections and learning

| # | Procedure | What the agent does | Returns |
| --- | --- | --- | --- |
| 16 | entrypoint-list | Read `models/workflows.csv` (optionally by kind). | Workflows |
| 17 | entrypoint-register | Append to `workflows.csv`; "command" = runbook + workbook paths. Registration never runs anything. | Workflow |
| 18 | correction-record | Copy `_templates/correction.md` to `corrections/<YYYY-MM-DD>-<name>.md` and fill it. | Correction |
| 19 | correction-list | Read correction frontmatter (optionally by status). | Corrections |
| 20 | scorecard-render | Transcribe every snapshot (chronological) into K04 › Snapshots; copy K04 › Scorecard column A into `scorecard.md` verbatim (overwrite allowed — it is derived). | Snapshot and scored counts, path |
| 21 | experiment-list | Read experiment frontmatter (optionally by status). | Experiments |
| 22 | context-pack | Rebuild `index.csv`, paste into K11 › Index with task tokens in Task; copy Pack column A into `context-pack.md` (temporary); open each listed file for excerpts. | Pack path, hits |
| 24 | model-export | Copy K01 to the requested path, fill Assumptions from company config, confirm Checks PASS. The K01 copy is the live-formula model. | Output path, checks |

### Everyday recipes

**Run a month-end close.** Export the closed month from Tally → save as `data/raw/tally-pl-<YYYY-MM>.csv` → ask "Run the October close". The agent reconciles with K03, builds `K01_LE-<month>.xlsx`, writes a D01 variance, scores last month's snapshot, takes a new snapshot and writes `output/<period>-close.md`. You review the narrative and the posture.

**Check cash for the next 13 weeks.** Give the agent the latest bank balance (say whether it is bank flash or GL) and any known lumpy items. It builds `K02_<date>.xlsx` with statutory dates and returns the trough, its week, the first negative week and a recommended line size.

**Prepare a board or shareholder meeting.** Ask for a board briefing for the period. The agent assembles the K01 headline and K02 runway, writes what changed, risks and the ask, fills the 8-slide deck and the memo, and adds Tamil labels if you want them. You sign off before anything is sent.

**Tell the model it is wrong.** Say what is off and why ("Pongal week collections always slip a week"). The agent classifies the correction, echoes the concrete change, and applies it only after you confirm.

**Add a domain.** Ask, for example, "Set up payroll properly". The agent copies D04 into `domains/`, fills it from your payroll summary (employee ids only), passes Checks, and transfers the loaded cost and PF/ESI flows into K01/K02 once the owner reviews it.

**Update a statutory rate.** Confirm the new value with the CA, change it in the workbook or file that uses it, and update the row in `verification-register.md` with source and date.

**Add a second client (practice use).** Run init for the new slug, add a row to `portfolio/portfolio.csv` with its business type, and onboard normally. Once three clients of a type have scored snapshots, W11 can propose shared priors.

## 13. Status, doctor, troubleshooting, FAQ and glossary

### Status (derived by scanning, never stored)

| Field | Rule |
| --- | --- |
| initialized | `memory/` exists with `intake.csv` |
| intake\_ready | K10 Readiness after pasting `intake.csv` (all 11 core keys known) |
| next question topic | K10 Readiness |
| onboarding stage | none → intake → proposal written → **approved** (box ticked with name and date) → scaffolded (a K01 copy registered as champion) → operating (≥ 1 snapshot) → learning (≥ 1 scored snapshot) |
| champion / challengers | `model-versions.csv` role column |
| sources / mappings / connectors / workflows | Registry row counts; folder count of `connectors/` |
| open corrections | `corrections/*.md` with `status: open` |
| last close | Latest snapshot with a score |

### Doctor (healthy = zero errors)

| # | Check | Error when |
| --- | --- | --- |
| 1 | Workspace | `companies/<slug>/memory/` missing |
| 2 | Directories | Any of sources, mappings, corrections, forecasts, experiments, decisions, models, research missing under `memory/` |
| 3 | Intake | Header differs from schema; invalid status, confidence or source\_type; repeated key; empty answer |
| 4 | Research objective | File missing; weight ≤ 0; duplicate metric or hard-check names; min\_improvement or complexity\_penalty < 0 |
| 5 | Model registry | Wrong header; more than one champion; duplicate model\_id; promotion without approved\_by |
| 6 | Workflow registry | Wrong header; duplicate name; invalid kind; absolute path or `..`; empty description |
| 7 | Source registry | Wrong header; duplicate or invalid id; currency not 3 letters; empty location, entity or extraction method |
| 8 | Mapping registry | Wrong header; duplicate (source\_id, source\_value); mapped without target; ignored without rationale |
| 9 | Connector contracts | `name` ≠ folder; missing fixture; empty expected\_totals; `live_ready: true` without a live recipe |
| 10 | Corrections | Frontmatter lacks type, target, status or date, or has invalid values |
| 11 | Snapshots | Frontmatter lacks label, created or predicted, or a score without fitness |
| 12 | Workbooks | A registered workbook whose Checks OVERALL ≠ PASS (warning if not recalculated since last edit) |

Warnings never block; errors do. A healthy report is evidence, not reasoning.

### Troubleshooting

| Symptom | Likely cause | What to do |
| --- | --- | --- |
| Checks OVERALL = FAIL on a blank kernel copy | K01, K04, K08, K09 and K11 need minimum inputs | Enter the inputs; FAIL on a blank master is intended |
| OVERALL = FAIL after editing | An input rule or identity broke | Find the failing numbered check and fix the input or structure — never a formula or tolerance |
| `#NAME?` or `#VALUE!` in Checks | Viewer that does not support a name or format, or a text value in a number cell | Recalculate in a full engine (Excel, LibreOffice, Google Sheets); check typed values |
| Values look empty or stale | Workbook not yet recalculated | Open and recalculate in the engine; if none is available, ask a human to do it |
| Indian grouping shows oddly | Engine lacks conditional formats in `TEXT()` | Set `number_style` to western and use `display_divisor` (₹ lakh) |
| K03 fails on duplicates | Same ledger name under two groups, or repeated rows | Rename or combine in the source export; never delete silently |
| K03 fails on unmapped accounts | A new ledger appeared | Add a mapping or an ignore with rationale; re-run |
| K03 "amounts do not parse" | Unusual format in the amount column | Check symbols, Dr/Cr suffix and the Cr sign on Setup |
| Connector validation fails | Fixture changed or golden totals outdated | Re-scaffold deliberately; log the change; never loosen tolerance |
| K04 will not score | Missing or zero actuals | Supply actuals; missing evidence is never perfect performance |
| Two corrections on one path fail K01 | Two applied rows on the same path | Supersede one (status `superseded`) |
| Correction path does not resolve | Path not in K01 › ValidKeys or wrong index | Use 0-based indexes and a listed key |
| Large month-1 cash swing | Working-capital seam: opening balances differ from implied levels | Set opening AR/AP/inventory to month-1 implied balances, or record the gap as a known month-1 item |
| K02 shows a negative trough | Raw, unfinanced view | It means "needs a draw" — size the line, compare with drawing power |
| Business has more than 8 channels or a different shape | K01 slots exceeded | Build a company-specific workbook with parity rows; do not merge channels |
| Agent will not scaffold | Gate 1 not recorded | Tick "Approved to scaffold" and add `Approved by: <name>, <date>` |
| Challenger will not promote | Not eligible, or no named approver | Check K05 › Epochs (hard checks, guard, gain) and fill Promotion with the approver |

### FAQ

**Do I need to install anything?** No. You need an agent that edits files and a spreadsheet engine. Google Sheets works: upload, recalculate, download as `.xlsx`.

**Can the agent log in to Tally, the bank or the GST portal?** Only with your explicit approval, and only through a host tool (an approved MCP server or the system's own export). The workspace never stores credentials.

**Why does the model ignore GST?** Revenue and costs are modelled ex-GST; net GST cash is a separate dated outflow in K02 (via D24). Blocked ITC is treated as cost.

**Are the numbers audited?** No. K01 is a management (MIS) model; label board numbers as such. D03 produces Schedule III totals from the mapped TB.

**Can I edit a snapshot or experiment after the fact?** No. Snapshots get their score once; other history is superseded by a new file and a status change.

**What happens if the agent's new model is better?** It proposes it. Only a named human can promote it (Gate 2).

**Can I use it for many clients?** Yes. Add each to `portfolio/portfolio.csv` with a business type. Only ratified, abstracted priors are shared; raw data stays in each company folder.

**Can I present in Tamil?** Yes — add Tamil labels from `number-and-language.md` and have a fluent reviewer check them.

**Is it safe to store payroll?** Use employee ids and aggregates only; never salary-by-name, PAN, Aadhaar or bank account numbers.

### Glossary

| Term | Meaning here |
| --- | --- |
| ICM | Interpretable Context Methodology: folder structure as agent architecture |
| openfpa | The open-source FP&A toolkit this workspace replaces |
| Factory / product | Stable numbered folders vs per-company output |
| Kernel (K01–K11) | The verified calculation workbooks |
| Domain (D01–D29) | A finance discipline module that feeds drivers to the kernel |
| Workflow (W00–W12) | A stage contract the agent follows |
| Champion / challenger | The live model / a candidate model under test |
| Epoch | One evaluated challenger in the research loop |
| Fitness | Weighted absolute forecast error; lower is better |
| Holdout | Periods kept out of fitting and used only for scoring |
| Snapshot | An immutable record of one forecast and its later score |
| Correction | A typed human fix: parametric, structural or context |
| Freeze line | The boundary between closed (actual) and forecast months |
| Posture | Plan, latest estimate or run-rate |
| Golden totals | Expected mapped totals stored in a connector for tolerance-0 validation |
| Fixture | A redacted sample export used to validate a connector |
| Drawing power | The usable cash-credit limit based on stock and debtor statements |
| ITC / GSTR-2B | GST input tax credit / the auto-drafted statement that makes it claimable |
| QRMP | Quarterly return, monthly payment GST scheme |
| DSO / DPO / DIO | Receivable, payable and inventory days (30-day months in K01) |
| NOL | Opening unabsorbed tax loss used by K01 |
| WD | Working day of the close |
| MIS | Management information system reporting (not statutory) |
| ₹ lakh / ₹ crore | 1,00,000 / 1,00,00,000 rupees |
