# pyfpa public API → no-code equivalents

Every name exported by `pyfpa/__init__.py` (and the internal helpers the skills call) has a home.
"K01 › Model" means workbook `02_kernel/K01_monthly-pnl-cash-model.xlsx`, sheet `Model`.

## Model configuration and engine
| pyfpa | Equivalent |
|---|---|
| `EntityConfig`, `Channel`, `OpexLine`, `DebtInstrument`, `WorkingCapitalConfig`, `OpeningBalances` | K01 › Assumptions blocks (scalars, 8 channel slots, 15 opex slots, 5 debt slots); validation rules = K01 › Checks 1–12 (`schemas/model-config.md`) |
| `load_config` (YAML + validation) | fill K01 › Assumptions; Checks must PASS |
| `revenue_from_config` | K01 › Model rows `revenue_ch1..8`, `revenue` |
| `cogs_from_config` | K01 › Model `cogs_ch1..8`, `cogs` |
| `opex_from_config` | K01 › Model `opex_1..15`, `opex` |
| `working_capital_from_config` | K01 › Model `ar_balance`, `ap_balance`, `inv_balance`, `wc_cash_impact` |
| `debt_from_config` | K01 › Model `debt_balance_k`, `interest_k`, `principal_k`, totals, `ending_debt` |
| `cashflow_from_config` | K01 › Model (all lines) and K01 › Export_Rows (month-per-row frame) |
| `periods.month_index` | K01 › Model rows `month_no`, `period_start`, `active`; plus Indian FY and quarter rows |
| `apply_corrections`, `apply_override`, `Override` | K01 › Corrections + Effective (path precedence rules in K01 README) |

## 13-week cash
| `Cash13Config`, `WeeklyFlow`, `load_cash13_config` | K02 › Setup + Flows (Checks validate) |
| `expand_flow` | K02 › Grid |
| `cash13_forecast` | K02 › Weekly |
| `runway_summary` | K02 › Runway (`min_cash`, `min_week`, `first_negative_week`) + credit-line sizing |

## IO and reporting
| `read_pl_csv`, `_parse_amount` | K03 › Reconcile parsing columns (₹/Rs./INR/$, commas, (parens), Dr/Cr) |
| `pyfpa.io.adapters.from_quickbooks / from_netsuite / from_shopify` (fixture examples) | `examples/ridgeline-parity/data/fixtures/` + connector template; Tally/Zoho/SAP export recipes in `01_tamil-nadu/data-sources-india.md` |
| `to_briefing_md` | K01 › Briefing (headline, optional runway, monthly table, narrative slots) |
| `forecast_to_excel` (static values) | K01 › Export_Rows (copy → paste values into any workbook) |
| `model_to_excel` (live formulas) | the K01 copy itself |
| `verify_workbook` | K01 › Checks (identities every month + golden parity rows); company-specific workbooks add their own parity rows |
| `excel.toolkit` (`add_named_cell`, `add_named_row`, `fill_formula_row`, formats) | conventions in `02_kernel/formula-reference.md` (named cells, one formula per line per month, number formats) |

## Analysis
| `reconcile` (model vs actual, tolerance) | K03 › Results variances; W04 variance table in D01 › Versions |
| `Segment`, `segment_pnl`, `roll_up_segments`, `segments_to_channels` | K07 › Segments, ToChannels, SegmentForecast |
| `Sku`, `sku_profitability`, `pareto_breakpoint`, `load_skus` | K06 › SKUs, Ranked |
| `Carveout`, `divest`, `net_debt_to_ebitda` | K08 › Setup, S0–S10, Grid |

