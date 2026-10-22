# W12 · Generate a company skill or agent (self-extending, not self-executing)

The toolkit re-tools itself per business instead of forcing a generic template. When the business profile
shows a gap the standard workflows don't cover, propose a bespoke **skill** (a markdown procedure + a
workbook) or **agent brief** (a role an agent plays with its own reading list), and write it only after
approval. Replaces openfpa `fpa-learn-business` steps 8–10 and the `skills/generated/` examples.

## Inputs
| Working | Reference |
|---|---|
| `memory/business-profile.md` facts; structural corrections; W09 structural proposals | `_templates/generated-skill/SKILL.md`, `_templates/generated-agent/AGENT.md` |
| the approved architecture | `examples/generated-skills/` (sku-profitability, segment-rollup) |
| | `02_kernel/formula-reference.md` (bespoke workbook rules), `04_domains/` templates |

## Process
1. **Find the gap** with evidence: a profile fact (e.g. "limited-SKU D2C brand where per-product
   economics drive the mix decision"), a human-authored structural correction (pre-ratified), or a W09
   persistent miss that survived the one-time screen.
2. **Propose** to the human: name, why (the cited facts), what it adds (procedure + workbook or domain
   template), the check that proves it works, what it touches in the model. No fact → no skill.
3. **Wait for approval.** Then copy `_templates/generated-skill/` to `companies/<slug>/skills/<name>/`
   (or `_templates/generated-agent/` to `agents/<name>/`), write `SKILL.md` with frontmatter
   `name, description (when to use), justified_by [facts/correction slugs], workbook`.
4. **Build the workbook** (copy a kernel or domain workbook when one fits — K06 for SKUs, K07 for segments —
   otherwise a bespoke workbook per formula-reference with Checks and parity rows).
5. **Record an experiment** (`memory/experiments/`) for any material model change it causes; register a
   workflow row if it becomes a recurring procedure.
6. **Never** write company skills into this workspace's factory folders. Only W11 may promote a skill into
   `portfolio/library/skills/`, and only after it recurs in ≥ 3 same-type clients and a human ratifies it.

## Typical generated skills (propose only when the profile justifies them)
| Business shape (TN examples) | Skill | Workbook |
|---|---|---|
| D2C / dealer product company with a discrete SKU set (furniture, pumps, appliances) | `sku-profitability` | K06 |
| Multi-segment group disclosing segment revenue + EBITDA (listed groups) | `segment-rollup` | K07 → K01 |
| SaaS / IT services on OMR (subscriptions) | `arr-waterfall-cohorts` | bespoke (cohort rows × months) |
| Trucking / logistics (Namakkal fleets) | `fleet-driver-cost-scorecard` | bespoke (vehicle × month) |
| Knitwear exporter (Tiruppur) | `order-book-and-export-incentive-cash` | bespoke + K02 flows |
| Dealer network with schemes (Coimbatore/Madurai) | `dealer-scheme-accrual-and-credit` | D06/D07 templates |
| Fireworks (Sivakasi) | `extreme-seasonality-working-capital` | K01 + K02 with pre-season stock build |

## Outputs
`skills/<name>/SKILL.md` (+ workbook), or `agents/<name>/AGENT.md`; experiment and workflow rows.

## Human check
Approval before writing; review of the first run's output.
