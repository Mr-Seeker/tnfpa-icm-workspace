# Fox Factory Holding Corp. FP&A Memory

- `intake.csv` + `intake-notes.md`: onboarding facts, evidence, confidence, and open questions
- `business-profile.md`: durable business context rendered from intake (K10)
- `sources/`: source inventory and data provenance (`registry.csv`, `evidence/`)
- `mappings/`: account and operational-data mappings (`registry.csv`)
- `corrections/`: typed human corrections (W08), applied through the K01 Corrections sheet
- `forecasts/`: immutable forecast snapshots and their scores (W09)
- `scorecard.md`: rendered forecast track record across all scored periods (K04; never hand-edit)
- `learnings.md`: accepted model changes with evidence and backtest delta
- `experiments/`: model hypotheses, evidence, checks, and ratification decisions
- `decisions/`: material CFO decisions and approvals (Gate 1, Gate 2, policies)
- `models/`: champion/challenger history (`model-versions.csv`, `promotions.csv`) and registered workflows (`workflows.csv`)
- `research/`: objective and immutable research epochs (W10)
- `index.csv`: rebuildable memory index (K11) — derived, never the source of truth
- `../connectors/`: fixture-validated company data-access recipes
