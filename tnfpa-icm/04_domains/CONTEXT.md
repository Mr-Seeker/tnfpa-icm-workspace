# 04_domains — the 29 enterprise domains (factory)

**Job:** extend the openfpa kernel to every system and discipline a finance function touches, without code. Each `Dnn_` folder has a contract (`CONTEXT.md`), a no-code template (workbook with `Checks`, plus playbooks for the judgement domains) and the exact kernel drivers it feeds. Domains never replace the kernel's accounting identities — they produce **driver evidence** (K01/K02 inputs, intake facts, corrections) that goes through the normal gates.

**How to use a domain:** copy `_templates/domain-record/` and the domain template into `companies/<slug>/domains/Dnn_<slug>/`, fill the pale-yellow cells, recalculate, confirm Checks = PASS, set `status: reviewed`, then transfer the ToKernel / summary values into the K01/K02 copy named in the contract (record the transfer in the domain `notes.md`). The full feed map is `domain-kernel-matrix.csv`.

| # | Domain | Folder | Feeds | Used in |
|---|---|---|---|---|
| 1 | Enterprise performance management & planning | `D01_epm-planning/` | K01 channels[i].cogs_pct; K01 channels[i].annual_revenue; W04 variance narrative | W02, W04, W07 |
| 2 | ERP & core accounting systems | `D02_erp-core-accounting/` | memory/mappings/registry.csv; K03 Reconcile; K01 opening_balances.* | W03, W02 |
| 3 | Statutory & regulatory reporting engines | `D03_statutory-regulatory-reporting/` | W07 board pack (statutory view); 01_tamil-nadu/statutory-calendar.csv; D10 evidence register | W04, W07 |
| 4 | HRIS & workforce management systems | `D04_hris-workforce-management/` | K01 opex fixed 'Payroll & benefits' monthly_amount; K02 salary, PF (15th), ESI (15th) flows; D16 gratuity valuation | W02, W05 |
| 5 | Human capital & business partnering | `D05_human-capital-business-partnering/` | K01 opex payroll (growth assumptions); D26 calibration log; W04 narrative | W04, W07 |
| 6 | Incentive compensation management & sales performance management | `D06_incentive-comp-sales-performance/` | K01 opex variable 'Sales incentives' pct_of_revenue; K02 quarterly payout flows | W02, W04, W05 |
| 7 | Customer relationship management systems | `D07_crm-customer-relationship/` | K01 channels revenue (sanity check); K02 receipts by week; K01 working_capital.dso_days | W03, W05 |
| 8 | Workflow & budget collaboration orchestration systems | `D08_workflow-budget-collaboration/` | W10 Gate 2 approvals; D09 capex approvals; W01 planning_cadence | W04, W07, W10 |
| 9 | Strategic portfolio & capital allocation systems | `D09_strategic-portfolio-capital-allocation/` | D17 CapexPlan → K01 capex_monthly, da_monthly; D23 green finance; W07 the ask | W02, W07 |
| 10 | Document management, audit & policy repositories | `D10_document-audit-policy/` | memory/sources/evidence/; D28 governance scorecard; doctor checklist | all |
| 11 | FinOps & cloud optimisation systems | `D11_finops-cloud-optimisation/` | K01 opex fixed 'Cloud & software' monthly_amount; D24 GST (RCM on imported services); D13 unit economics | W02, W04 |
| 12 | Spend management & strategic procurement | `D12_spend-procurement/` | K01 working_capital.dpo_days; K02 supplier payment flows; D24 tax (43B(h) disallowance) | W02, W05 |
| 13 | Revenue operations & pricing optimisation | `D13_revenue-operations-pricing/` | K01 channels growth_rate / cogs_pct; W04 variance drivers; K06 SKU economics | W04, W07, W12 |
| 14 | Macroeconomic & market intelligence systems | `D14_macroeconomic-market-intelligence/` | K01 debt[ALL].annual_rate; K01 opex escalation; K01 seasonality / growth; W08 corrections (context) | W02, W04, W10 |
| 15 | Risk & treasury management systems | `D15_risk-treasury/` | K01 debt slots (CC/OD as loc, term loans); K02 stress (D27); W07 covenant headroom | W05, W07 |
| 16 | Actuarial & insurance / risk modelling engines | `D16_actuarial-insurance-risk/` | K01 opex payroll benefits; K02 gratuity payouts on exit; D27 crisis scenarios | W02, W05 |
| 17 | Capex & asset lifecycle management systems | `D17_capex-asset-lifecycle/` | K01 capex_monthly; K01 da_monthly; D24 deferred tax view | W02, W04 |
| 18 | Real estate & facilities optimisation / IWMS / proptech | `D18_real-estate-facilities-iwms-proptech/` | K01 opex fixed 'Rent & facilities'; K02 monthly rent flows; D03 Ind AS 116 disclosures | W02, W05 |
| 19 | Investor relations & shareholder intelligence platforms | `D19_investor-relations-shareholder-intelligence/` | W07 investor update; K01 champion; D28 governance | W07 |
| 20 | Corporate development systems | `D20_corporate-development/` | D21 M&A valuation; D09 capital allocation; W01 cfo_priorities | W01, W07 |
| 21 | M&A systems | `D21_mergers-acquisitions/` | K01 copy of target; K08 divestiture; D22 cap table | W07, W10 |
| 22 | Cap table management systems | `D22_cap-table-management/` | D21 accretion/dilution; D19 shareholding; K01 opening cash | W07 |
| 23 | ESG & sustainability accounting / green finance platforms | `D23_esg-sustainability-green-finance/` | K01 opex (energy costs); D09 projects (solar/efficiency); D19 BRSR disclosures | W02, W07 |
| 24 | Specialised tax & transfer pricing engines | `D24_tax-transfer-pricing/` | K02 GST (20th), TDS (7th), advance tax (15th) disbursements; K01 tax_rate; D21/D03 | W05, W02 |
| 25 | Executive & boardroom negotiation psychology | `D25_boardroom-negotiation-psychology/` | K01 debt rate / terms after a bank negotiation; D12 supplier terms → DPO; D26 calibration log | W05, W07 |
| 26 | Qualitative strategic intuition and judgement | `D26_strategic-intuition-judgement/` | W08 context corrections; W10 hypotheses; W00 reflexes | W01, W09, W10 |
| 27 | Ad-hoc crisis improvisation | `D27_crisis-improvisation/` | K02 baseline weekly cash; D15 risk register; W08 context corrections | W05, W07 |
| 28 | Ethical oversight & governance culture | `D28_ethics-governance-culture/` | D10 evidence register; W10 Gate 2; K01 opex | W04, W07, W10 |
| 29 | Informal corporate intelligence networks | `D29_informal-intelligence-networks/` | memory/intake.csv (evidence); W08 context corrections; D14 macro register | W01, W08, W00 |

Domains 25–29 (negotiation, judgement, crisis, ethics, informal intelligence) are qualitative disciplines made deterministic with structured records, explicit scoring rules and playbooks — the agent prepares and records; humans decide.
