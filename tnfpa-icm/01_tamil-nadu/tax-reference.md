# Tax reference (verify every rate in `verification-register.md` before use)

## Goods and Services Tax (GST)
- **Structure:** intra-state supply inside Tamil Nadu → CGST + SGST (equal halves); inter-state supply
  and imports → IGST. Tamil Nadu's GST state code is **33** (GSTIN begins `33…`); Puducherry is 34.
- **Rates:** after the September 2025 rate rationalisation the main slabs are 5% and 18%, with a 40%
  rate for specified luxury / sin goods (and special rates such as 0.25%/3% for stones/precious metals).
  Record the actual HSN/SAC rate per product in D24 and in K01 notes — never assume.
- **Cash vs P&L:** GST is not revenue or cost for the model when input tax credit (ITC) is available.
  Model revenue and COGS **excluding GST**; model the **net GST cash payment** as a K02 disbursement
  (D24 GST sheet: output tax − eligible ITC per GSTR-2B + reverse-charge tax, which must be paid in cash).
  Blocked credits (s.17(5)) and ineligible ITC become cost — put them in COGS/opex.
- **Working-capital effect:** customers pay invoice value *including* GST; AR in the balance sheet is
  GST-inclusive while K01 AR = revenue × DSO/30 is GST-exclusive. If GST-inclusive AR matters for the
  CC/OD drawing-power calculation, scale DSO by (1 + weighted GST rate) in a company workbook and say so.
- **E-invoicing / e-way bills:** mandatory above notified turnover; e-way bills for movement of goods
  above the notified value. Affects cut-off evidence, not the model.
- **E-commerce:** marketplace operators collect GST TCS on net taxable supplies (rate notified; was cut to
  0.5% in 2024) and income-tax TDS u/s 194-O (0.1% from October 2024). Both are receivable credits —
  model the timing gap in K02 receipts.

## Income tax (company)
- **New law:** the Income-tax Act, 2025 replaces the 1961 Act from **1 April 2026** (tax year 2026-27).
  Section numbers below are the familiar 1961-Act references; map to the new sections with the CA.
- **Concessional regime (s.115BAA):** 22% + 10% surcharge + 4% cess = **25.168%** effective; no MAT,
  but most exemptions/incentives (incl. additional depreciation) are forgone. K01 default tax_rate.
- **Normal regime:** 25% (turnover ≤ ₹400 crore in the reference year) or 30%, plus surcharge (7% above
  ₹1 crore income, 12% above ₹10 crore) and 4% cess; MAT 15% of book profit applies.
- **K01 tax model:** tax = rate × positive pre-tax after consuming the opening unabsorbed-loss balance
  (`opening_balances.nol`). It does not create new carry-forward from in-period losses and does not model
  MAT, deferred tax or set-off restrictions — bridge those outside the engine (W00).
- **Advance tax:** cumulative 15% by 15 June, 45% by 15 September, 75% by 15 December, 100% by 15 March
  (D24 AdvanceTax → K02 flows). Interest applies on shortfalls.
- **Depreciation for tax:** WDV block rates (e.g. plant & machinery 15%, computers 40%, buildings 10%,
  furniture 10%); half rate when put to use for < 180 days in the year (D17).
- **MSME payments (s.43B(h)):** amounts due to micro/small enterprises (Udyam-registered) are deductible
  only when paid within the MSMED Act limit (agreed term, max 45 days). Unpaid at year-end → disallowed (D12).
- **TDS sections commonly met:** 192 salary, 194C contractors (1%/2%), 194J professional/technical
  (10% / 2%), 194I rent (10% land/building, 2% plant), 194H commission, 194Q purchase of goods above
  ₹50 lakh (0.1%), 194-O e-commerce. Deposit by the 7th (March: 30 April) → K02.

## Transfer pricing
- International and specified domestic transactions must be at arm's length (methods CUP, RPM, CPM,
  PSM, TNMM, other). With 6+ comparables the arm's-length **range** is the 35th–65th percentile
  (data-point rule, implemented in D24 › TPRange); otherwise the arithmetic mean with the notified
  tolerance band. Accountant's report and master-file obligations apply above thresholds.

## Tamil Nadu state-level items
- **Professional tax:** levied by local bodies (e.g. Greater Chennai Corporation) half-yearly on
  employees' half-yearly income slabs; capped by the Constitution at ₹2,500 per person per year.
- **Labour Welfare Fund:** annual employer + employee contribution, due 31 January.
- **Stamp duty & registration:** conveyance, lease, mortgage and share-transfer instruments attract TN
  stamp duty and registration fees (rates by instrument; check the Registration Department schedule).
- **Electricity:** TN tariffs are revised by TNERC; distribution is by TNPDCL (successor to TANGEDCO's
  distribution business). Electricity tax/charges flow into D23 (energy) and K01 opex.
