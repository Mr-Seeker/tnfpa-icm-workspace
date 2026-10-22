# Memory index (replaces `.fpa/index.yaml`)

**File:** `memory/index.csv` — header `path,category,title,keywords`. Derived and rebuildable; never the
source of truth. One row per `.md`, `.csv` or `.yaml` file under `memory/` except `index.csv` and
`context-pack.md`. `path` is relative to `memory/`; `category` = first folder (or the file stem for
top-level files); `title` = first `# ` heading, else the stem in Title Case; `keywords` = unique lowercase
words (`[a-z0-9][a-z0-9_-]+`) from the path, title, headings and frontmatter values, space-separated.
