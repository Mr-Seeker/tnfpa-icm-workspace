# Crisis playbooks (first 72 hours)

Every playbook: **(1)** safety first; **(2)** name a crisis lead and a single numbers owner; **(3)** freeze
non-essential payments; **(4)** run D27 stress on the latest K02 baseline; **(5)** call the bank RM before
the trough week; **(6)** log every decision in `crisis-log.csv`; **(7)** communicate facts, next update time.

| Scenario | Specific actions | Cash levers |
|---|---|---|
| Cyclone / flood (Chennai, delta, coast) | staff safety, move stock above flood line, photograph damage for insurer (D16), notify insurer within policy time | BI claim, deferral of non-critical vendors with consent, CC limit ad-hoc |
| Grid outage / power cuts | DG fuel stock, shift planning, TNPDCL liaison | diesel cost spike in K02 |
| GST portal outage at filing | evidence screenshots, follow notified extensions only | keep GST cash ready regardless |
| Bank account freeze / fraud | inform bank and police (cybercrime), switch collections to alternate account, inform customers in writing | alternate banking lines |
| Key customer / dealer default | stop supplies, invoke security, legal notice, ECGC/insurance where present | collections re-forecast, factoring/TReDS for other receivables |
| Labour unrest | talks via the right channels, compliance check (wages, PF/ESI), no retaliation | overtime/contract labour cost |
| Key person loss | delegate authority per DoA, access recovery through IT | — |
| Cyber attack / ransomware | isolate, restore from backup, inform CERT-In as required | recovery spend |

`crisis-log.csv` columns: `timestamp,decision,data_used,owner,expected_effect,review_at,outcome`.
