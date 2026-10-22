# 05_bi-and-presentation — dashboards, data model and board templates (factory)

**Job:** turn kernel outputs into things people look at — BI dashboards, board decks, memos, MIS packs —
without code. BI tools read the CSV star schema; office suites open the templates.

| Path | What |
|---|---|
| `data-model/` | star schema: fact and dimension CSV headers, `dim_period_india.csv` (Indian FY calendar 2020-21 → 2035-36), `measures.csv` (plain-language measure definitions), `data-dictionary.csv`, `relationships.csv` |
| `dashboards/` | dashboard specifications (purpose, audience, tiles, charts, filters, refresh, source files) |
| `chart-standards.md` | how every chart must look (one system across Excel, PowerPoint and BI) |
| `theme/tnfpa-bi-theme.json` | colour/typography theme file importable by Power BI-style tools (data, not code) |
| `templates/board-briefing-template.pptx` | board / lender deck with `{{placeholders}}` and native, editable charts |
| `templates/board-memo-template.docx` | board memo with the same structure |
| `templates/monthly-mis-inr-lakh.xlsx` | paste K01 Export_Rows → ₹ lakh MIS with FY totals and checks |
| `templates/communications.md` | lender update email, WhatsApp/Teams status note, investor update outline |

**How a dashboard gets data (no code):** each refresh, copy K01 › Export_Rows (values) into
`companies/<slug>/output/bi/fact_monthly_model.csv`, K02 › Weekly into `fact_cash13.csv`, mapped actuals
into `fact_actuals.csv`; point the BI tool's file/folder connector at `output/bi/` and press refresh.
Relationships and measures are configured by clicks from `data-model/relationships.csv` and `measures.csv`.
**Human check:** the CFO compares dashboard headline tiles with K01 › Summary before publishing.
