# W07 · Board briefing (Operate)

Turn forecast output into a board / investor / lender-grade briefing: the headline numbers, the cash
story, what changed, the risks and the ask — as markdown, a deck and a memo. Make the operator look like
they have a CFO. **Core principle:** a board wants the story and the three things that matter, not a dump.

**Use when:** board decks, investor updates, bank/lender packages (CC renewal, term-loan review), "summarise
the forecast for leadership".

## Inputs
| Working | Reference |
|---|---|
| workflows of kind `report` (use a registered briefing procedure if one exists) | `05_bi-and-presentation/templates/board-briefing-template.pptx`, `board-memo-template.docx` |
| champion K01 copy (Summary, Briefing), latest K02 Runway | `05_bi-and-presentation/dashboards/cfo-cockpit.md`, `chart-standards.md` |
| latest close narrative (`output/<period>-close.md`), D15 covenants, D19 (listed) | `01_tamil-nadu/number-and-language.md`, `03_workflows/W00_cfo-judgment/` |

## Process
1. **Discover the company procedure** (workflows kind `report`).
2. **Build the forecast** — the champion K01 (monthly) and, optionally, the latest K02 runway. Enter the
   runway values into K01 › Briefing B3:B6.
3. **Render the briefing:** copy K01 › Briefing column D (headline: revenue, EBITDA, net income, ending
   cash; optional 13-week runway: trough and week, first negative week; monthly table) — this is the data spine.
4. **Add the narrative the renderer can't:** prepend `## What changed` (the 3 things that moved) and append
   `## Risks` (3 forward risks) and `## The ask` (e.g. "approve enhancement of the cash-credit limit to
   ₹2.4 crore before week 3 to bridge the Deepavali stock build"). Save `output/<date>-board-briefing.md`.
5. **Apply judgment** (W00): caveat any pre-close month, say whether cash is bank flash or GL, say that
   amounts exclude GST, state the unit (₹ lakh / ₹ crore) in every table header.
6. **Deck and memo:** copy the pptx/docx templates into `output/`, replace the `{{placeholders}}` with the
   briefing values (headline tiles, monthly chart from K01 Export_Rows, runway chart from K02 Weekly,
   what changed, risks, ask). Add Tamil labels if the audience prefers (number-and-language.md).
7. If the audience wants the model itself, deliver the W06 workbook alongside.

## Common mistakes
Leading with a table instead of the takeaway. Presenting a cash trough without the recommended action.
Mixing lakh and crore. Quoting EBITDA as profit when D&A or finance costs matter.

## Outputs
`output/<date>-board-briefing.md`, `output/<date>-board-deck.pptx`, optionally `output/<date>-board-memo.docx`.

## Human check
CFO signs off the narrative and the ask before anything is sent. Sending an email/message is a separate,
explicit user instruction.
