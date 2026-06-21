## Samyama — Graph-Vector Database & Systems Research

We build [**Samyama Graph**](https://github.com/samyama-ai/samyama-graph) — an open-source
graph-vector database in Rust that queried **1 billion edges for $2.50** (74M nodes, single
machine). OpenCypher, RESP, vector search, 14 graph algorithms. Alongside it we run a daily
**DBMS systems-research program** — small, reproducible, pre-registered papers on the
database problems we hit while building it.

### What we proved

We loaded the entire PubMed corpus (every article since 1966), ClinicalTrials.gov, Reactome
pathways, and DrugBank into one graph. Then asked:

> *"What drugs are most tested in cancer clinical trials?"*

**Answer**: Pembrolizumab (137 trials), followed by Carboplatin (106) and Paclitaxel (106).
**5.2 seconds.** One query spanning four databases.

[96 of 100 benchmark queries pass →](https://samyama-ai.github.io/samyama-graph-book/biomedical_benchmark.html)

### Research

Reproducible, pre-registered systems papers — honest baselines, not SOTA claims. Each repo
ships code, data, and the preprint.

| Paper | Question | Preprint |
|---|---|---|
| [**group-commit-policy**](https://github.com/samyama-ai/group-commit-policy) | When is group-commit tuning worth it? A parameter-free policy is optimal above a device load threshold. | [arXiv:2606.18187](https://arxiv.org/abs/2606.18187) |
| [**lsm-bloom-allocation**](https://github.com/samyama-ai/lsm-bloom-allocation) | When is adaptive LSM Bloom-filter tuning worth it? Log-law + two-clock adaptivity frontier. | [arXiv:2606.18138](https://arxiv.org/abs/2606.18138) |
| [**biomedqa**](https://github.com/samyama-ai/biomedqa) | MCP tools vs text-to-Cypher vs standalone LLM over federated biomedical KGs. | [arXiv:2603.15080](https://arxiv.org/abs/2603.15080) |
| [**clinical-llm-graphrag**](https://github.com/samyama-ai/clinical-llm-graphrag) | When does KG grounding help an LLM? Public-KG null; out-of-training decisive. | repo |
| [**bandwidth-bound-scan**](https://github.com/samyama-ai/bandwidth-bound-scan) | A predictive bandwidth-fraction law for columnar scans (x86/AVX2 + Apple M4/NEON). | repo |
| [**cloud-egress-cache**](https://github.com/samyama-ai/cloud-egress-cache) | Billing-faithful egress caching: exact dollar-optimum + crossover rule. | repo |
| [**filtered-ann-regret**](https://github.com/samyama-ai/filtered-ann-regret) | Filtered-ANN strategy selection as a phase transition; finite-size scaling on SIFT1M. | repo |
| [**ce-metric-eval**](https://github.com/samyama-ai/ce-metric-eval) | When does q-error actually predict query-plan regret? | repo |
| [**dbms_research**](https://github.com/samyama-ai/dbms_research) | 1000+ open DBMS problems — formal statements, bounds, 6,700+ link-checked references. | catalog |

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
| [**assetops-kg**](https://github.com/samyama-ai/assetops-kg) | Industrial operations (IBM AssetOpsBench) | 12.6K nodes |

### Quick start

```bash
git clone https://github.com/samyama-ai/samyama-graph && cd samyama-graph
cargo build --release
./target/release/samyama
# RESP on :6379, HTTP on :8080
```

**Website**: [samyama.dev](https://samyama.dev) · **Book**: [samyama-ai.github.io/samyama-graph-book](https://samyama-ai.github.io/samyama-graph-book/) · **Contact**: [samyama.dev/contact](https://samyama.dev/contact)
