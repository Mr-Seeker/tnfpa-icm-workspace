# Guardrails (always on)

## Human control at consequential boundaries
1. **External access** — ask before reading any live system: Tally/Zoho/SAP/NetSuite, bank portals,
   GST portal (GSTN), income-tax e-filing, TRACES, EPFO/ESIC, MCA21, MCP servers, email. Prefer files the
   user supplies or exports they make.
2. **Gate 1 — architecture approval** before generating any model, connector, skill or agent.
3. **Gate 2 — champion promotion** only with a named human approver and date (K05 Promotion sheet).
4. **Corrections** — echo your interpretation back once; set `status: applied` only after the human confirms.
5. **Generated skills/agents** — propose each with the profile facts that justify it; write only after approval.

## No hidden gaps
6. Missing, duplicate, conflicting and unmapped data fail visibly (K03). Never fill with defaults.
7. Never treat missing or zero actuals as perfect forecast performance (K04 refuses to score them).
8. Never overwrite source data, correction history, forecast snapshots, experiments or epochs. Supersede
   by adding a new file and changing the old one's `status`; keep the old file.
9. A workbook with any FAIL on its `Checks` sheet is not evidence. Fix the inputs or the structure —
   never edit a formula cell to force a pass, and never loosen a tolerance to make a check pass.

## Evidence before promotion
10. No evidence, no experiment. No holdout, no promotion. Never score on periods used to fit.
11. A parametric change must improve **holdout** fitness, not in-sample fit; cap any driver move at ±25%
    per cycle (K04 Learning_Guards); a structural change needs a persistent same-signed miss (K ≥ 2 closes)
    that survived the one-time-item screen — or a human-authored structural correction.
12. Hard accounting and reconciliation checks override metric improvement. Complexity is a cost.

## Numbers you report
13. Do not hand-calculate a figure you will report: read it from a recalculated workbook.
14. Apply `03_workflows/W00_cfo-judgment/` before any conclusion (pre-close months, flash vs GL cash,
    intercompany, D&A, impairments, raw cash, one-offs, GST-inclusive vs exclusive, lakh/crore units).
15. Every statutory rate or date you rely on must be checked against `01_tamil-nadu/verification-register.md`
    and, when it changes, recorded there with the source and date.

## Privacy and safety
16. Never store credentials, passwords, OTPs, PAN/Aadhaar of individuals, bank account numbers or full
    salary-by-name in this workspace. Payroll records use employee ids; fixtures are redacted.
17. Informal intelligence (D29) is limited to public or lawfully shared information. No insider
    information (SEBI PIT Regulations), no confidential competitor data, no pretexting.
18. Keep data local. Cross-client learning (W11) shares only ratified, abstracted priors — never raw client data.
