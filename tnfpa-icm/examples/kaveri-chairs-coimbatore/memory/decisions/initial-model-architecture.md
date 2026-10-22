# Initial Model Architecture Proposal

**Status:** Approved. Approved by: S. Meenakshi (CFO) and R. Senthil (MD), 2026-03-22.

## Objective

A monthly FY2026-27 budget and rolling latest estimate in K01 (four channels, five opex lines, cash credit as a LOC and the TIIC term loan), a 13-week cash forecast in K02 with dated GST/TDS/PF/ESI/advance-tax flows, and a ₹ lakh MIS and board pack.

## Known Facts

- See `memory/business-profile.md` (16 facts, all confirmed or ≥ 85% confidence).

## Remaining Unknowns

- No architecture-critical unknowns remain.

## Proposed Connectors

- tally-pl-monthly: Tally Prime P&L export (Dr/Cr), normalised to Account,Amount, fixture-validated
- bank-flash-weekly: Indian Bank statement export for K02 opening cash (flash basis)

## Proposed Model Components

- K01 champion: Dealer, Online, D2C, Institutional channels; payroll from D04; rent from D18; marketing and freight variable
- K02 13-week cash with D07 collections, D12 MSME supplier payments, D24 GST/TDS/advance tax
- D17 capex plan for the CNC router; D15 covenant tests

## Proposed Generated Skills

- sku-profitability (dealer vs marketplace SKU economics) — K06
- dealer-scheme-accrual-and-credit — D06/D07 templates

## Risks And Judgment Areas

- Festival pull-forward (Deepavali, Pongal); cyclone/monsoon one-offs; marketplace commission inside online COGS; GST-inclusive receipts vs ex-GST model

## Validation Checks

- K03 reconciliation of the Tally P&L (no duplicates, no unmapped ledgers)
- K01 and K02 Checks = PASS; base-year revenue ties to Tally within 1%

## Decision

- [x] Approved to scaffold
- [ ] Revise proposal
- [ ] Stop after business profile
