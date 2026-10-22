# Ridgeline parity — proof that the no-code kernel equals openfpa

Synthetic product company from openfpa (`examples/ridgeline/`), loaded unchanged into the kernel workbooks.

| File | Proves |
|---|---|
| `models/K01_ridgeline.xlsx` | P&L and indirect cash flow for 12 months. Checks contain GOLDEN rows equal to openfpa's `docs/demo/briefing.md`: revenue 6,000,000; EBITDA 824,000; net income 572,651; ending cash 720,418. Every month and line matched an independent re-implementation of `pyfpa.cashflow_from_config` to < 1e-12 relative error, and the Briefing sheet reproduces the briefing markdown character for character. |
| `models/K02_ridgeline.xlsx` | 13-week cash: trough −146,000 in week 7, first negative week 3 (GOLDEN rows) — the inventory build that creates a liquidity gap before seasonal collections. |
| `models/K06_ridgeline-skus.xlsx` | SKU ranking and Pareto breakpoint 4, identical to `pyfpa.sku_profitability`. |
| `data/fixtures/*.csv` | openfpa's fixture adapters (QuickBooks, NetSuite, Shopify) — use them to practise W03 reconciliation in K03. |
| `output/briefing.md` | openfpa's published briefing (the target the workbooks reproduce). |

To re-verify: open each workbook in any spreadsheet engine, let it recalculate, read `Checks` → OVERALL = PASS.
Currency here is USD (as in openfpa); the workbook's `number_style` is set to western and `currency_symbol` to `$`.
