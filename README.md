# Repolex Knowledge Graph of geopandas/pgpkg

RDF knowledge graph data for [geopandas/pgpkg](https://github.com/geopandas/pgpkg), parsed by [repolex](https://repolex.ai).

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
rlex download geopandas/pgpkg
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── f9d4c5efe72949cc714b12969b0a48d57c14bb56
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── f9d4c5efe72949cc714b12969b0a48d57c14bb56
│           └── chunk-001.nq.gz
├── blob
│   ├── 06ce07bef543aa78320cd3674d6be8a5ad9e969e.nq.gz
│   ├── 242758e0c2a71fff6562b7d841213e62299a0927.nq.gz
│   ├── 4ac33a23b91a97ebc3c6911e8fca318b1f9b4c0a.nq.gz
│   ├── 4caeb074040452d8d39721bfe91596ea3dfd27cf.nq.gz
│   ├── 69f31db25b956cf0cb4de978c0a24e793d3eb87d.nq.gz
│   ├── 7afe06a6cf67a37feb17f7b7f9fe881e8107aef0.nq.gz
│   ├── 94abb234d942141d0d2c19f583c5e41fac7e1883.nq.gz
│   ├── a4c647016d1482b40fb0d408036779a989abf50b.nq.gz
│   ├── af424e3557ab52ea2601be78e3b432b4f16a82e2.nq.gz
│   ├── cdf92b8647a3634e05539c91311485435efbbe72.nq.gz
│   └── df173aee237bd9fd9f444be3300679c942a6501f.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── f9d4c5efe72949cc714b12969b0a48d57c14bb56.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 17 files
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

[geopandas/pgpkg](https://github.com/geopandas/pgpkg)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
