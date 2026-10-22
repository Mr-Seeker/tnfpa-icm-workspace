# Model registry (replaces `.fpa/models/registry.yaml`)

`memory/models/model-versions.csv` — header `model_id,role,created,artifact,source_epoch,description,retired_at`
- role: champion (at most one), challenger, retired. model_id unique across all roles.
- artifact: relative path to the workbook (e.g. `models/K01_champion.xlsx`) or a sheet reference.
- register_challenger: append a challenger row; a duplicate id is an error.

`memory/models/promotions.csv` — header `from_model,to_model,epoch_id,approved_by,approved_at,notes`
- Written only when K05 › Promotion says PROMOTE: the old champion's role → retired (retired_at = date),
  the challenger's role → champion, the epoch status → promoted, and one promotions row appended.
- approved_by must be a named human. The challenger's source_epoch must equal epoch_id.
