# Chart standards (one system across Excel, PowerPoint and BI)

1. **Title says the takeaway**, subtitle says the unit and scope: "Cash dips below zero in week 3 — ₹ lakh, 13 weeks from 6 Apr 2026".
2. **Form follows the question:** trend → line; comparison of a few categories → bars; composition over time
   → stacked columns (≤ 5 series); bridge → waterfall; distribution of errors → heatmap or dot plot.
   No pies with more than 3 slices; no 3-D; no dual axes unless both share a unit.
3. **Colour roles** (from `theme/tnfpa-bi-theme.json`): actual = navy, latest estimate = teal, budget = grey,
   challenger = amber, negative/alert = red, positive/ok = green. Colour encodes meaning, never decoration.
4. **Reference lines** for limits: zero line on cash charts, CC/OD limit line, covenant thresholds.
5. **Indian grouping or a stated unit** — never raw 9-digit numbers. Two decimals in ₹ lakh / ₹ crore.
6. **Pre-close months** lighter or hatched with a footnote; forecast months visually distinct from actuals.
7. **Accessible:** contrast ≥ 4.5:1 for text; do not rely on red/green alone (add labels or markers).
8. **Tamil labels** optional as a second line under the English axis title (number-and-language.md).
