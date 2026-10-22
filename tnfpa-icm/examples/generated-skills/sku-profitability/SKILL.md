---
name: sku-profitability
description: Use when analysing which products make or lose money, ranking SKUs by margin or contribution, running a Pareto/80-20 on a product line, or deciding which SKUs to cut, reprice or push in a product business.
justified_by: ["business profile: product company with a discrete SKU set (example)"]
workbook: 02_kernel/K06_sku-profitability.xlsx
---

# SKU profitability (generated skill — example)

> **Example.** This is the kind of bespoke skill W01/W12 proposes when the business profile says
> *"product company with a discrete SKU set"*. In a real engagement it is written into
> `companies/<slug>/skills/` after human approval, citing the profile facts that justify it (e.g. a
> limited-SKU D2C furniture brand in Coimbatore where per-product economics drive the mix decision).

The channel-level forecast tells you the business is healthy; it doesn't tell you *which products* carry
it. This skill computes per-SKU economics and the Pareto curve so you can see the 80/20, find
margin-dilutive SKUs, and make cut/reprice/push calls. **Core principle:** revenue flatters; margin and
contribution decide. Rank by gross profit, not sales.

## When to use
"Which products actually make money?" · "what should we cut?" · product-mix, pricing or assortment
decisions · any product business with a discrete SKU set.

## Workflow
1. Copy `02_kernel/K06_sku-profitability.xlsx` to `companies/<slug>/skills/sku-profitability/`.
   Enter annual units, net selling price (ex-GST) and unit cost per SKU on `SKUs`.
2. Read `Ranked`: sorted by gross profit (desc) with units, revenue, COGS, gross profit, gross margin,
   revenue share and cumulative revenue %. `pareto_breakpoint` = SKUs making the first 80% of revenue.
3. Read the signals:
   - **Top of the list** (high gross profit) — protect and push.
   - **High revenue, low gross margin** — reprice or renegotiate cost; they buy share with your margin.
   - **Low revenue share AND low margin** — candidates to cut (carrying cost without contribution).
   - **The Pareto tail** — if the bottom SKUs add complexity (SKUs to manage, inventory, dies/moulds) without margin, rationalise.
4. Recommend in business terms: which SKUs to push, reprice or discontinue, and the margin impact of each.

## Judgment checks (W00)
Gross margin here is price minus unit cost only — it excludes marketplace commission (Amazon.in/Flipkart),
dealer schemes, freight, returns and fulfilment, and any blocked GST credit. A D2C SKU and a dealer SKU at
the same listed margin are not equally profitable once channel economics hit (use D13 › Waterfall for the
pocket price). A "high-margin" SKU with tiny volume may not be worth its complexity — weigh contribution
rupees, not just the percentage.

## Verification
On openfpa's Ridgeline SKUs the workbook ranks Summit Camp Chair (GP 918,000), Basecamp Lounger (738,000),
Ridgeback Recliner (624,000), Trail Stool (506,000), Kids Trail Chair (324,000) with cumulative revenue
28.7% / 52.7% / 74.1% / 89.5% / 100% and a Pareto breakpoint of 4 — identical to `pyfpa.sku_profitability`.
