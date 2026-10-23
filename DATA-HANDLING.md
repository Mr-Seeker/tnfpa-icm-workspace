# Data handling

A one-page summary for finance, IT and security reviewers. Every point below restates rules in the [User Manual](README.md); where they differ, the files in `tnfpa-icm/00_system/` govern.

## Where data lives

- The workspace is plain files: folders, markdown, CSV registries and `.xlsx` workbooks.
- Each company's data and outputs sit in its own folder, `tnfpa-icm/companies/<company>/`, on the machine or drive where you open the workspace. Companies never share state except through ratified priors in `portfolio/library/`.
- The workspace contains no scripts, macros, add-ins, packages or containers.

## What the AI agent can read

- Files you place in the workspace or point it to.
- It must ask before reading any live system: Tally, Zoho, SAP, NetSuite, bank portals, the GST portal, income-tax e-filing, TRACES, EPFO/ESIC, MCA21, MCP servers and email.
- It never writes or runs code. Calculations happen in spreadsheet formulas you can inspect.

## What the agent can do on its own, and what needs you

| The agent can | Only with your approval |
| --- | --- |
| Inspect files, ask questions, fill workbooks, write memory files and reports | Approve the model architecture (Gate 1, with a named approver and date) |
| Propose forecast changes within set limits | Promote a new champion forecast model (Gate 2, with a named approver and date) |
| Prepare a draft message from the templates | Send any email or message |
| Propose a generated skill or agent | Write that skill or agent into the workspace |
| Work from files you supplied | Any external access, including any live system |

## Your AI provider

The agent sends the content it reads to its model provider for processing. Retention and training terms are set by your organisation's agreement with that provider. Choose a provider and plan that meet your data policy before you load company data.

## Example data

The example companies use synthetic or public data. Kaveri Chairs is fictional; Fox Factory uses public SEC filings; Ridgeline is openfpa's synthetic company.

## Questions

Open an issue at [github.com/Mr-Seeker/tnfpa-icm-workspace/issues](https://github.com/Mr-Seeker/tnfpa-icm-workspace/issues).
