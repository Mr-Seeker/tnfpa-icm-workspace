# _templates — stamps (copy, never start from a blank page)

| Template | Copy to | When |
|---|---|---|
| `company/` | `companies/<slug>/` | init (W01 step 1) |
| `correction.md` | `companies/<slug>/memory/corrections/<YYYY-MM-DD>-<name>.md` | W08 |
| `snapshot.md` | `companies/<slug>/memory/forecasts/<label>.snapshot.md` | W04/W09 every forecast |
| `experiment.md` | `companies/<slug>/memory/experiments/<slug>.experiment.md` | W09 before any model change |
| `epoch.md` | `companies/<slug>/memory/research/epochs/<epoch_id>.md` | W10 each challenger |
| `decision.md` | `companies/<slug>/memory/decisions/<YYYY-MM-DD>-<slug>.md` | any approval/gate |
| `connector/` | `companies/<slug>/connectors/<name>/` | W03 recurring access |
| `generated-skill/` | `companies/<slug>/skills/<name>/` | W12 after approval |
| `generated-agent/` | `companies/<slug>/agents/<name>/` | W12 after approval |
| `domain-record/` | `companies/<slug>/domains/Dnn_<slug>/` (+ the domain workbook) | when a domain feeds the model |

The template **is** the schema (`00_system/schemas/`). If a copied record drifts from its template, re-stamp it.
