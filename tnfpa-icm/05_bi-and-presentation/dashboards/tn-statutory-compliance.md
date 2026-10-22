# Dashboard: Tamil Nadu statutory compliance

**Audience:** controller, company secretary  
**Refresh:** weekly  
**Sources:** 01_tamil-nadu/statutory-calendar.csv, D12, D24, D10

## Headline tiles
- Upcoming due dates (next 30 days)
- GST cash due (20th)
- TDS due (7th)
- PF/ESI due (15th)
- MSME dues > 45 days
- Overdue document reviews

## Charts
- Calendar strip of obligations
- MSME ageing buckets
- GST payable vs ITC trend

## Filters
month

## Rules
- Follow `../chart-standards.md`. State the unit (₹ lakh / ₹ crore) in every title.
- Stocks (cash, debt, balances) take the last period; flows sum; ratios are ratios of sums.
- Pre-close months are visually marked (hatched / lighter) and footnoted (W00).
- Before publishing, headline tiles must equal K01 › Summary / K02 › Runway for the same scenario.
