# Source record (replaces `.fpa/sources/registry.yaml`)

**File:** `memory/sources/registry.csv`, sorted by source_id. Header:
`source_id,kind,location,entity,currency,periods,extraction_method,refreshed_at,notes`

| column | rule |
|---|---|
| source_id | `^[a-z][a-z0-9-]*$`, unique |
| kind | local_file, shared_folder, accounting_system, operating_system, api, public_filing, manual |
| location | non-empty (relative path or system name, e.g. `data/raw/tally-pl-2026-09.csv`, `Tally Prime company 'Kaveri FY26-27'`) |
| entity | non-empty legal entity (with GSTIN state code if relevant, e.g. `Kaveri Chairs Pvt Ltd (33)`) |
| currency | 3 letters, upper case (INR, USD …) |
| periods | `; `-separated, de-duplicated, no blanks (e.g. `2026-04; 2026-05` or `FY2025-26`) |
| extraction_method | non-empty (how it was produced: "Tally Prime > Display > Trial Balance > Export CSV by accountant") |
| refreshed_at | optional ISO date |
| notes | optional |

Registering an existing id requires explicit overwrite intent. Evidence files (profiles, reconciliations)
live in `memory/sources/evidence/`.
