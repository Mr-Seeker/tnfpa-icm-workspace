# W03 · Configure actuals and data sources (Phase 2)

Connect the model to real data — from wherever it lives. Not married to one connector: everything
normalises to one shape (`Account, Amount`), and where no recipe exists you **write the recipe for this
source** (the Fox Factory example's SEC-EDGAR pull is the pattern: the agent met the data where it was).
**Core principle:** one normalised shape regardless of source, so the engine never cares where numbers
came from.

## Where the data can come from
- **Local spreadsheets / exports** (always works, no credentials): P&L, balance sheet, trial balance, AR/AP
  aging, inventory, bank statements. K03 parses any two-column Account/Amount table (₹, Rs., $, commas,
  lakh commas, (parens) = negative, Dr/Cr). Richer tables (aged buckets, item-level stock, GSTR-2B) have no
  rigid reader by design: derive **DSO** from AR aging, **DIO** from inventory, **DPO** from AP aging in a
  company workbook with its own Checks.
- **Accounting system via an approved MCP server or the system's own export** (Tally Prime, Zoho Books,
  SAP, NetSuite, Ramco, Marg, Busy) — the host tool owns authentication; this workspace never sees credentials.
- **Public filings** — MCA21 financial statements, BSE/NSE results and shareholding (listed companies),
  SEC/other regulators for foreign parents (see `examples/foxfactory-public-proof/`).
- **Anything else** — write the export recipe and normalise to Account/Amount (or to the drivers needed).

## Inputs
| Working | Reference |
|---|---|
| `memory/models/workflows.csv` (kind connector), `connectors/` | `02_kernel/K03_source-reconcile.xlsx` |
| the source files, `memory/sources/registry.csv`, `memory/mappings/registry.csv` | `01_tamil-nadu/data-sources-india.md`, `schedule-iii-mapping.csv` |
| approved architecture (which sources need recurring access) | `00_system/schemas/connector.md`, `_templates/connector/` |

## Process
1. **Discover existing access:** list workflows of kind `connector` and `connectors/*/connector.md`; reuse
   a validated one when it exists.
2. **Pull** actuals via the path that fits (user export, host MCP with approval, public download).
3. **Profile** the table (K03 › Profile): columns, empty values, duplicate rows → evidence file.
4. **Register** the source (stable id, entity with GSTIN state code if relevant, currency, periods,
   extraction method, location).
5. **Map** every account to a model target (seed from `schedule-iii-mapping.csv`); register deliberate
   ignores with a rationale (e.g. GST control ledgers, interest that the debt schedule models).
6. **Reconcile** (K03 › Reconcile/Results): duplicates and unmapped accounts fail; never drop or overwrite
   silently. For richer tables build a company reconciliation workbook giving equivalent evidence and
   register it as a workflow.
7. **Register recurring access** (only if recurring and approved): copy `_templates/connector/` to
   `connectors/<name>/`, put an explicitly **redacted** fixture in `fixtures/source.csv`, run K03 on it
   (must pass with ≥ 1 mapped total), write the golden mapped totals into `connector.md`, write the export
   recipe and failure behaviour. Validate (K03, tolerance 0, fixture mode) after every change and log it.
   Set `live_ready: true` only when the live recipe is documented and approved; then register the
   workflow with kind `connector`.
8. **Judgment** (W00): pre-close months, flash vs GL cash, one-time items, GST-inclusive figures.

## Outputs
Registered sources, mappings, evidence files, connector folders with validation logs, workflow rows.

## Credentials
Never store secrets. MCP servers and ERPs own their own authentication. Only redacted fixtures here.

## Human check
Approve any external access before it happens; confirm a fixture is redacted before it is stored.

## Next
Actuals wired → operate: **W04 monthly-close**, **W05 cash-runway**, **W07 board-briefing**.
