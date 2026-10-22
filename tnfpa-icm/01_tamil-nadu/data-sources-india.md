# Data sources and no-code export recipes (W03 connectors)

The connector is a **recipe + fixture + golden totals** (`00_system/schemas/connector.md`). The export
itself is done by the human, by the ERP's own scheduler, or by an approved MCP server — never by code here.

| Source | Typical export (human or MCP) | Normalise to | Watch out for |
|---|---|---|---|
| **Tally Prime** | Gateway of Tally → Display More Reports → Trial Balance / Profit & Loss → set period (F2) → Export (Ctrl+E) → CSV/Excel, "Show closing balance only", ledger-wise | `Account,Amount` with Dr/Cr suffix or separate Debit/Credit columns (K03 parses "1,20,000.00 Cr") | group vs ledger level; stock journal timing; multiple companies (one per FY); duplicate ledger names across groups |
| **Zoho Books** | Reports → Profit and Loss / Trial Balance → Export as CSV/XLSX (or Zoho Analytics scheduled export; or an approved Zoho MCP connection) | `Account,Amount` | accrual vs cash basis toggle; branches/locations as separate columns |
| **SAP S/4HANA / Business One** | financial statement version export (S_ALR / F.01) or B1 Trial Balance → Excel | `Account,Amount` + profit centre | sign convention (credits negative) |
| **Oracle NetSuite** | saved search / financial report → CSV (or approved MCP) | `Account,Amount` | subsidiaries and intercompany (W00) |
| **Ramco / Marg / Busy** | standard TB/P&L report → Excel | `Account,Amount` | column headers vary — map once |
| **Bank statements** | net-banking → statement → CSV/XLSX | dated receipts/payments for K02 | flash vs GL cash (W00) |
| **GST portal** | GSTR-2B (download JSON → view as Excel via the portal's offline tool), GSTR-1/3B summaries (PDF/Excel) | ITC and output tax by month for D24 | 2B vs books mismatch; timing of supplier filing |
| **TRACES / Form 26AS / AIS** | download statements | TDS credits for D24 | mismatch with books |
| **EPFO / ESIC** | ECR and challan reports | PF/ESI cash for K02, D04 | arrears |
| **MCA21** | company master data, filed financials (public) | public comparables, D19/D21 | — |
| **BSE / NSE** | results and shareholding pattern (public) | listed comparables, D19 | — |
| **RBI DBIE, MoSPI, FBIL, TN Dept of Economics & Statistics, IMD** | public data downloads | D14 macro register (dated) | — |
| **Shopify / Amazon Seller Central / Flipkart Seller Hub** | payouts and order reports | channel revenue, fees, TCS/TDS credits | settlement lag → K02 receipts |
| **Spreadsheet the company already keeps** | itself | profile with K03 first | hidden rows, merged cells, totals inside data |

Credentials stay with the host tool or the human. Never place passwords, OTPs or API keys in this
workspace. Every recurring source gets: a registered source, exact mappings, a redacted fixture, golden
mapped totals, documented failure behaviour, and a validation log.