## Backtest and learning
| `extract_lines`, `aggregate_periods`, `DEFAULT_SCORE_LINES`, `DEFAULT_WEIGHTS` | K01 › Summary (predicted lines) and K04 › Score/Holdout |
| `score_forecast`, `ScoreResult` | K04 › Score |
| `holdout_backtest` | K04 › Holdout + a fit-only K01 copy |
| `Snapshot`, `snapshot_forecast`, `save_snapshot`, `load_snapshot` | `memory/forecasts/<label>.snapshot.md` (+ `<label>.assumptions.xlsx` copy) from K01 › Summary |
| `render_scorecard` | K04 › Scorecard → `memory/scorecard.md` |
| `persistent_miss`, `magnitude_cap` | K04 › Learning_Guards |

## Memory
| `initialize_workspace`, `workspace_path` | copy `_templates/company/` → `companies/<slug>/` |
| `Correction`, `save_correction`, `load_corrections` | `memory/corrections/<slug>.md` (`schemas/correction.md`) |
| `Experiment`, `ExperimentCheck`, `ExperimentDecision`, `save/load_experiment(s)` | `memory/experiments/<slug>.experiment.md` (`schemas/experiment.md`) |
| `Intake`, `IntakeFact`, `IntakeQuestion`, `save/load_intake` | `memory/intake.csv` + `intake-notes.md` (`schemas/intake.md`) |
| `record_intake_fact`, `intake_ready`, `next_intake_questions` | K10 › RecordFact, Readiness |
| `ArchitectureProposal`, `render_business_profile`, `render_architecture_proposal`, `write_onboarding_outputs` | K10 › Profile, Proposal |
| `MemoryEntry/Hit/Index`, `build_memory_index`, `save/load_memory_index`, `search_memory`, `build_context_pack` | `memory/index.csv` + K11 |
| `CompanyEntrypoint`, `EntrypointKind`, `EntrypointRegistry`, `register_entrypoint`, `load/save_entrypoint_registry` | `memory/models/workflows.csv` (`schemas/workflow-registry.md`) |
| `SourceKind`, `SourceRecord`, `SourceRegistry`, `register_source`, `load/save_source_registry` | `memory/sources/registry.csv` |
| `MappingRule`, `MappingStatus`, `MappingRegistry`, `register_mapping`, `load/save_mapping_registry` | `memory/mappings/registry.csv` |
| `profile_table`, `reconcile_account_table` | K03 › Profile, Reconcile/Results |
| `ConnectorAuth`, `ConnectorManifest`, `connector_bundle_path`, `connector_generated_root`, `load/save_connector_manifest(s)`, `scaffold_connector_bundle`, `validate_connector_bundle` | `companies/<slug>/connectors/<name>/connector.md` + `fixtures/` (`schemas/connector.md`) + K03 fixture validation |
| `validate_workspace` (doctor), `inspect_data_files` | `status-and-doctor.md`; K03 › Inspect |

## Research
| `MetricObjective`, `ResearchObjective`, `load/save_research_objective` | `memory/research/objective.md` + K05 › Objective |
| `ResearchEpoch`, `EpochEvaluation`, `evaluate_challenger`, `save/load_epoch(s)` | `memory/research/epochs/<id>.md` + K05 › Epochs |
| `ModelRegistry`, `ModelVersion`, `PromotionRecord`, `register_challenger`, `promote_challenger`, `load/save_model_registry` | `memory/models/model-versions.csv`, `promotions.csv` + K05 › Promotion |

## Portfolio
| `Portfolio`, `ClientRef`, `load_portfolio`, `clients_of_type` | `portfolio/portfolio.csv` + K09 › Clients |
| `recover_actuals`, `best_snapshot` | K04 › Snapshots (recovered actual columns, best_snapshot cell) |
| `MINEABLE_DRIVERS`, `PriorCandidate`, `mine_priors` | K09 › Mine |
| `ValidationResult`, `validate_prior` | K09 › Validate |
| `SkillCandidate`, `find_recurring_skills` | K09 › Skills |
| `load_library`, `promote_prior`, `promote_skill`, `seed_from_library` | `portfolio/library/` (priors CSV, skills folders, `library-log.md`) + W11 procedure |
