# Intake (replaces `.fpa/intake.md` YAML frontmatter)

**File:** `memory/intake.csv` — one row per fact. `memory/intake-notes.md` holds `business_name`,
`schema_version: 1` and free-text notes.

| column | type | rule |
|---|---|---|
| key | text | unique; core keys: business_model, revenue_model, customer_channels, collections, supplier_payments, seasonality, entities, financing, data_sources, planning_cadence, cfo_priorities; TN keys: gst_profile, tds_and_tax_regime, payroll_statutory, msme_and_incentives, seasonal_calendar_tn; any other key allowed (topic defaults to `other`) |
| topic | text | business, cash_cycle, finance_structure, planning, tn_statutory, other |
| question | text | the bank prompt for known keys, else the key |
| answer | text | non-empty, trimmed |
| status | enum | confirmed, inferred, conflict |
| confidence | number | 0–1 (user answers = 1.0; default non-user evidence = 0.8) |
| source_type | enum | user, local_file, external, inference |
| sources | text | `; `-separated file paths or citations, de-duplicated, order kept |
| alternatives | text | `; `-separated conflicting answers (conflict only) |

**Known** = status ≠ conflict and (status = confirmed or confidence ≥ 0.70).
**Ready** = all 11 core keys known. **Recording** = K10 › RecordFact (progressive authority).
