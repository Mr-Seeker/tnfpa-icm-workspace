---
schema_version: 1
slug: ""                # ^[a-z0-9][a-z0-9._-]*$
created: YYYY-MM-DD
status: draft           # draft | proposed | accepted | rejected | reverted
hypothesis: ""
snapshot: ""            # label/path of the scored snapshot that motivated it
cfo_question: ""
rationale: ""
evidence: []
training_periods: []
holdout_periods: []
files_changed: []
metrics_before: {}
metrics_after: {}
checks: []              # - {name: "accounting invariants", result: pass|fail|not_run, details: ""}
# decision:             # only for accepted | rejected | reverted (outcome must equal status)
#   outcome: accepted
#   decided_by: ""
#   decided_at: YYYY-MM-DD
#   notes: ""
---
Narrative: what changed, why, what the holdout showed. Accepted requires evidence, files_changed and checks that all pass.
