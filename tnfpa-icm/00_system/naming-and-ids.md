# Naming and ids

| Thing | Rule | Example |
|---|---|---|
| company slug | lowercase letters, digits, hyphens; city suffix optional | `kaveri-chairs-coimbatore` |
| source_id, connector name, workflow name | `^[a-z][a-z0-9-]*$` | `tally-pl-monthly` |
| correction slug | `<YYYY-MM-DD>-<short-name>` (whole slug = filename) | `2026-11-02-deepavali-spike` |
| experiment slug, epoch_id | `^[a-z0-9][a-z0-9._-]*$` | `kvr-fy2627-003-pongal-lag` |
| model_id | `<company>-<what>-<version>` | `kvr-k01-v2-dealer-dso` |
| snapshot label | the forecast period or cycle | `2026-10` or `LE-Oct-FY2026-27` |
| fiscal year label | `FY<start>-<end yy>` (April–March) | `FY2026-27` |
| fiscal quarter | Q1 = Apr–Jun … Q4 = Jan–Mar | `FY2026-27 Q3` |
| dates | ISO `YYYY-MM-DD` everywhere in files (display may use DD-MM-YYYY) | `2026-10-18` |
| amounts in files | full rupees, no separators, negative with `-` | `-146000` |
| amounts in reports | ₹ with Indian grouping or a stated unit (₹ lakh / ₹ crore) | `₹1,46,000` · `₹1.46 lakh` |
| workbook copies | `<kernel id>_<purpose>.xlsx` inside `companies/<slug>/models/` | `K01_champion.xlsx`, `K01_challenger-dso.xlsx` |
| domain records | `companies/<slug>/domains/Dnn_<slug>/` | `domains/D24_tax-transfer-pricing/` |

Path rules: always relative to the company root; never absolute; never containing `..`.
Reserved names: `total` (channel/opex line), `index.csv` and `context-pack.md` (never indexed).
