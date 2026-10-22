# Status and doctor (replaces `openfpa status` and `openfpa doctor`)

## Status — derived by scanning, never stored

For `companies/<slug>/` report (see `command-equivalents.md` #1 for field names):

| Field | Rule |
|---|---|
| initialized | `memory/` exists with `intake.csv` |
| intake_ready | K10 Readiness › J1 after pasting `intake.csv` (all 11 core keys known) |
| next question topic | K10 Readiness › B2 |
| onboarding stage | none → intake → proposal written → **approved** (decision box ticked with name/date) → scaffolded (a K01 copy registered as champion) → operating (≥ 1 snapshot) → learning (≥ 1 scored snapshot) |
| champion / challengers | `memory/models/model-versions.csv` role column |
| sources / mappings / connectors / workflows | row counts of the registries; folder count of `connectors/` |
| open corrections | `memory/corrections/*.md` with `status: open` |
| last close | latest `memory/forecasts/*.snapshot.md` with a score |

## Doctor — the contract check (healthy = zero errors)

Run every line. Record failures in your reply; fix before relying on workspace state.

| # | Check | Error when |
|---|---|---|
| 1 | workspace | `companies/<slug>/memory/` missing |
| 2 | directories | any of `sources mappings corrections forecasts experiments decisions models research` missing under `memory/` |
| 3 | intake | `intake.csv` header differs from `schemas/intake.md`, a status/confidence/source_type is invalid, a key repeats, an answer is empty |
| 4 | research objective | `research/objective.md` missing; a metric weight ≤ 0; duplicate metric or hard-check names; min_improvement or complexity_penalty < 0 |
| 5 | model registry | `model-versions.csv` / `promotions.csv` header wrong; more than one champion; duplicate model_id; a promotion without approved_by |
| 6 | workflow registry | `workflows.csv` header wrong; duplicate name; kind not in forecast/close/cash/research/report/connector/custom; a path is absolute or contains `..`; description empty |
| 7 | source registry | header wrong; duplicate source_id; id not `^[a-z][a-z0-9-]*$`; currency not 3 letters; empty location/entity/extraction_method |
| 8 | mapping registry | header wrong; duplicate (source_id, source_value); mapped row without target; ignored row without rationale |
| 9 | connector contracts | a `connectors/<dir>/connector.md` whose `name` ≠ folder; missing fixture; empty expected_totals; `live_ready: true` without a live recipe |
| 10 | corrections | a file whose frontmatter lacks type/target/status/date, or a type/status outside the allowed values |
| 11 | snapshots | a `forecasts/*.snapshot.md` whose frontmatter lacks label/created/predicted, or a score without fitness |
| 12 | workbooks | any registered workbook whose `Checks` OVERALL ≠ PASS (warning if never recalculated since last edit) |

Warnings never block; errors do. A healthy report is evidence, not reasoning.
