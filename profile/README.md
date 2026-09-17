## Samyama — Graph-Vector Database & Systems Research

We build [**Samyama Graph**](https://github.com/samyama-ai/samyama-graph) — an open-source
graph-vector database in Rust. OpenCypher, RESP, HTTP, vector search, graph algorithms
([read the paper, arXiv:2603.08036](https://arxiv.org/abs/2603.08036)). Alongside it we run a
daily **DBMS systems-research program** — small, reproducible, pre-registered papers on the
database problems we hit while building it.

**What is measured, and re-measured on a schedule** (v1.8.0, 2026-09):

| | |
|---|---|
| openCypher TCK | **3,845 of 3,847 evaluated scenarios pass**, at 98.7% coverage of the 3,897-scenario corpus. Neo4j 5 scores 79.5% on the same corpus and comparator. |
| LDBC SNB | Interactive **21/21** and BI **20/20** complete at SF1, no timeouts; Graphalytics 12/12 agrees with the LDBC reference answers |
| Memory | **200 resident bytes per edge** on SNB SF10 (176M edges) |
| Scale | 74M nodes and 1B edges loaded on a single machine |
| Transactions | BEGIN/COMMIT/ROLLBACK over RESP and HTTP, with a published anomaly table |

Every number above comes from a suite that writes a result envelope, and a regression gate
blocks the release tag when a verdict is red or stale. Where something is unmeasured, the
scorecard says so rather than leaving a gap.

### What we proved

We loaded the entire PubMed corpus (every article since 1966), ClinicalTrials.gov, Reactome
pathways, and DrugBank into one graph. Then asked:

> *"What drugs are most tested in cancer clinical trials?"*

**Answer**: Pembrolizumab (137 trials), followed by Carboplatin (106) and Paclitaxel (106).
**5.2 seconds.** One query spanning four databases.

[96 of 100 benchmark queries pass →](https://samyama-ai.github.io/samyama-graph-book/biomedical_benchmark.html)

### Papers

Eleven arXiv preprints — the industrial asset-operations paper is accepted at the
Agents+Graph workshop @ VLDB 2026 — reproducible, pre-registered, code + data with each. Honest baselines,
not SOTA claims.

| Paper | arXiv | Code |
|---|---|---|
| Samyama: A Unified Graph-Vector Database with In-Database Optimization, Agentic Enrichment, and Hardware Acceleration | [2603.08036](https://arxiv.org/abs/2603.08036) | [samyama-graph](https://github.com/samyama-ai/samyama-graph) |
| Open Biomedical Knowledge Graphs at Scale: Construction, Federation, and AI Agent Access | [2603.15080](https://arxiv.org/abs/2603.15080) | [biomedqa](https://github.com/samyama-ai/biomedqa) |
| Graph-Grounded Optimization: Rao-Family Metaheuristics, Classical OR, and SLM-Driven Formulation over KGs | [2605.12204](https://arxiv.org/abs/2605.12204) | [optimization_algorithms](https://github.com/samyama-ai/optimization_algorithms) |
| Knowledge Graphs as the Missing Data Layer for LLM-Based Industrial Asset Operations | [2605.26874](https://arxiv.org/abs/2605.26874) | [assetops-kg](https://github.com/samyama-ai/assetops-kg) |
| When Does q-error Predict Plan Regret? Three Regimes of Cardinality-Estimation Error | [2606.15600](https://arxiv.org/abs/2606.15600) | [ce-metric-eval](https://github.com/samyama-ai/ce-metric-eval) |
| Filtered ANN as a Phase Transition: When Selectivity-Estimation Error Causes Plan Regret | [2606.16341](https://arxiv.org/abs/2606.16341) | [filtered-ann-regret](https://github.com/samyama-ai/filtered-ann-regret) |
| The Value of Adaptivity in LSM Bloom-Filter Tuning: A Log-Law and a Two-Clock Frontier | [2606.18138](https://arxiv.org/abs/2606.18138) | [lsm-bloom-allocation](https://github.com/samyama-ai/lsm-bloom-allocation) |
| Group Commit Self-Clocks: Why Tuning Is Unnecessary Above a Device-Set Load Threshold | [2606.18187](https://arxiv.org/abs/2606.18187) | [group-commit-policy](https://github.com/samyama-ai/group-commit-policy) |
| Caching for Dollars, Not Hits: An Exact Offline Reference for Cloud-Egress Caching | [2606.20539](https://arxiv.org/abs/2606.20539) | [cloud-egress-cache](https://github.com/samyama-ai/cloud-egress-cache) |
| Removable and Irreducible: A Token-Cost Ledger for the Multilingual Tokenization Tax | [2609.00378](https://arxiv.org/abs/2609.00378) | [token-cost-ledger](https://github.com/samyama-ai/token-cost-ledger) |
| Bounded, Indeterminate, or a Bug: A Condition-Aware Oracle for Differential Testing of SQL Aggregates | [2609.00381](https://arxiv.org/abs/2609.00381) | [numeric-semantics-oracle](https://github.com/samyama-ai/numeric-semantics-oracle) |

Also: [**dbms_research**](https://github.com/samyama-ai/dbms_research) — a catalog of 1000+ open
DBMS problems with formal statements, bounds, and 6,700+ link-checked references. Preprints in
progress: [clinical-llm-graphrag](https://github.com/samyama-ai/clinical-llm-graphrag),
[bandwidth-bound-scan](https://github.com/samyama-ai/bandwidth-bound-scan).

### Engine & tooling

| Repository | What | Notes |
|---|---|---|
| [**samyama-graph**](https://github.com/samyama-ai/samyama-graph) | Graph-vector database (Rust, OpenCypher, RESP, HTTP, vector search) | v1.8.0 · 4,494 tests · Apache 2.0 · `ghcr.io/samyama-ai/samyama-graph` |
| [**graphrag-rs**](https://github.com/samyama-ai/graphrag-rs) | Turn any folder of docs into a queryable KG via MCP | Rust, MCP |
| [**samyama-graph-book**](https://github.com/samyama-ai/samyama-graph-book) | Architecture book + biomedical benchmark | [Read online](https://samyama-ai.github.io/samyama-graph-book/) |

### Knowledge graphs

| Repository | What | Scale |
|---|---|---|
| [**pubmed-kg**](https://github.com/samyama-ai/pubmed-kg) | PubMed/MEDLINE | 66.2M nodes, 1.04B edges |
| [**clinicaltrials-kg**](https://github.com/samyama-ai/clinicaltrials-kg) | ClinicalTrials.gov | 7.8M nodes, 27M edges |
| [**druginteractions-kg**](https://github.com/samyama-ai/druginteractions-kg) | DrugBank + ChEMBL + SIDER | 245K nodes, 388K edges |
| [**pathways-kg**](https://github.com/samyama-ai/pathways-kg) | Reactome biological pathways | 119K nodes, 835K edges |
| [**surveillance-kg**](https://github.com/samyama-ai/surveillance-kg) | WHO disease surveillance (GHO) | Public health |
| [**edge-ai-kg**](https://github.com/samyama-ai/edge-ai-kg) | Edge-AI deployment: boards, accelerators, ONNX kernels, quantized models | 25K nodes, 76K edges |
| [**imdb-kg**](https://github.com/samyama-ai/imdb-kg) | Movies, series, people (IMDB non-commercial) | 1.94M nodes, 2.63M edges |
| [**cricket-kg**](https://github.com/samyama-ai/cricket-kg) | Cricket matches (Cricsheet) | 36K nodes, 1.4M edges |
| [**football-kg**](https://github.com/samyama-ai/football-kg) | Tournaments, teams, players, goals (DataHub) | 16K nodes, 12K edges |
| [**assetops-kg**](https://github.com/samyama-ai/assetops-kg) | Industrial operations (IBM AssetOpsBench) | 12.6K nodes, 12.6K edges |
| [**bank-model-risk-kg**](https://github.com/samyama-ai/bank-model-risk-kg) | Model governance, lineage, regulation (synthetic) | Model risk |
| [**health-determinants-kg**](https://github.com/samyama-ai/health-determinants-kg) | World Bank WDI, WHO air quality, FAO, UNDP | Social determinants |
| [**health-systems-kg**](https://github.com/samyama-ai/health-systems-kg) | WHO SPAR and NHWA, Gavi, Global Fund, IHME | Health systems |
| [**mental-health-kg**](https://github.com/samyama-ai/mental-health-kg) | Mental-health indicators and services | Public health |
| [**regulatory-affairs-kg**](https://github.com/samyama-ai/regulatory-affairs-kg) | Regulatory submissions and requirements | Compliance |
| [**legal-judgments-graph-kg**](https://github.com/samyama-ai/legal-judgments-graph-kg) | Judgments, citations, courts | Legal |
| [**wildfire-evac-kg**](https://github.com/samyama-ai/wildfire-evac-kg) | Road network for evacuation modelling (OpenStreetMap) | Paradise, CA |
| [**edtech-kg**](https://github.com/samyama-ai/edtech-kg) | Curriculum, skills and learning paths | Education |

Most ship a prebuilt `.sgsnap` snapshot on the
[samyama-graph releases page](https://github.com/samyama-ai/samyama-graph/releases) — import one
and start querying in under a second, no ETL.

**Data licences are recorded, not assumed.** Each of these repositories is Apache 2.0 for its
*loader*; the data it reads carries its own terms. A `DATA-LICENSES.md` names every upstream
source, what its own terms page says, and the date we read it — and states where that leaves the
derived graph. Some of those answers are inconvenient and are written down anyway: the WHO-based
graphs are non-commercial and share-alike, and `druginteractions-kg` combines share-alike,
non-commercial and possibly non-redistributable sources, so we ship the loader rather than the
graph. Where a source could not be verified, the row says so instead of guessing.

**Newest — [edge-ai-kg](https://github.com/samyama-ai/edge-ai-kg)**: the question it answers is
*"which operators in my model have no kernel on this accelerator, and silently fall back to the
CPU?"* Built on three real public sources — the [ONNX](https://github.com/onnx/onnx) operator
catalog, [ONNX Runtime](https://github.com/microsoft/onnxruntime) kernel registrations across
CPU/CUDA/DirectML, and 73 measured [MLPerf Tiny v1.2](https://github.com/mlcommons/tiny_results_v1.2)
submissions — plus a generated hardware fleet for scale. Every node is stamped `real` or
`synthetic`, so the two are never conflated.

### Quick start

```bash
git clone https://github.com/samyama-ai/samyama-graph && cd samyama-graph
cargo build --release
./target/release/samyama
# RESP on :6379, HTTP on :8080
```

**Website**: [samyama.dev](https://samyama.dev) · **Book**: [samyama-ai.github.io/samyama-graph-book](https://samyama-ai.github.io/samyama-graph-book/) · **Contact**: [samyama.dev/contact](https://samyama.dev/contact)
