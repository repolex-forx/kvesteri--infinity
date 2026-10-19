# Repolex Knowledge Graph of kvesteri/infinity

RDF knowledge graph data for [kvesteri/infinity](https://github.com/kvesteri/infinity), parsed by [repolex](https://repolex.ai).

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
rlex download kvesteri/infinity
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1be47baffce430fa0f393fbe0d0dd4788f10d820
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 1be47baffce430fa0f393fbe0d0dd4788f10d820
│           └── chunk-001.nq.gz
├── blob
│   ├── 2e766368afd6f59fddfd3effbe18ff85d35a4735.nq.gz
│   ├── 408a31737626ceced20782dd9128b7bef66f56ed.nq.gz
│   ├── 43bd71d9ca366369c06ad9de644a1e490c8c05af.nq.gz
│   ├── 89832919750b5b9f8d4cb78978c24c256bbdcac3.nq.gz
│   ├── 8b791c449302f8c15641474176cd89dc46f8546a.nq.gz
│   ├── b5762e514c06ca9ccbd1afec0ed49edc1ebc92e4.nq.gz
│   ├── d483e44746231020d6129a0efe3d2b861404482f.nq.gz
│   ├── ddbed596a62ee422e0df20a4e2f51d9a686032f4.nq.gz
│   ├── ded606788041fc9cd4d017e2dfe5a6e9bdeefbae.nq.gz
│   ├── e85a15a0fdf0d24b46b3481a2e456f4d43c9fc33.nq.gz
│   └── fa802168651e888cd62abf8df7571391284fc536.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 1be47baffce430fa0f393fbe0d0dd4788f10d820.nq.gz
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

[kvesteri/infinity](https://github.com/kvesteri/infinity)

---
*Parsed on 2026-10-19 by [repolex](https://repolex.ai)*
