# No-code policy

The workspace must stay 100% no-code: no programming languages, scripts, macros, notebooks,
containers, package managers, command lines or execution environments. Determinism comes from
spreadsheet recalculation and from written decision rules, not from programs.

## Allowed file types

| Purpose | Types |
|---|---|
| Contracts, memory, narrative, frontmatter records | `.md` (markdown with YAML frontmatter as plain data) |
| Registries, fact tables, BI data model | `.csv` (UTF-8, comma, header row; a file containing ₹, Tamil or other non-ASCII text starts with a UTF-8 BOM so Excel opens it correctly), `.tsv` |
| Calculation engines and templates | `.xlsx` (no macros); `.ods` / Google Sheets copies are equivalent |
| Board decks and memos | `.pptx`, `.docx`, `.pdf` exports; `.odp` / `.odt` equivalents |
| BI theme / dashboard configuration | `.json` theme files read by BI tools (data, not code) |
| Images for decks | `.png`, `.svg` |

**Forbidden:** `.py`, `.js`, `.ts`, `.sh`, `.ps1`, `.bat`, `.vba`/`.bas`, macro-enabled `.xlsm`/`.pptm`/`.docm`,
`.ipynb`, Power Query **M** text, DAX/SQL **script files**, Dockerfiles, `requirements.txt`, `package.json`,
YAML used as program configuration, add-ins, external data connections that refresh automatically.
A BI tool may hold *point-and-click* measures and relationships configured from
`05_bi-and-presentation/data-model/measures.csv`; those definitions are written in plain language and
spreadsheet-style formulas, never as stored script files.

## Allowed formula vocabulary (every major engine supports these)

Arithmetic, `^`, comparison; `SUM SUMIF SUMIFS SUMPRODUCT COUNT COUNTA COUNTIF COUNTIFS AVERAGE MEDIAN
STDEVP MIN MAX SMALL LARGE ABS ROUND ROUNDUP INT MOD IF IFERROR AND OR NOT ISNUMBER N INDEX MATCH
EDATE DATEDIF DAY MONTH YEAR TODAY TEXT LEFT RIGHT MID LEN TRIM LOWER UPPER SUBSTITUTE SEARCH REPT
CODE VALUE NPV IRR PV`. No dynamic-array-only functions (`UNIQUE`, `FILTER`, `LET`, `LAMBDA`, `XLOOKUP`)
so files behave identically in Excel 2016+, LibreOffice, Google Sheets and Zoho Sheet.
Avoid whole-column references (`A:A`) — use bounded ranges.

## Workbook conventions

- Pale-yellow cells with blue text are the only cells anyone types into. White cells are formulas.
- Every workbook has `README` (purpose, how to use) and `Checks` (OVERALL PASS/FAIL) sheets.
- Workbooks are saved with "recalculate on open". The kernel copies in `02_kernel/` are read-only
  masters: copy them into a company folder before typing anything.
- When results must leave a workbook, copy the rendered text/values (e.g. Briefing, Scorecard, Pack
  sheets) into the target markdown file verbatim.
