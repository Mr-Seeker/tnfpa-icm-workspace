# D18 · Real estate & facilities optimisation / IWMS / proptech

**Job:** Lease register with Ind AS 116 liability and right-of-use view, space utilisation and cost per used seat/sq ft, and cash rent for K01/K02.

## Systems of record (Tamil Nadu / India)
Facilio (Chennai), IWMS (Planon, Archibus), Excel lease registers, landlord agreements.

## Inputs
| Working (this company) | Reference |
|---|---|
| exports / registers from the systems above; `companies/<slug>/domains/D18_real-estate-facilities-iwms-proptech/` | `D18_real-estate-facilities-iwms-proptech.xlsx` (template); `01_tamil-nadu/` |

## Process
1. Copy `D18_real-estate-facilities-iwms-proptech.xlsx` and `_templates/domain-record/notes.md` into `companies/<slug>/domains/D18_real-estate-facilities-iwms-proptech/`.
2. Replace the sample rows with the company's data (sheets: Leases (rent, escalation, term, IBR, deposit, TN registration → liability, interest, ROU depreciation, utilisation, rent per used unit), ToKernel). Type only into pale-yellow cells.
3. Recalculate; `Checks` OVERALL must be PASS. Verify any statutory rate against `01_tamil-nadu/verification-register.md`.
4. Apply W00 judgment; set `notes.md` status to `reviewed` after the owner confirms.
5. Transfer the feed values below into the company's K01/K02 copy or memory file and log the transfer in `notes.md`.

## Feeds the kernel
| Target | From |
|---|---|
| K01 opex fixed 'Rent & facilities' | ToKernel B4 |
| K02 monthly rent flows | Leases |
| D03 Ind AS 116 disclosures | lease liability |

## Tamil Nadu notes
- Tenancies in TN should be registered with the Rent Authority under the TN Regulation of Rights and Responsibilities of Landlords and Tenants Act 2017.
- Micro-markets: Chennai OMR/Guindy/Ambattur offices; Oragadam–Sriperumbudur and Hosur SIPCOT industrial; Coimbatore Avinashi Road.

## Used in workflows
W02, W05

## Human check
Admin head confirms lease terms; CFO approves renewals per DoA.
