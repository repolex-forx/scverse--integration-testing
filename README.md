# Repolex Knowledge Graph of scverse/integration-testing

RDF knowledge graph data for [scverse/integration-testing](https://github.com/scverse/integration-testing), parsed by [repolex](https://repolex.ai).

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
rlex download scverse/integration-testing
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 26725873224bee5e32d1ab94dca982c3c56395f3
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 26725873224bee5e32d1ab94dca982c3c56395f3
│           └── chunk-001.nq.gz
├── blob
│   ├── 433609251879b18ea1b3df70c44a85b4a11c8bed.nq.gz
│   ├── 789f724ce681c31c3e45fb5c54d9741c8e98dd7c.nq.gz
│   ├── 82f927558a3dff0ea8c20858856e70779fd02c93.nq.gz
│   ├── b6ecf1443fc2437d0cef56f5240dbd2e055bd26e.nq.gz
│   ├── cc05b2846d35e636be2f866fbe179cb41066f121.nq.gz
│   ├── d29b592f60bd14a6ad9d1f7349587f81078603f1.nq.gz
│   └── f9b444cb1ca88c59dade5eb4a0360dd85394bde5.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 26725873224bee5e32d1ab94dca982c3c56395f3.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 15 files
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

[scverse/integration-testing](https://github.com/scverse/integration-testing)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
