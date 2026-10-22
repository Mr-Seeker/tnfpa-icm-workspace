# Numbers and language

## Indian digit grouping and units
- Group as 12,34,56,789 (lakh = 1,00,000 = 10⁵; crore = 1,00,00,000 = 10⁷). Board packs usually state
  "₹ in lakh" or "₹ in crore" in the header and show 2 decimals.
- Spreadsheet number format for Indian grouping (whole rupees):
  `[>=10000000]##\,##\,##\,##0;[>=100000]##\,##\,##0;##,##0` (negatives: wrap with a sign in text).
- K01 › Assumptions has `number_style` (indian/western), `currency_symbol` (₹), `display_divisor`
  (1 / 1,000 / 1,00,000 / 1,00,00,000) and `display_unit` for reports.
- Files keep full rupees without separators; only reports format.
- Write "₹" (U+20B9). In plain text "Rs." is acceptable; never "INR" mixed with "₹" in one table.

## Bilingual board labels (Tamil / English)
Use English as the primary language for statutory and board documents; add Tamil labels when the
audience prefers it (family-owned businesses, regional banks, employees).

| English | Tamil |
|---|---|
| Revenue / Sales | வருவாய் / விற்பனை |
| Gross profit | மொத்த லாபம் |
| EBITDA | வட்டி, வரி, தேய்மானத்திற்கு முந்தைய லாபம் (EBITDA) |
| Net profit | நிகர லாபம் |
| Cash / Ending cash | ரொக்கம் / இறுதி ரொக்க இருப்பு |
| Working capital | நடைமுறை மூலதனம் |
| Receivables | வரவேண்டிய தொகை |
| Payables | செலுத்த வேண்டிய தொகை |
| Inventory / Stock | சரக்கு இருப்பு |
| Forecast | முன்கணிப்பு |
| Budget | வரவு செலவுத் திட்டம் |
| Variance | மாறுபாடு |
| Cash credit limit | ரொக்கக் கடன் வரம்பு |
| Risk | அபாயம் |
| Board meeting | இயக்குநர் குழுக் கூட்டம் |
| Approved | அங்கீகரிக்கப்பட்டது |

Have a fluent reviewer check Tamil text before it goes to a board or bank.
