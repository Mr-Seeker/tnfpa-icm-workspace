# Dashboard: CFO cockpit

**Audience:** CFO, MD, board  
**Refresh:** after every close (W04) and every cash run (W05)  
**Sources:** fact_monthly_model, fact_actuals, fact_cash13, fact_scorecard

## Headline tiles
- Revenue (FY to date, vs budget)
- Gross margin % (ratio of sums)
- EBITDA and EBITDA margin
- Ending cash and net debt (state flash vs GL)
- 13-week trough and first negative week
- Forecast fitness (latest) and trend

## Charts
- Monthly revenue and EBITDA: actual vs LE vs budget (column + line)
- Ending cash by month with CC limit reference line
- Scorecard fitness over time (line, lower is better)

## Filters
company, scenario, fiscal year, quarter

## Rules
- Follow `../chart-standards.md`. State the unit (₹ lakh / ₹ crore) in every title.
- Stocks (cash, debt, balances) take the last period; flows sum; ratios are ratios of sums.
- Pre-close months are visually marked (hatched / lighter) and footnoted (W00).
- Before publishing, headline tiles must equal K01 › Summary / K02 › Runway for the same scenario.
