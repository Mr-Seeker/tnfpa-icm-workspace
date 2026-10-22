# Verification register

Every rate, threshold and due date in `01_tamil-nadu/`, `04_domains/` templates and K-workbook defaults
is a **starting value**, recorded here with the date it was written. Before using one for a decision:
check the "last verified" date; if it is older than the modelling period or a notification may have
changed it, confirm with the official source or the company's CA, then update this table.

| Item | Value used | Where used | Official source to check | Last verified |
|---|---|---|---|---|
| Corporate tax, s.115BAA effective | 25.168% | K01 default tax_rate; D24 | Income-tax Act 2025 / Finance Act | 2026-10-18 (workspace build; confirm new-Act section) |
| Income-tax Act 2025 in force | from 1 Apr 2026 | tax-reference.md | CBDT notifications | 2026-10-18 |
| Advance tax schedule | 15/45/75/100% on 15 Jun/Sep/Dec/Mar | D24; statutory-calendar.csv | Income-tax Act | 2026-10-18 |
| GST slabs after rationalisation | 5% / 18% / 40% (+ special) | tax-reference.md; D24 defaults (18%) | GST Council / CBIC rate notifications | 2026-10-18 |
| GSTR-1 / GSTR-3B monthly due days | 11th / 20th | statutory-calendar.csv; K02 DateToWeek | CGST Rules / GSTN | 2026-10-18 |
| QRMP GSTR-3B group for Tamil Nadu | 22nd | statutory-calendar.csv | CBIC notification | 2026-10-18 |
| E-commerce GST TCS / IT TDS 194-O | 0.5% / 0.1% | tax-reference.md | CBIC / CBDT | 2026-10-18 |
| TDS deposit due day | 7th (March: 30 Apr) | statutory-calendar.csv | Income-tax Rules | 2026-10-18 |
| EPF rates and wage ceiling | 12% + 12%; ₹15,000 | D04 Rates | EPFO | 2026-10-18 |
| ESI rates and wage limit | 3.25% + 0.75%; ₹21,000 | D04 Rates | ESIC | 2026-10-18 |
| Gratuity ceiling | ₹20 lakh | D16; labour-and-payroll.md | Payment of Gratuity Act / Social Security Code | 2026-10-18 |
| Bonus eligibility wage | ₹21,000 | D04 | Payment of Bonus Act / Code on Wages | 2026-10-18 |
| Labour Codes in force | November 2025 | labour-and-payroll.md | Ministry of Labour notifications; TN rules | 2026-10-18 |
| MSME payment limit | 45 days | D12; tax-reference.md | MSMED Act s.15; IT Act s.43B(h) | 2026-10-18 |
| TN professional tax cap | ₹2,500 per year | labour-and-payroll.md | Constitution Art. 276; local body slabs | 2026-10-18 |
| TN Labour Welfare Fund | employer ₹40 / employee ₹20 per year (template default) | D04 Rates | TN Labour Welfare Board | 2026-10-18 (confirm current amounts) |
| CSR thresholds | NW ₹500 cr / TO ₹1,000 cr / NP ₹5 cr; 2% | D28 CSR | Companies Act s.135 | 2026-10-18 |
| Grid emission factor | 0.71 kgCO2/kWh (template default) | D23 Factors | CEA CO2 Baseline Database (latest version) | 2026-10-18 (replace with latest CEA value) |
| Transfer-pricing range | 35th–65th percentile, 6+ comparables | D24 TPRange | Income-tax Rules (range concept) | 2026-10-18 |
| Ind AS applicability | listed or NW ≥ ₹250 crore | reporting-framework.md | Companies (Ind AS) Rules | 2026-10-18 |
| SEBI LODR results timelines | 45 days / 60 days annual | D19 Calendar | SEBI LODR | 2026-10-18 |
| USD/INR in D11 | 88.00 (placeholder) | D11 Setup | FBIL reference rate | placeholder - always replace |

When you update a value, change it in the file that uses it AND here (one home per fact: the workbook
cell holds the value; this table holds its provenance).
