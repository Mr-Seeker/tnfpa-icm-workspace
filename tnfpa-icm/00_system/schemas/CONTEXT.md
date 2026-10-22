# schemas — the record contracts

One file per record type. Each states the file location, the exact columns or frontmatter fields,
allowed values and the validation rules openfpa enforced in code (now enforced by you, by K-workbook
`Checks`, and by the doctor checklist). When a schema and a file disagree, fix one of them in the
same change — never leave them drifted.

| Schema | Record lives at (inside `companies/<slug>/`) |
|---|---|
| `intake.md` | `memory/intake.csv`, `memory/intake-notes.md` |
| `source-record.md` | `memory/sources/registry.csv` |
| `mapping-rule.md` | `memory/mappings/registry.csv` |
| `correction.md` | `memory/corrections/<slug>.md` |
| `snapshot.md` | `memory/forecasts/<label>.snapshot.md` (+ `<label>.assumptions.xlsx`) |
| `experiment.md` | `memory/experiments/<slug>.experiment.md` |
| `research-objective.md` | `memory/research/objective.md` |
| `research-epoch.md` | `memory/research/epochs/<epoch_id>.md` |
| `model-registry.md` | `memory/models/model-versions.csv`, `memory/models/promotions.csv` |
| `workflow-registry.md` | `memory/models/workflows.csv` |
| `connector.md` | `connectors/<name>/connector.md` + `fixtures/source.csv` |
| `model-config.md` | K01 Assumptions (the EntityConfig contract) |
| `memory-index.md` | `memory/index.csv` |
| `portfolio.md` | `portfolio/portfolio.csv`, `portfolio/library/` |
| `decision.md` | `memory/decisions/<date>-<slug>.md` |
| `domain-record.md` | `domains/Dnn_<slug>/…` |
