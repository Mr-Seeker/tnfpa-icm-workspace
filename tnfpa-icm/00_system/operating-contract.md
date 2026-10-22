# Operating contract (replaces openfpa `AGENTS.md`)

This workspace is an agent-native FP&A workbench, not a fixed application. The goal is to help an
AI build the finance system that fits one company while preserving a small, trustworthy accounting
kernel. The kernel is spreadsheets; the memory is markdown and CSV; the agent is the reasoning layer.

## Architecture

- `02_kernel/` is the stable kernel: validated input schemas, accounting mechanics, reconciliation,
  scoring, research evaluation and reusable analyses — as workbooks with live formulas and `Checks`.
- `companies/<slug>/memory/` is company memory: business context, sources, mappings, corrections,
  forecasts, experiments, decisions and accepted learnings (the openfpa `.fpa/` folder, made visible).
- Company-specific work lives in visible company namespaces: `models/` (workbook copies and
  company-specific workbooks), `connectors/` (no-code data-access contracts), `skills/`
  (generated skills) and `agents/` (generated agent briefs).
- Do not force a business into the K01 channel/opex/debt shape when its economics require a
  different model (cohorts, projects, contracts, fleets, stores, complex inventory). Build a
  company-specific workbook in `companies/<slug>/models/` using the K01 conventions and the
  `02_kernel/formula-reference.md` vocabulary, give it a `Checks` sheet, and register it.
- `01_tamil-nadu/` and `04_domains/` are factory layers: local law and the 29 enterprise domains.
  They feed drivers into the kernel; they never replace the kernel's accounting identities.

## Company onboarding

- Trigger onboarding when `memory/intake.csv` is not ready (K10 Readiness) and the user asks to build,
  configure, forecast, analyse or learn the business. Do not force onboarding for a narrow task.
- Control surface (each item = a file procedure in `command-equivalents.md`):
  status → init (copy `_templates/company/`) → doctor → inspect-data (K03 Inspect) for each supplied
  folder → source-profile (K03 Profile) → source-register (`sources/registry.csv`) → source-list →
  mapping-register (`mappings/registry.csv`) → mapping-list → reconcile-source (K03 Reconcile) →
  connector-list → connector-scaffold / connector-validate → intake-next (K10 Readiness) →
  intake-record (K10 RecordFact → `intake.csv`) → entrypoint-list / entrypoint-register
  (`models/workflows.csv`) → correction-record / correction-list → scorecard-render (K04) →
  experiment-list → context-pack (K11) → onboarding-render (K10 Profile + Proposal) → model-export (K01).
- Treat workbook and file outputs as evidence; they are not the reasoning engine.
- Inspect supplied local files before asking questions. Do not access external systems, portals
  (GST, MCA, bank, income-tax), MCP servers or connectors without user approval.
- Register every source used by a model with its entity, currency (INR unless stated), periods,
  extraction method and location. A file existing in the workspace is not lineage.
- Persist exact mappings, including deliberate ignores with rationale. Never infer an unmapped account
  into a model silently.
- Reconcile compatible account-amount sources with K03. For richer tables (aged AR/AP, item-level
  inventory, GSTR-2B), build an equivalent company workbook with its own `Checks` and register it.
- Build a connector only when recurring access is useful and the architecture is approved. One-time
  local files need no connector.
- Connector fixtures must be explicitly redacted. Never place a production export in `connectors/`
  without confirming it is safe to keep there.
- Connector validation is fixture-mode only (K03 with tolerance 0 against golden totals). It must not
  access a live system. Live access stays with the host tool (MCP server, ERP export, human export).
- Record source-derived and user-confirmed facts with citations and confidence (K10 RecordFact).
- Ask only the unresolved questions K10 returns, in rounds of at most three related questions.
  Record direct user answers immediately as confirmed. Ask for confirmation only on conflict or low confidence.
- For a Tamil Nadu company also clear the `tn_statutory` questions before W03.
- When intake is ready, render `memory/business-profile.md` and
  `memory/decisions/initial-model-architecture.md` (K10). **Stop.** Do not scaffold connectors,
  models, skills or agents until the user approves the proposal (tick the box and record who/when).
- After a company workflow has a tested procedure, register it in `memory/models/workflows.csv`.
  Registration advertises the procedure; it does not run it.

## Adaptation loop

1. Read status and doctor, then `memory/MEMORY.md`, intake, business profile, corrections, prior
   experiments and source notes before changing a model.
2. Rebuild `memory/index.csv` and build a bounded context pack for the task (K11).
3. Reconcile source data and report unmapped or unexplained amounts.
4. State a falsifiable financial hypothesis before editing any assumption or workbook.
5. Make the smallest company-specific change that can test it (copy the champion workbook first).
6. Run every relevant `Checks` sheet and a holdout (K04) or labelled scenario comparison.
7. Save a research epoch (`memory/research/epochs/`) with evidence, changed files, before/after
   metrics, check results and the memory sources used (K05 evaluates it).
8. Autonomously discard weak or failed challengers and preserve why they failed.
9. Present only promotion-eligible challengers for human ratification. Never replace the champion
   without explicit approval (K05 Promotion = PROMOTE plus the human's name and date).

## Excel output

For the standard monthly model, the champion K01 copy **is** the live-formula workbook (named driver
cells, real formulas, Checks). For any other cadence or layout (quarterly, weekly, segment tabs, a lender
view, a Tamil Nadu MIS in ₹ lakh) build a company-specific workbook from the K01 conventions, register
it as a `report` workflow, and verify it reproduces K01 (same lines, same months, tolerance 1e-6 or the
stated rounding). No workbook ships with a FAIL anywhere in `Checks`.

## Kernel guardrails

See `guardrails.md`. In short: never hide differences; never treat missing scoring evidence as
perfect; never overwrite source data, correction or experiment history; a change that improves a
headline metric but breaks an accounting invariant is a failed experiment; complexity is a cost;
promote company behaviour into `02_kernel/` only after it demonstrably generalises.

## Required evidence for an accepted model change

The hypothesis and CFO question; source evidence and periods used; files and assumptions changed;
before/after metrics; reconciliation and accounting checks; holdout or scenario results; who accepted
it, when and why.
