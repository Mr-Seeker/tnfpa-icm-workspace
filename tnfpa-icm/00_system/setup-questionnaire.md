# Setup questionnaire (configure the factory once per organisation)

Ask these once, when the workspace is first opened by a new firm or finance team, and record the answers
in `00_system/setup-answers.md` (create it from the table below). Company-level facts belong in each
company's intake, not here.

| # | Question | Default if unanswered | Used by |
|---|---|---|---|
| 1 | Which spreadsheet engine will recalculate the workbooks (Excel / LibreOffice / Google Sheets / Zoho Sheet / OnlyOffice / WPS)? | Microsoft Excel | every K/D workbook (if Google Sheets: upload, recalculate, download as .xlsx) |
| 2 | Which BI tool, if any (Power BI / Tableau / Looker Studio / Zoho Analytics / Metabase / none)? | none (Excel charts) | `05_bi-and-presentation/` |
| 3 | Which office suite for decks and memos (Microsoft 365 / Google Workspace / Zoho Workplace / LibreOffice)? | Microsoft 365 | W07 templates |
| 4 | Report units and grouping: ₹ lakh, ₹ crore or full rupees; Indian or western grouping? | ₹ lakh, Indian grouping | K01 display settings, W07 |
| 5 | Board-pack language: English only, or English with Tamil labels? | English | `01_tamil-nadu/number-and-language.md` |
| 6 | Who is the human approver for Gate 1 and Gate 2 by default (role)? | CFO (Gate 2 also MD for family-owned firms) | W01, W10, D08 DoA |
| 7 | Is a CA / tax adviser available to confirm statutory rates (name of firm, not personal details)? | none — flag every rate as "to confirm" | `01_tamil-nadu/verification-register.md` |
| 8 | Which external systems may the agent ever access with approval (MCP servers, ERP exports, bank portals)? | none — files supplied by humans only | W03, guardrails |
| 9 | Will this workspace hold several clients (practice / CA firm) or one company? | one company | W11, `portfolio/` |
| 10 | Default fiscal year start month and close deadline (working day)? | April; WD6 | W04, K01 start_month |
