# TN-FPA ICM Workspace

**A no-code, AI-agent-native FP&A workbench, with an India and Tamil Nadu localisation layer.**

This folder is a complete replacement for [openfpa](https://github.com/JeffBrines/openfpa) by Jeff Brines,
restructured as an Interpretable Context Methodology (ICM) workspace in the style of Jake Van Clief
(Van Clief & McDermott, arXiv:2603.16021). Everything openfpa did with Python, a CLI and tests is
done here with:

- **folders and markdown** — the operating contract, the workflows, the memory;
- **CSV registries** — sources, mappings, intake facts, model versions, workflows;
- **spreadsheet workbooks with live formulas** — the finance kernel and the 29 domain modules;
- **BI data model + Office templates** — dashboards, board decks and memos.

There are no scripts, macros, add-ins, packages, containers or command lines. Any mainstream
spreadsheet engine (Microsoft Excel, LibreOffice Calc, Google Sheets, OnlyOffice, Zoho Sheet, WPS) can
recalculate every workbook; any BI tool (Power BI, Tableau, Looker Studio, Zoho Analytics, Metabase,
Superset) can read the CSV data model; any office suite can open the deck and memo templates.

## Who uses it

The primary user is an **AI agent** (Claude, Codex, or any agent that can read and edit files).
Humans point the agent at their data, answer short question rounds, and approve the two gates:
the model architecture, and every champion-model promotion.

## Start

1. Open this folder with your agent and say, for example:
   *"Help me onboard our company. Our Tally exports are in ./company-data. Inspect them first,
   then ask me only what you cannot determine."*
2. The agent reads `CLAUDE.md`, copies `_templates/company/` to `companies/<your-slug>/`, inspects
   your files, records facts, asks ≤3 questions at a time, and stops for your architecture approval.
3. After approval it scaffolds the model workbooks, wires in actuals, and runs closes, 13-week cash,
   board briefings and the learning loop.

## Proof that it does what openfpa did

`examples/` contains three verified worked examples:

| Example | What it proves |
|---|---|
| `ridgeline-parity/` | The kernel workbooks reproduce openfpa's published Ridgeline outputs exactly (revenue 6,000,000; EBITDA 824,000; net income 572,651; ending cash 720,418; 13-week trough −146,000 in week 7, first negative week 3). |
| `foxfactory-public-proof/` | The four-phase SEC-data example (reproduction, FY2025 holdout research, FY2026–27 forecast, Marucci divestiture) reproduces every published figure. |
| `kaveri-chairs-coimbatore/` | A full Tamil Nadu company workspace: Tally Dr/Cr export, GST/TDS/PF/ESI cash calendar, Indian fiscal year, ₹ lakh reporting, Deepavali/Pongal seasonality. |

`00_system/coverage/openfpa-coverage-map.csv` maps every one of openfpa's 206 files to its replacement.

## Licence and credit

openfpa is MIT-licensed (Copyright (c) 2026 Guiderail). ICM is MIT-licensed (Van Clief & McDermott).
Both attributions, and openfpa's full licence text, are in [`NOTICE`](../NOTICE) and
[`THIRD_PARTY_NOTICES.md`](../THIRD_PARTY_NOTICES.md) at the repository root. Statutory rates in `01_tamil-nadu/` change — always check
`01_tamil-nadu/verification-register.md` before relying on one.
