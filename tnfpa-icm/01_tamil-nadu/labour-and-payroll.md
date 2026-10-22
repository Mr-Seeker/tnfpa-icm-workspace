# Labour and payroll (Tamil Nadu employers)

**Labour Codes:** the Code on Wages 2019, Industrial Relations Code 2020, Social Security Code 2020 and
OSH Code 2020 were brought into force nationally in November 2025, consolidating the earlier Acts named
below. State rules (Tamil Nadu) and transition notifications determine the exact obligations — verify.
Key effect for models: the **wage definition** (basic + DA + retaining allowance must be at least 50%
of total remuneration) drives PF, gratuity and bonus bases. D04 uses "basic % of gross" for this.

| Item | Rule used by D04 (verify) | Cash timing (K02) |
|---|---|---|
| EPF (employer) | 12% of PF wage (3.67% EPF + 8.33% EPS, EPS on wage capped at ₹15,000); many employers cap total at ₹15,000 wage | 15th of next month |
| EPF (employee) | 12% of PF wage, deducted from salary | 15th (remitted with employer share) |
| EDLI + admin | ≈1% of PF wage (EDLI 0.5% + admin 0.5%) | 15th |
| ESI | employer 3.25%, employee 0.75% of gross for employees earning up to ₹21,000/month in notified areas | 15th |
| Gratuity | 15/26 × last monthly basic+DA × completed years (≥ 5 years; fixed-term rules differ), ceiling ₹20 lakh; accrue ≈ 4.81% of basic; value per Ind AS 19 / AS 15 (D16) | on exit |
| Statutory bonus | 8.33% (min) – 20% (max) of capped wage for employees earning up to ₹21,000/month | within 8 months of FY end; usually paid before Deepavali (Oct/Nov) |
| TN professional tax | half-yearly slabs by local body, max ₹2,500/yr | half-yearly |
| TN Labour Welfare Fund | small fixed annual employer + employee amounts | 31 January |
| Leave encashment | per policy; actuarial liability (D16) | on encashment/exit |
| Minimum wages | Tamil Nadu notifies scheduled-employment minimum wages + VDA (revised half-yearly) | — |
| Overtime | twice the ordinary rate (Factories Act / OSH Code) | with payroll |

**Workforce realities to ask about (W01 intake › payroll_statutory):** contract labour share (CLRA
compliance, principal-employer liability for PF/ESI), migrant workers in Tiruppur/Coimbatore/Hosur
clusters, women in night shifts (permitted with safeguards), festival advances, canteen and transport
costs, apprentices under NAPS, and the Naan Mudhalvan / TNSDC skilling pipeline for hiring plans.

**Privacy:** never store salary-by-name. Use employee ids; aggregate before memory.
