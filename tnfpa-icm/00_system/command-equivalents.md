# openfpa CLI → no-code procedures

openfpa's `openfpa <command>` (and `python3 -m pyfpa.cli <command>`) emitted a JSON envelope with exit
code 0 (success), 1 (operation or check failed) or 2 (invalid arguments). Here every command is a
deterministic **file procedure**. The equivalent of the JSON envelope is a short result block you write
in your reply (and, where noted, into a memory file):

```
result: success | failed | invalid
command: <name>   company: companies/<slug>
evidence: <workbook + sheet, or file paths read>
data: <the fields listed below>
```

`invalid` = a required input is missing or malformed (fix before retrying). `failed` = the procedure ran
but a check failed (report it; do not proceed as if it passed). `C` = `companies/<slug>`.

| # | openfpa command (arguments) | No-code procedure | Returns (data) |
|---|---|---|---|
| 1 | `status <root>` | If `C/memory/` is missing → `initialized: false`, next = init. Else read `memory/intake.csv` (fact count by status), K10 Readiness (`intake_ready`, next topic), existence of `business-profile.md` and `decisions/initial-model-architecture.md`, `models/model-versions.csv` (champion, challenger count), `models/promotions.csv` (count), `models/workflows.csv` (names), `sources/registry.csv`, `mappings/registry.csv` (counts), `connectors/*/connector.md` (names). | initialized, business_name, intake_ready, fact_count, facts_by_status, next_question_count, next_question_topic, profile/proposal exist, champion, challenger_count, promotion_count, workflows, source_count, mapping_count, connectors |
| 2 | `init <root> --business-name` | Copy `_templates/company/` to `companies/<slug>/` (slug rules in `naming-and-ids.md`). Never overwrite an existing company folder — if it exists, only add missing files. Put the name in `memory/MEMORY.md`, `memory/intake-notes.md` (business_name) and `CLAUDE.md`. | workspace path, created files |
| 3 | `doctor <root>` | Run the checklist in `status-and-doctor.md` (directories exist; every registry parses against its schema; intake valid; objective valid; snapshots parse). Healthy = zero errors. | healthy, checks[name,result,details], error_count, warning_count |
| 4 | `inspect-data <data-root> --max-files 500` | List files under the folder (skip hidden files/folders and `.git`, `node_modules`, `venv`, `__pycache__`, `build`, `dist`, `memory`). Paste relative path + bytes into a copy of **K03 › Inspect**. Read **Inspect_Summary**. Truncate at max-files and say so. | files[path, extension, bytes, category], file_count, category_counts, missing_priority_categories, truncated |
| 5 | `source-profile <root> --file` | Open the table (CSV/TSV/XLS/XLSX/ODS) and paste header + rows into **K03 › Profile**. Write the result to `memory/sources/evidence/<source_id>-profile-<date>.md`. Never modify the source file. | path, rows, columns, empty_by_column, duplicate_rows |
| 6 | `source-register <root> --source-id --kind --location --entity --currency --period… --extraction-method [--refreshed-at] [--notes] [--overwrite]` | Append one row to `memory/sources/registry.csv` per `schemas/source-record.md`. If the id exists and overwrite was not explicitly intended → `failed: source already registered`. Keep rows sorted by source_id. | the record |
| 7 | `source-list <root> [--kind]` | Read `memory/sources/registry.csv` (filter by kind). | sources[] |
| 8 | `mapping-register <root> --source-id --source-value [--target] [--status mapped/ignored] [--rationale] [--overwrite]` | Append one row to `memory/mappings/registry.csv` per `schemas/mapping-rule.md` (mapped needs target; ignored needs rationale; key = source_id + source_value unique). The source_id must already be registered. | the rule |
| 9 | `mapping-list <root> [--source-id] [--status]` | Read and filter `memory/mappings/registry.csv`. | mappings[] |
| 10 | `reconcile-source <root> --source-id [--file] [--account-column Account] [--amount-column Amount] [--expected-json] [--tolerance 0.01] [--allow-unmapped]` | Copy **K03**; set Setup (source_id, tolerance, allow-unmapped); paste the source's mapping rows into **Mapping**, the account/amount columns into **Reconcile** (file defaults to the registered location), expected totals into **Results**. Save the copy as `memory/sources/evidence/<source_id>-reconcile-<date>.xlsx` and summarise in a `.md` beside it. | source_id, row_count, source_total, mapped_total, mapped_totals, duplicates, unmapped, ignored, variances, passed |
| 11 | `connector-list <root> [--source-id]` | List `C/connectors/*/connector.md` (filter by source_id in frontmatter). | connectors[manifest] |
| 12 | `connector-scaffold <root> --name --source-id --description --auth-method none/host_environment/mcp --fixture [--account-column] [--amount-column] [--overwrite]` | Preconditions: source registered, mappings complete, architecture approved, fixture is an explicitly redacted CSV. Run K03 on the fixture with no expected totals: it must PASS with ≥1 mapped total. Copy `_templates/connector/` to `C/connectors/<name>/`, copy the fixture to `fixtures/source.csv`, write the mapped totals into `connector.md` frontmatter `expected_totals`, fill the export recipe. | manifest, reconciliation |
| 13 | `connector-validate <root> --name` | Copy **K03**; Setup tolerance = 0; paste `fixtures/source.csv` (fixture mode only — never live); expected = `expected_totals` from `connector.md`. Must PASS. Record the result in `connector.md` › Validation log. | manifest, reconciliation, passed |
| 14 | `intake-next <root> [--limit 3]` | Paste `memory/intake.csv` into **K10 › Facts**; read **Readiness** (next topic and ≤ limit questions). | questions[key, topic, prompt, reason, current_answer] |
| 15 | `intake-record <root> --key --answer --source-type user/local_file/external/inference [--source…] [--confidence] [--topic] [--question]` | Use **K10 › RecordFact** to compute the resulting row (progressive authority), then replace that key's row in `memory/intake.csv`. Empty answer → invalid. | fact, intake_ready |
| 16 | `entrypoint-list <root> [--kind]` | Read `memory/models/workflows.csv` (filter kind). | workflows[] |
| 17 | `entrypoint-register <root> --name --kind --description --command-json --working-directory --input… --output… [--overwrite]` | Append to `memory/models/workflows.csv` per `schemas/workflow-registry.md`. "Command" = the runbook path + workbook path (no executables). Registration never runs anything. | workflow |
| 18 | `correction-record <root> --slug --type --target --date [--status open] [--notes] [--override-path --override-value]` | Copy `_templates/correction.md` to `memory/corrections/<slug>.md` (slug = `<YYYY-MM-DD>-<short-name>`), fill frontmatter + body. | correction |
| 19 | `correction-list <root> [--status]` | Read frontmatter of `memory/corrections/*.md`. | corrections[] |
| 20 | `scorecard-render <root>` | Transcribe every `memory/forecasts/*.snapshot.md` (chronological) into **K04 › Snapshots**; copy **K04 › Scorecard** column A into `memory/scorecard.md` verbatim (overwrite allowed: it is a derived file). | snapshot_count, scored_count, scorecard_path |
| 21 | `experiment-list <root> [--status]` | Read frontmatter of `memory/experiments/*.experiment.md`. | experiments[] |
| 22 | `context-pack <root> --task [--category…] [--limit 8]` | Rebuild `memory/index.csv` (rules in K11 README), paste it into **K11 › Index**, task tokens into **Task**; copy **Pack** column A into `memory/context-pack.md` (temporary). Then open each listed source file to read its excerpt. | context_pack_path, hits |
| 23 | `onboarding-render <root> --proposal-summary [--connector…] [--model-component…] [--generated-skill…] [--risk…] [--validation-check…]` | Only when K10 `intake_ready` = TRUE (else `failed: intake not ready`). Fill **K10 › Proposal** inputs; copy **Profile** column A to `memory/business-profile.md` and **Proposal** column D to `memory/decisions/initial-model-architecture.md`. Then stop for approval. | profile path, proposal path |
| 24 | `model-export <root> --config --out` | Copy **K01** to the requested path, fill Assumptions from the company config, confirm Checks = PASS. (There is no separate export step: the K01 copy is the live-formula model.) | out path, checks |

Fallback rule from openfpa (`python3 -m pyfpa.cli` when the console script is missing) has no
equivalent and no need: every procedure above needs only file access and a spreadsheet engine.
