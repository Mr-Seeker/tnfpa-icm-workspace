# Dashboard: Forecast accuracy and learning

**Audience:** CFO, audit committee  
**Refresh:** after each scored close  
**Sources:** fact_scorecard, memory/experiments, memory/models/promotions.csv

## Headline tiles
- Latest fitness
- Lines with persistent misses
- Experiments accepted / rejected this year
- Champion promotions (with approver)

## Charts
- Per-line error by period (heatmap, diverging around 0)
- Fitness trend

## Filters
line, period

## Rules
- Follow `../chart-standards.md`. State the unit (₹ lakh / ₹ crore) in every title.
- Stocks (cash, debt, balances) take the last period; flows sum; ratios are ratios of sums.
- Pre-close months are visually marked (hatched / lighter) and footnoted (W00).
- Before publishing, headline tiles must equal K01 › Summary / K02 › Runway for the same scenario.
