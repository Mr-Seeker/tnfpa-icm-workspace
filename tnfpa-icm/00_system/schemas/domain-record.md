# Domain record

**Folder:** `domains/Dnn_<slug>/` inside a company. Contains a copy of the domain template workbook or
CSV from `04_domains/Dnn_<slug>/`, plus `notes.md` with frontmatter `domain, owner, refreshed_at,
feeds (list of K01/K02 paths or intake keys), status (draft|reviewed|in-use)`. A domain record feeds the
kernel only when its workbook's `Checks` = PASS and `status: reviewed` or `in-use`.
