# W11 · Portfolio learn (Loop B — your practice compounds)

Loop A (W09/W10) makes the model better at one client. This makes the **practice** compound: client #10
starts smarter than client #1 because the library carries what generalised across #1–9. Everything is
local — your own book, in this workspace. **Core principle:** self-improving, never self-ratifying. The
objective is cross-client: does a pattern learned on some clients not degrade the others' backtests?

## Setup
`portfolio/portfolio.csv` lists client workspaces and a business-type tag, e.g.
`companies/kaveri-chairs-coimbatore,tn-furniture-d2c-dealer` · `companies/abc-knits-tiruppur,tiruppur-knitwear-export`.

## Inputs
| Working | Reference |
|---|---|
| `portfolio/portfolio.csv`; each client's scored snapshots and corrections; `skills/` folders | `02_kernel/K09_portfolio-learning.xlsx`, `K04…`, `K01…` |
| `portfolio/library/` | `00_system/schemas/portfolio.md` |

## Process
1. **Load** the manifest into K09 › Clients: for each client its best (lowest-fitness scored) snapshot
   (K04 › Snapshots best_snapshot) and the six mineable driver values from that snapshot's assumptions
   workbook (DSO, DIO, DPO, tax_rate, da_monthly, capex_monthly) — replaced by an **applied parametric
   correction on the exact same path** if one exists.
2. For each business type with **at least 3 clients**:
   - **Priors:** K09 › Mine lists drivers that cluster tightly (CoV ≤ 0.15, support ≥ 3) at the median.
     Validate each with K09 › Validate (leave-one-out: for each client re-run its best-snapshot K01 copy with
     the peer median, score with K04 on the same lines/weights against recovered actuals, enter the new
     fitness). Surface validated priors first (by mean delta), then unvalidated/judgement ones.
   - **Skills:** K09 › Skills finds generated-skill folder names recurring in ≥ 3 same-type clients. Also
     weigh recurring **structural corrections** across clients — a human-authored pattern that repeats is
     strong signal.
3. **Present** candidates ranked by evidence (support count + cross-client delta).
4. **Ratify:** on the user's acceptance append the prior to `portfolio/library/priors/<type>.csv`, copy the
   skill folder to `portfolio/library/skills/<name>/`, and add a line to `library-log.md`. Reversible.

## Guardrails
Local only. At least 3 clients to propose; tight clusters only; a prior must not degrade held-out clients.
You ratify everything; priors are seeds, not mandates — each client's loop refines them.

## The payoff
New clients inherit the library: W01 step 7 seeds their starting model from promoted priors (as
assumption values, recorded as such) and offers the promoted skills.
