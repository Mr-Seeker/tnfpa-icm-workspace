# D11 · FinOps & cloud optimisation systems

**Job:** Make cloud and SaaS spend visible in rupees, including reverse-charge GST leakage, commitment coverage and unit cost, and feed it to K01 opex.

## Systems of record (Tamil Nadu / India)
AWS Cost Explorer, Azure Cost Management (South India region = Chennai), GCP billing, Zoho/Microsoft 365/Google Workspace admin billing exports.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D11_finops-cloud-optimisation/` | `D11_finops-cloud-optimisation.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D11_finops-cloud-optimisation.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D11_finops-cloud-optimisation/`.
2. Replace the sample rows with the company's data (sheets: Setup (USD/INR dated, RCM rate, leakage share, units), CloudCosts (service, provider, region, currency, amount → INR, RCM leakage, all-in), Unit). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 opex fixed 'Cloud & software' monthly_amount | Unit B4 |
| D24 GST (RCM on imported services) | RCM |
| D13 unit economics | cost per unit |

## Tamil Nadu notes
- Imported services from foreign cloud providers attract IGST under reverse charge for B2B; claim ITC where eligible.
- Use the FBIL/RBI reference rate on the invoice date for conversion; record the date (D14).

## Used in workflows
W02, W04

## Human check
IT head confirms allocations; CFO approves commitments (D08).
