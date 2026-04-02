## Samyama — Graph-Vector Database for Billion-Edge Knowledge Graphs

We build [**Samyama Graph**](https://github.com/samyama-ai/samyama-graph) — an open-source graph-vector database written in Rust that handles **74 million nodes and 1 billion edges on a single machine for $2.50**.

### What we proved

We loaded the entire PubMed corpus (every article since 1966), ClinicalTrials.gov, Reactome pathways, and DrugBank into one graph. Then asked:

> *"What drugs are most tested in cancer clinical trials?"*

**Answer**: Pembrolizumab (137 trials), followed by Carboplatin (106) and Paclitaxel (106). **5.2 seconds.** One query spanning four databases.

[96 of 100 benchmark queries pass →](https://samyama-ai.github.io/samyama-graph-book/biomedical_benchmark.html)

### Repositories

| Repository | What | Scale |
|---|---|---|
| [**samyama-graph**](https://github.com/samyama-ai/samyama-graph) | Graph-vector database (Rust, OpenCypher, RESP) | 1877 tests, Apache 2.0 |
| [**samyama-graph-book**](https://github.com/samyama-ai/samyama-graph-book) | Architecture book + biomedical benchmark | [Read online](https://samyama-ai.github.io/samyama-graph-book/) |
| [**pubmed-kg**](https://github.com/samyama-ai/pubmed-kg) | PubMed/MEDLINE knowledge graph | 66.2M nodes, 1.04B edges |
| [**clinicaltrials-kg**](https://github.com/samyama-ai/clinicaltrials-kg) | ClinicalTrials.gov knowledge graph | 7.8M nodes, 27M edges |
| [**druginteractions-kg**](https://github.com/samyama-ai/druginteractions-kg) | Drug interactions (DrugBank + ChEMBL + SIDER) | 245K nodes, 388K edges |
| [**pathways-kg**](https://github.com/samyama-ai/pathways-kg) | Biological pathways (Reactome) | 119K nodes, 835K edges |
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
