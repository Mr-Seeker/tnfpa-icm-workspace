# W10 · Company research loop (AutoResearch-style champion/challenger)

Run bounded autonomous research against the company's own forecast history (inspired by Karpathy's
AutoResearch: define an objective, run bounded experiments, keep measurable improvements, preserve failed
attempts so they are not repeated without new evidence). The AI may generate, test and discard challengers
autonomously **after Gate 1**. Only promotion to champion needs human approval (**Gate 2**).

## Memory and state
- `memory/research/objective.md` — company metrics, weights, hard checks, min improvement, complexity
  penalty, max metric regression.
- `memory/research/epochs/*.md` — every hypothesis and evaluated epoch, including discarded ones.
- `memory/models/model-versions.csv` + `promotions.csv` — champion, challengers, retired, approvals.
- `memory/index.csv` — rebuildable lexical index; `memory/context-pack.md` — temporary retrieval output.

## Inputs
| Working | Reference |
|---|---|
| workflows of kind `research`; scored snapshots; prior epochs | `02_kernel/K05_research-evaluator.xlsx`, `K04…`, `K01…`, `K11…` |
| the miss being investigated (from W09) | `_templates/epoch.md`, `00_system/schemas/research-epoch.md` |

## Process
1. **Discover the company procedure** (workflows kind `research`).
2. **Retrieve context:** rebuild `index.csv`, build a context pack (K11) for the miss; read prior
   *failed* epochs before proposing a repeated hypothesis.
3. **Load the objective and registry** into K05 › Objective. The objective is CFO-specific: forecast-error
   metrics by decision importance, hard accounting checks, minimum improvement, complexity penalty.
4. **Run bounded epochs** — at most five challengers per run. For each:
   - state one falsifiable financial hypothesis;
   - make the smallest company-specific change in a challenger copy (`models/K01_challenger-<slug>.xlsx`);
   - fit only on training periods; score on rolling/holdout periods not used to fit (K04);
   - run every hard check (K01/K03 Checks; holdout separation documented);
   - enter champion and challenger metrics, complexities and check results in K05 › Epochs;
   - write the epoch file (`memory/research/epochs/<epoch_id>.md`) with the evaluation copied from K05.
5. **Discard autonomously:** mark failed/weak candidates `discarded`; preserve their workbook reference,
   evidence, metrics and rejection reason so future agents do not repeat them without new evidence.
6. **Propose the strongest challenger:** register only promotion-eligible challengers
   (`model-versions.csv` role challenger, source_epoch = epoch_id); mark that epoch `proposed`; explain
   the objective gain, trade-offs, complexity cost and relevant memory.
7. **Promote only after approval (Gate 2):** with the human's explicit acceptance fill K05 › Promotion
   (approved_by, date). Only if it says PROMOTE: challenger → champion, old champion → retired, append
   `promotions.csv`, set the epoch to `promoted`, append `learnings.md`.

## Guardrails
Experiment autonomously only after architecture approval. Never tune and score on the same periods. Hard
accounting/reconciliation checks override metric gains. Do not promote a larger model unless the gain beats
its complexity cost. No evidence → no experiment; no holdout → no promotion. Human approval is needed only
for promotion, not for each epoch.

## Outputs
Challenger workbooks, epoch files, registry rows, learnings.
