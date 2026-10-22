# Portfolio manifest and library (replaces `~/.fpa/portfolio.yaml` and `~/.fpa/library/`)

`portfolio/portfolio.csv` — header `client_path,business_type,notes`; client_path is relative to the
workspace (e.g. `companies/kaveri-chairs-coimbatore`); business_type is the clustering tag
(e.g. `tn-furniture-d2c-dealer`, `tiruppur-knitwear-export`, `coimbatore-pumps-oem`).

`portfolio/library/priors/<business_type>.csv` — header
`driver,value,support,cross_client_holdout_delta,n_folds,promoted_at,approved_by`.
`portfolio/library/skills/<skill-name>/SKILL.md` — copied recurring skills.
`portfolio/library/library-log.md` — one line per promotion: `- prior <driver> = <value> for <type> (support N, delta ±0.0000)`
or `- skill <name> for <type> (support N)`.
