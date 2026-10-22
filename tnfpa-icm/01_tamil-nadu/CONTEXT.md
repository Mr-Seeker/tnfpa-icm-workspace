# 01_tamil-nadu — local context (factory, stable; re-verify on change)

**Job:** everything an agent needs to make openfpa-style FP&A correct for a company operating in
Tamil Nadu, India: fiscal calendar, statutory obligations and their cash dates, tax mechanics, labour
costs, reporting framework, chart-of-accounts mapping, seasonality priors, sector clusters,
institutions, data sources and number/language conventions.

| File | Use it in |
|---|---|
| `fiscal-and-close-calendar.md` | W01 intake (planning_cadence), W02 start_month, W04 close timetable |
| `statutory-calendar.csv` | W05 13-week cash (dated statutory outflows), D03, D24 |
| `tax-reference.md` | W02 tax_rate, W05 GST/TDS/advance-tax flows, D24 |
| `labour-and-payroll.md` | D04/D05 payroll cost, K02 payroll flows |
| `reporting-framework.md` | D03 statutory reporting, W07 board pack wording |
| `schedule-iii-mapping.csv` | W03 mapping registry seeds (Tally groups → Schedule III → kernel targets) |
| `seasonality-library.csv` | W02 seasonality starting weights (priors, never facts) |
| `sector-clusters.md` | W01 business-model questions, D14 macro links |
| `institutions-and-ecosystem.md` | D15 banking, D20 corporate development, D29 networks |
| `data-sources-india.md` | W03 connectors and export recipes (Tally, Zoho, SAP, GST portal, banks) |
| `number-and-language.md` | every report: ₹, lakh/crore, Indian digit grouping, Tamil labels |
| `verification-register.md` | before relying on ANY rate, threshold or due date |

**Rule:** rates, thresholds and due dates change by notification. Treat every number here as "as
recorded on the date in `verification-register.md`". If the register is older than the period you are
modelling, ask the human (or their CA) to confirm, then update the register — do not guess.
