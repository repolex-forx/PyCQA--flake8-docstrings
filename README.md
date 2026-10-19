# Repolex Knowledge Graph of PyCQA/flake8-docstrings

RDF knowledge graph data for [PyCQA/flake8-docstrings](https://github.com/PyCQA/flake8-docstrings), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download PyCQA/flake8-docstrings
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 2e2f1b2700dafe36115c2e2efc3ac7d66aa4ee3e
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 2e2f1b2700dafe36115c2e2efc3ac7d66aa4ee3e
│           └── chunk-001.nq.gz
├── blob
│   ├── 305007bb2d817f5aa4ece170ace36824a6a6e664.nq.gz
│   ├── 3d74d9e03604141b4f71f4b4e12d083371ed0021.nq.gz
│   ├── 5cd80c756c0cf7e8d46f7fbe71040f1deed3ef57.nq.gz
│   ├── 5e4cc71b0bbe3d3a42647928cc42b83cceb9b0e4.nq.gz
│   ├── 606849326a4002007fd42060b51e69a19c18675c.nq.gz
│   ├── 60b434582ac7b8b49ac60a7f67936d9b8deff66a.nq.gz
│   ├── 6b68635eca04cb75f6eb09dd161905ce8ae97965.nq.gz
│   ├── 6eabbdeac8df2d7d57fef12818499df4f32bf10c.nq.gz
│   ├── 9aeff1e26d05d27e4ea0d9dd317c65e0d86441a9.nq.gz
│   ├── aa8361945e1421af6d29ee4eae1c6563027839ec.nq.gz
│   └── fffe028219565be1f0339e1cb65b63311c00fea1.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 2e2f1b2700dafe36115c2e2efc3ac7d66aa4ee3e.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 19 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[PyCQA/flake8-docstrings](https://github.com/PyCQA/flake8-docstrings)

---
*Parsed on 2026-10-19 by [repolex](https://repolex.ai)*
