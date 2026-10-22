# Experiment (replaces `.fpa/experiments/<slug>.experiment.yaml`)

**File:** `memory/experiments/<slug>.experiment.md`; slug `^[a-z0-9][a-z0-9._-]*$`. Frontmatter fields:
`schema_version: 1, slug, created, status (draft|proposed|accepted|rejected|reverted), hypothesis,
snapshot (label/path of the scored snapshot), cfo_question, rationale, evidence[], training_periods[],
holdout_periods[], files_changed[], metrics_before{}, metrics_after{}, checks[{name, result pass|fail|not_run,
details}], decision{outcome accepted|rejected|reverted, decided_by, decided_at, notes}`.

Rules (enforced by you before saving): terminal statuses (accepted/rejected/reverted) need a decision
whose outcome equals the status; draft/proposed must not have a decision; **accepted** needs evidence,
files_changed, at least one check, and every check = pass. Never overwrite an experiment implicitly;
change status with an explicit edit and keep the history in the body.
