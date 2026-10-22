# Research epoch (replaces `.fpa/research/<id>.epoch.yaml`)

**File:** `memory/research/epochs/<epoch_id>.md`. Frontmatter: `schema_version: 1, epoch_id, created,
status (generated|evaluated|discarded|proposed|promoted), hypothesis, champion_id, challenger_id,
memory_sources[], files_changed[], training_periods[], holdout_periods[], checks[{name,result,details}],
evaluation{champion_metrics{}, challenger_metrics{}, per_metric_improvement{}, weighted_improvement,
complexity_cost, objective_gain, hard_checks_passed, regression_guard_passed, promotion_eligible}, notes`.

Rules: non-generated statuses need an evaluation (copied from K05 › Epochs); only promotion-eligible
epochs may be proposed or promoted; discarded epochs are kept forever (with the reason) so the same
hypothesis is not retried without new evidence. Saving over an existing epoch needs explicit overwrite.
