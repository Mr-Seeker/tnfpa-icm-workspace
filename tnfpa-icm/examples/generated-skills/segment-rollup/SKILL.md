---
name: segment-rollup
description: Use when modelling a multi-segment company that discloses segment net sales and segment Adjusted EBITDA but not segment COGS or operating income — rolls segment P&Ls into a consolidated forecast and reconciles total segment Adjusted EBITDA to the disclosed total. Generated for Fox Factory (PVG/AAG/SSG).
justified_by: ["examples/foxfactory-public-proof/memory/business-profile.md: three reportable segments; segment metric is Adjusted EBITDA (ASU 2023-07); segment WC, debt and tax not disclosed"]
workbook: 02_kernel/K07_segment-rollup.xlsx
---

# Segment roll-up (generated for Fox Factory)

## Why this skill exists
The standard workflows model a single entity. Fox Factory reports **three segments** and discloses
**net sales and Adjusted EBITDA per segment — but not segment COGS or operating income**. Segment working
capital, debt and tax are not disclosed, so segments drive the P&L down to Adjusted EBITDA only and the
consolidated layer owns everything below. (The same shape applies to Indian listed groups reporting
operating segments under Ind AS 108 with segment revenue and segment results.)

## Model shape
```
segment net sales + Adj EBITDA margin (PVG, AAG, SSG)
   │ K07 › Segments (roll-up)        → total net sales + total Adj EBITDA (margin recomputed, never averaged)
   │ K07 › ToChannels (blended cogs) → revenue channels for K01
   ▼
consolidated K01 (blended COGS%, one adjusted_opex line, D&A, capex, WC days, debt, tax)
   ▼
consolidated P&L + indirect cash flow (revenue → … → FCF)
```

## How to use
1. One K07 › Segments row per segment from disclosed net sales and Adjusted-EBITDA margin
   (adjusted EBITDA / net sales).
2. Read the TOTAL row and **reconcile it to the disclosed segment-footnote total** — it must tie.
3. Copy K07 › ToChannels into the K01 channel rows (blended consolidated COGS% on every segment; channels
   sum back to consolidated COGS by construction).
4. In K01 set one fixed opex line `adjusted_opex` = (gross profit − total adjusted EBITDA) / 12 per month so
   engine EBITDA ties to segment Adjusted EBITDA.
5. Keep goodwill impairment and discrete tax items **out** of the engine, in a documented bridge to
   reported net income — the lean engine models the operating business, not one-time non-cash charges.
6. For forecast years use K07 › SegmentForecast (per-year growth and margin per segment).

## Reference implementation
`examples/foxfactory-public-proof/` (Phase A reproduction workbooks, Phase C forecast workbooks).

## Guardrail
This skill belongs in the client's own `skills/` namespace — it is specific to a segment-reporting company
and must not be promoted into the factory unless W11 finds it recurring across ≥ 3 same-type clients.
