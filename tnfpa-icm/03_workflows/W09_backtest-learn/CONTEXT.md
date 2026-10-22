# W09 · Backtest and learn (Operate / Learn — at and after each close)

The model should get measurably better at this business over time. Score past forecasts against the
company's actuals, surface what keeps missing, and propose improvements a human ratifies. The objective
metric is the error against the company's own books (K04 fitness) — the FP&A analogue of a validation loss.
**Core principle:** self-experimenting, never self-promoting. Everything learned lives as plain files.

## Memory
- `memory/forecasts/<period>.snapshot.md` (+ `.assumptions.xlsx`) — each forecast's assumptions and
  predictions and, after close, its score.
- `memory/scorecard.md` — the running track record (rendered by K04, never hand-edited).
- `memory/experiments/<slug>.experiment.md` — each tested model change, evidence, files, checks,
  before/after metrics, decision.
- `memory/learnings.md` — every accepted change: what, the evidence, the backtest delta, the date.

## Inputs
| Working | Reference |
|---|---|
| snapshots, closed-period actuals (W03), corrections, champion | `02_kernel/K04_scoring-backtest.xlsx`, `K01…` |
| `memory/research/objective.md` | `_templates/experiment.md`, `_templates/snapshot.md`, `00_system/guardrails.md` |

## Process
1. **Snapshot every forecast** when produced: K01 › Summary snapshot block → `forecasts/<label>.snapshot.md`
   with the `created` date you were given; save the untouched workbook as `<label>.assumptions.xlsx`.
2. **Score at close:** load that period's snapshot, enter predicted vs aggregated actuals into K04 › Score,
   write the score (fitness, per-line errors, weights used) back into the snapshot, then re-render the
   scorecard (K04 › Snapshots → Scorecard → `memory/scorecard.md`). Missing/zero actuals → no score.
3. **Attribute** each material per-line miss to a driver (volume / price / cost ratio / working-capital
   timing). **Run the W00 one-time screen first** — never blame the model for a one-off.
   **Monitor applied corrections:** if a parametric correction's target line keeps missing, flag it as
   possibly stale (applied → superseded) for the human — never auto-revert.
4. **Create an experiment** before changing the model: hypothesis, CFO question, evidence, fit periods,
   holdout periods, files expected to change (`_templates/experiment.md`, status draft).
5. **Propose, tagged by type:**
   - **Parametric** (an assumption change): re-score it with a holdout (K04 › Holdout + a fit-only K01
     copy). Surface it **only if it lowers holdout fitness** (not in-sample), ranked by the delta. Clamp the
     move with K04 › Learning_Guards magnitude cap (±25% per cycle).
   - **Structural** (method/skill change, e.g. a dealer-scheme revenue lag): surface **only** when
     persistent_miss is TRUE for the line (same sign over K ≥ 2 closes) and it survived the one-time screen.
     Hand it to W12 to generate the skill *on approval* — propose, don't auto-write.
6. **Evaluate:** record before/after metrics and explicit checks in the experiment. A change that breaks
   reconciliation or another accounting invariant is failed even if a headline metric improves.
7. **Ratify and log:** present proposals; the human accepts/rejects. On accept add the decision, set
   `status: accepted` (explicit overwrite), update the champion (new K01 copy + model-versions row via W10's
   promotion when it replaces the champion), and append to `learnings.md`. Rejected and reverted
   experiments stay in memory.
8. **Run W10** when a miss warrants several autonomous challenger epochs instead of one manual proposal.

## Bootstrap (day one)
With ~12+ months of actuals, don't wait: run a holdout immediately (fit on the earlier months, hold out
the recent ones) to report current accuracy and the first round of parametric proposals.

## Guardrails
Never score on data the model was fit on. No proposal off a single period. Parametric changes must improve
holdout fitness. Cap moves per cycle. The human ratifies champion promotion. Missing or zero actuals are
insufficient evidence, not perfect performance.

## Next
Scored and learned → **W07** (report the forecast and how it is tracking).
