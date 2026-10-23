# Third-party notices

This repository is licensed under the Apache License 2.0 (see [LICENSE](LICENSE) and [NOTICE](NOTICE)).
It also contains material from the projects below, which keep their own licences.

## openfpa

- **Source:** [github.com/JeffBrines/openfpa](https://github.com/JeffBrines/openfpa)
- **Licence:** MIT, Copyright (c) 2026 Guiderail (full text below)
- **Used for:** the FP&A method this workspace rebuilds without code, its reference outputs, and the example data listed below. The mapping of every openfpa file to its replacement is in [`tnfpa-icm/00_system/coverage/openfpa-coverage-map.csv`](tnfpa-icm/00_system/coverage/openfpa-coverage-map.csv).

**Files copied unchanged from openfpa** (paths under `tnfpa-icm/`):

- `examples/foxfactory-public-proof/data/raw/SOURCES.md`
- `examples/foxfactory-public-proof/data/raw/balance_sheet.csv`
- `examples/foxfactory-public-proof/data/raw/cash_flow.csv`
- `examples/foxfactory-public-proof/data/raw/income_statement.csv`
- `examples/foxfactory-public-proof/data/raw/quarterly.csv`
- `examples/foxfactory-public-proof/data/raw/segments.csv`
- `examples/foxfactory-public-proof/memory/business-profile.md`
- `examples/foxfactory-public-proof/memory/decisions/initial-model-architecture.md`
- `examples/foxfactory-public-proof/output/divestiture.md`
- `examples/foxfactory-public-proof/output/forecast-briefing.md`
- `examples/foxfactory-public-proof/output/historical-holdout.md`
- `examples/foxfactory-public-proof/output/reconciliation.md`
- `examples/ridgeline-parity/data/fixtures/netsuite_pl.csv`
- `examples/ridgeline-parity/data/fixtures/quickbooks_pl.csv`
- `examples/ridgeline-parity/data/fixtures/shopify_summary.csv`
- `examples/ridgeline-parity/data/quickbooks_pl_sample.csv`
- `examples/ridgeline-parity/output/briefing.md`

**Files adapted from openfpa** (paths under `tnfpa-icm/`):

- `examples/foxfactory-public-proof/memory/research/epochs/foxf-fy2025-001-broad-mean-reversion.md`
- `examples/foxfactory-public-proof/memory/research/epochs/foxf-fy2025-002-slow-margin-recovery.md`
- `examples/foxfactory-public-proof/memory/research/objective.md`

The Fox Factory figures in those files come from public SEC filings by Fox Factory Holding Corp., as recorded in `SOURCES.md`.

### openfpa licence

```text
MIT License

Copyright (c) 2026 Guiderail

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Interpretable Context Methodology (ICM)

- **Source:** Jake Van Clief and David McDermott, *Interpretable Context Methodology: Folder Structure as Agent Architecture*, [arXiv:2603.16021](https://arxiv.org/abs/2603.16021). Reference implementation: [github.com/RinDig/Interpretable-Context-Methodology](https://github.com/RinDig/Interpretable-Context-Methodology).
- **Licence:** MIT (Copyright (c) 2026 Model Workspace Protocol Contributors)
- **Used for:** the folder-as-architecture structure of this workspace. The method is followed; no ICM files are copied into this repository, so no ICM licence text is reproduced here.
