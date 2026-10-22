# W08 · Capture a correction (Learn)

A human reviewing a forecast is the highest-signal feedback there is — they catch structural errors and
domain knowledge a backtest cannot see, and catch them now. Turn it into durable, typed memory that
grounds every future forecast. **Core principle:** the human is the authority; capture, confirm the
interpretation once, then it persists. Everything is plain markdown the user owns.

**Use when:** "December always spikes", "you're double-counting the dealer scheme", "that Q3 number was a
one-time government order", "Pongal week collections always slip".

## The three correction types
- **parametric** — a concrete driver fix ("November runs ~1.9× a normal month"). Becomes an override
  (path + value) applied to every future forecast via the K01 › Corrections sheet.
- **structural** — a methodology fix ("you're double-counting deferred revenue", "model dealer schemes as
  a revenue deduction, not marketing"). A pre-ratified structural proposal (the human authored it) → W12 to
  generate the skill/model change. Do NOT wait for backtest misses.
- **context** — a one-time-item note ("that Q3 spike was a one-off TNEB tender"). Annotates so W00's
  one-time screen keeps the backtest from learning a one-off.

## Inputs
| Working | Reference |
|---|---|
| the human's statement; the forecast/close it refers to; `memory/corrections/` | `_templates/correction.md`, `00_system/schemas/correction.md` |
| champion K01 copy (ValidKeys sheet for paths) | `00_system/naming-and-ids.md` |

## Process
1. **Classify** (parametric / structural / context).
2. **Identify the target** — driver path (e.g. `channels[*].seasonality[10]` for November,
   `working_capital.dio_days`), line, or profile area. For parametric draft `override: {path, value}`
   (0-based indexes; `[*]` = all).
3. **Write** `memory/corrections/<YYYY-MM-DD>-<short-name>.md` from the template: frontmatter (type,
   target, status: open, date, override) and body (**Was off:** … **Correction:** … **Why:** [[links]]).
4. **Confirm interpretation:** echo the concrete change ("I'll set November seasonality to 1.9 on all
   channels — right?"). Only on confirmation set `status: applied`; for parametric, add the row to the
   champion's Corrections sheet and confirm Checks PASS (no duplicate applied path, path resolves).
5. **Keep `memory/MEMORY.md` current** (it indexes the vault) and rebuild `memory/index.csv`.

## Applying corrections
Every forecast copy of K01 carries all applied parametric corrections in its Corrections sheet. They are
seeds, not mandates — the per-company loop (W09/W10) refines from there.

## Guardrails
Confirm before `applied`. Reversible via status (open/applied/superseded). The backtest monitors applied
corrections and may *flag* a stale one; it never reverts — the human decides.

## Outputs
A correction file; updated K01 Corrections (parametric); updated MEMORY.md and index.csv.

## Next
Correction captured → re-run **W04** / **W07** grounded by it; structural → **W12**.
