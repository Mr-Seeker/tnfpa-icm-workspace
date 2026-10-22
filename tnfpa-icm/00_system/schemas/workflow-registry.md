# Workflow registry (replaces `.fpa/models/entrypoints.yaml`)

**File:** `memory/models/workflows.csv` sorted by name. Header:
`name,kind,description,procedure,workbook,working_directory,inputs,outputs,registered_at`

| column | rule |
|---|---|
| name | `^[a-z][a-z0-9-]*$`, unique (overwrite only on explicit intent) |
| kind | forecast, close, cash, research, report, connector, custom |
| description | non-empty |
| procedure | relative path to the runbook markdown (the steps a person or agent follows) |
| workbook | relative path to the workbook it uses (blank if none) |
| working_directory | `.` or a relative path without `..` |
| inputs / outputs | `; `-separated relative paths without `..`, de-duplicated |

Registration advertises a tested procedure for discovery; it never executes anything. Before running a
company workflow, list the registry; after validating a new one, register it.
