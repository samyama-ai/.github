## Samyama — Graph-Vector Database & Systems Research

We build [**Samyama Graph**](https://github.com/samyama-ai/samyama-graph) — an open-source
graph-vector database in Rust that queried **1 billion edges for $2.50** (74M nodes, single
machine). OpenCypher, RESP, vector search, 14 graph algorithms
([read the paper, arXiv:2603.08036](https://arxiv.org/abs/2603.08036)). Alongside it we run a
daily **DBMS systems-research program** — small, reproducible, pre-registered papers on the
database problems we hit while building it.

### What we proved

We loaded the entire PubMed corpus (every article since 1966), ClinicalTrials.gov, Reactome
pathways, and DrugBank into one graph. Then asked:

> *"What drugs are most tested in cancer clinical trials?"*

**Answer**: Pembrolizumab (137 trials), followed by Carboplatin (106) and Paclitaxel (106).
**5.2 seconds.** One query spanning four databases.

[96 of 100 benchmark queries pass →](https://samyama-ai.github.io/samyama-graph-book/biomedical_benchmark.html)

### Papers

Nine arXiv preprints — reproducible, pre-registered, code + data with each. Honest baselines,
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

Also: [**dbms_research**](https://github.com/samyama-ai/dbms_research) — a catalog of 1000+ open
DBMS problems with formal statements, bounds, and 6,700+ link-checked references. Preprints in
progress: [clinical-llm-graphrag](https://github.com/samyama-ai/clinical-llm-graphrag),
[bandwidth-bound-scan](https://github.com/samyama-ai/bandwidth-bound-scan).

### Engine & tooling

| Repository | What | Notes |
|---|---|---|
| [**samyama-graph**](https://github.com/samyama-ai/samyama-graph) | Graph-vector database (Rust, OpenCypher, RESP, vector search) | 1933 tests, Apache 2.0 |
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
| [**cricket-kg**](https://github.com/samyama-ai/cricket-kg) | Cricket matches (Cricsheet) | 36K nodes, 1.4M edges |
| [**assetops-kg**](https://github.com/samyama-ai/assetops-kg) | Industrial operations (IBM AssetOpsBench) | 12.6K nodes, 12.6K edges |

### Quick start

```bash
git clone https://github.com/samyama-ai/samyama-graph && cd samyama-graph
cargo build --release
./target/release/samyama
# RESP on :6379, HTTP on :8080
```

**Website**: [samyama.dev](https://samyama.dev) · **Book**: [samyama-ai.github.io/samyama-graph-book](https://samyama-ai.github.io/samyama-graph-book/) · **Contact**: [samyama.dev/contact](https://samyama.dev/contact)
