# The system in one screen

## What this is

An **agent-native FP&A workbench**: a stable no-code finance kernel (spreadsheets), an operating
contract (markdown), durable company memory (markdown + CSV) and an evidence-gated research loop,
so one AI agent can learn one company, build the FP&A system that fits it, and improve it as
actuals arrive — exactly the job openfpa did, with no programming language anywhere.

| openfpa had | This workspace has |
|---|---|
| `pyfpa/` Python kernel | `02_kernel/` eleven verified spreadsheet engines (K01–K11) |
| `openfpa` CLI (24 JSON commands) | file procedures in `00_system/command-equivalents.md` |
| `AGENTS.md` / `CLAUDE.md` / `skills/` | `CLAUDE.md` + `00_system/operating-contract.md` + `03_workflows/` |
| `.fpa/` company memory | `companies/<slug>/memory/` (visible, same contracts) |
| `connectors/generated/` code | `companies/<slug>/connectors/<name>/` export recipes + fixtures + golden totals |
| `models/generated/` code | `companies/<slug>/models/` copies of kernel workbooks |
| `skills/generated/`, `agents/generated/` | `companies/<slug>/skills/`, `.../agents/` markdown |
| tests + CI | each workbook's `Checks` sheet + `examples/*` golden parity |
| (not in openfpa) | `01_tamil-nadu/` localisation, `04_domains/` 29 enterprise domains, `05_bi-and-presentation/` |

## Layers (factory vs product)

```
FACTORY (stable, configure once)                 PRODUCT (new every run)
00_system/      rules, schemas, equivalents      companies/<slug>/memory/    facts, evidence, history
01_tamil-nadu/  local law, calendars, context    companies/<slug>/models/    company workbooks
02_kernel/      calculation engines (read-only)  companies/<slug>/output/    briefings, decks, packs
03_workflows/   stage contracts                  companies/<slug>/domains/   domain records
04_domains/     29 domain modules                portfolio/library/          ratified priors & skills
05_bi-and-presentation/ data model, templates
_templates/     stamps for new things
```

## The lifecycle (one company)

```
W01 learn-business ──► [GATE 1: architecture approval] ──► W02 scaffold-model ──► W03 configure-actuals
        ▲                                                                              │
        │                         operate (every month / on demand)                    ▼
   W11 portfolio ◄── W10 research-loop ◄── W09 backtest-learn ◄── W04 monthly-close ──► W05 cash-runway
   (cross-client)   [GATE 2: champion            ▲                      │                    │
                     promotion approval]          └── W08 capture-correction (any time)       ▼
                                                                  W06 live-excel-model ──► W07 board-briefing
W00 cfo-judgment is consulted inside every step.  04_domains feed drivers into K01/K02 at W02, W03, W04, W05.
```

Human gates (never skip): **Gate 1** — architecture proposal approved before any model, connector,
skill or agent is generated. **Gate 2** — a challenger replaces the champion only with a named human
approval. Also: ask before any external access; confirm a correction's interpretation before `applied`.

## State machine (the filesystem is the state)

| Question | Answer by reading |
|---|---|
| Is the company onboarded? | `memory/intake.csv` readiness via `02_kernel/K10…` + `memory/decisions/initial-model-architecture.md` decision box |
| Which sources are trusted? | `memory/sources/registry.csv`, `memory/mappings/registry.csv`, reconciliation evidence in `memory/sources/evidence/` |
| What is the live model? | `memory/models/model-versions.csv` (role = champion) |
| How accurate are we? | `memory/scorecard.md` (rendered by K04, never hand-edited) |
| What did we learn / reject? | `memory/learnings.md`, `memory/experiments/`, `memory/research/epochs/` |
| What has a human corrected? | `memory/corrections/*.md` |

## How a calculation happens (no code)

1. Copy the kernel workbook into the company folder. 2. Type inputs into pale-yellow cells only.
3. The spreadsheet engine recalculates (Excel, LibreOffice Calc, Google Sheets, OnlyOffice, Zoho Sheet,
WPS). 4. Read `Checks` → OVERALL must be PASS. 5. Copy results into memory/output files.
If no spreadsheet engine is reachable, stop and ask the human to open and recalculate the file.
