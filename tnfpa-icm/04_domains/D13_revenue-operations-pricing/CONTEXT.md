# D13 · Revenue operations & pricing optimisation

**Job:** Explain revenue with a price–volume–mix bridge and see true pocket price after GST, dealer discounts, schemes, marketplace commission and freight.

## Systems of record (Tamil Nadu / India)
CRM (D07), ERP sales registers, marketplace seller reports (Amazon.in, Flipkart, Meesho), price lists.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D13_revenue-operations-pricing/` | `D13_revenue-operations-pricing.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D13_revenue-operations-pricing.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D13_revenue-operations-pricing/`.
2. Replace the sample rows with the company's data (sheets: PVM (prior/current units and price → volume, mix, price effects), Bridge (reconciles to current revenue), Waterfall (MRP incl. GST → pocket price)). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 channels growth_rate / cogs_pct | PVM trends |
| W04 variance drivers | volume / price / mix |
| K06 SKU economics | pocket price |

## Tamil Nadu notes
- MRP is GST-inclusive (Legal Metrology packaged-commodity rules) — always strip GST before margin analysis.
- Aadi and Deepavali discounting shift mix to promotional SKUs; separate mix from price.

## Used in workflows
W04, W07, W12

## Human check
Sales/pricing head reviews the bridge before it is used in a board narrative.
