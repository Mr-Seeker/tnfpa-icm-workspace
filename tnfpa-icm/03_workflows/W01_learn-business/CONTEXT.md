# W01 · Learn the business (Phase 0 — onboarding)

Before any model, learn the business. Produces a **durable business profile** every other workflow reads
first, an **architecture proposal** for human approval, and (after approval) proposals for bespoke
skills/agents. **Core principle:** a forecast is only as good as the business understanding behind it —
encode it once, explicitly.

**Use when:** a new company is onboarded; "build us a model / understand our business"; the profile is
missing or stale. **Do not** force this for a narrow task that can be done without the whole company.

## Inputs
| Working (this company) | Reference (every run) |
|---|---|
| the folders/files the user points to (e.g. `./company-data`) | `02_kernel/K03_source-reconcile.xlsx` (Inspect, Profile) |
| `companies/<slug>/memory/intake.csv`, `intake-notes.md` | `02_kernel/K10_intake-onboarding.xlsx` |
| existing models or MIS packs the company already uses | `00_system/schemas/intake.md`, `source-record.md`, `mapping-rule.md` |
| | `01_tamil-nadu/sector-clusters.md`, `fiscal-and-close-calendar.md` |
| | `portfolio/library/` (only after approval, step 7) |

## Process
1. **Check and initialise.** Status (`00_system/status-and-doctor.md`). If uninitialised, copy
   `_templates/company/` to `companies/<slug>/` and set the business name. Run the doctor checklist.
2. **Inspect local evidence first.** For every supplied folder, list files into a K03 copy › Inspect;
   note missing priority categories (P&L, balance sheet, AR aging, AP aging, inventory). Profile the
   tables you will rely on (K03 › Profile; save evidence under `memory/sources/evidence/`), register them
   (`sources/registry.csv`), read financials, MIS packs, board notes and existing models. Record each fact
   you can establish with K10 › RecordFact → `intake.csv` (`source_type: local_file`, file paths as
   sources, honest confidence). Never open an external system without approval.
3. **Ask only what remains unknown.** Paste `intake.csv` into K10 › Facts; ask the Readiness "next round"
   (≤ 3 related questions, one topic). After each reply record it with `source_type: user` (confirmed at
   1.0). Ask the user to resolve only conflicts and low-confidence inferences.
4. **Repeat short rounds** until K10 `intake_ready` = TRUE. For a Tamil Nadu company continue through the
   `tn_statutory` questions (GST profile, tax regime/TDS, payroll statutory, MSME & incentives, local
   seasonal calendar). Never ask what local evidence or earlier conversation already answered.
5. **Propose the company architecture.** Fill K10 › Proposal: objective summary, connectors (which sources
   need recurring access and how — usually export recipes), company model components (K01 slots used, or a
   bespoke workbook; which `04_domains` modules feed which drivers), generated skills, risks/judgement
   areas, validation checks. Copy K10 › Profile → `memory/business-profile.md` and K10 › Proposal →
   `memory/decisions/initial-model-architecture.md`.
6. **STOP for approval (Gate 1).** Summarise known facts, remaining unknowns and the proposal. Do not
   scaffold or generate anything until the user approves. Record approval in the decision file
   (tick "Approved to scaffold", add `Approved by: <name>, <date>`).
7. **After approval, seed from the portfolio library** if `portfolio/library/priors/<type>.csv` exists for
   this business type: priors are seeds; the client's own loop refines them (W11).
8. **Identify gaps the standard workflows don't cover** and propose bespoke skills/agents (W12): product
   company with SKUs → `sku-profitability`; multi-division → `segment-rollup`; SaaS → ARR/cohort;
   logistics → driver-cost scorecard; textile exporter → order-book & export-incentive cash; dealer
   network → dealer-credit & scheme-accrual.
9. **Generate approved artefacts** via W12 into `skills/` and `agents/`; company models into `models/`;
   connectors into `connectors/`. Each must cite the profile facts that justify it and include a `Checks`
   sheet or a reconciliation.
10. **Apply existing corrections** before forecasting: applied parametric corrections go into the K01
    copy's Corrections sheet; route `structural` corrections through W12 as pre-ratified proposals.

## Outputs (in `companies/<slug>/`)
`memory/intake.csv` (facts with citations), `memory/sources/registry.csv` + `evidence/`,
`memory/business-profile.md`, `memory/decisions/initial-model-architecture.md` (status Proposed → Approved),
`memory/MEMORY.md` updated, `memory/index.csv` rebuilt.

## Human check
Gate 1 approval of the architecture proposal (and every generated skill/agent before it is written).

## Guardrails
Self-extending, not self-executing. No profile fact → no generated skill. Material generated changes are
recorded as experiments (`memory/experiments/`); rejected and reverted ones are kept.

## Next
After approval → **W02 scaffold-model**. Consult **W00** throughout.
