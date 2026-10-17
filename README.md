# Repolex Knowledge Graph of colcon/colcon-clean

RDF knowledge graph data for [colcon/colcon-clean](https://github.com/colcon/colcon-clean), parsed by [repolex](https://repolex.ai).

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
rlex download colcon/colcon-clean
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 9cff7c8b8a24ef734ce18621a8ac6504d00d412e
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 9cff7c8b8a24ef734ce18621a8ac6504d00d412e
│           └── chunk-001.nq.gz
├── blob
│   ├── 09d2ab1422293c1a75089e398457422540a4fa75.nq.gz
│   ├── 0aa7e017003cb22e999600bfe96389bddcc3f446.nq.gz
│   ├── 0f17157ed42b486a0c57cbffddd97987a4844e6b.nq.gz
│   ├── 0f65d5cb6b576d178d3c990ae15fbc5ba17c0a5f.nq.gz
│   ├── 1675169988de8b693733b9f6fad2bac90ac4a30a.nq.gz
│   ├── 169c343ecad4270530b803b50d547c07edb3be9c.nq.gz
│   ├── 1929e6bf4bc5d24ff1e07a6710782c2cfe00eab9.nq.gz
│   ├── 1bf70061f2c781974cea87778c1aa67ed8118da7.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 29e73b0612711d70291ccf6da25cf6d0169e18a0.nq.gz
│   ├── 415561b8fdbd09a0e3ab882ab59fa15b9920b2e9.nq.gz
│   ├── 48b0dbd05d8b2ade421ae4f97e630ecef5cab48b.nq.gz
│   ├── 5e326a0dfb784ba28486bec975394815ca819aa8.nq.gz
│   ├── 632cf30bec73a2493eb3065bcf49b04bff06cb95.nq.gz
│   ├── 7087a929dccbe5fd4d7774db9113dfa917f94889.nq.gz
│   ├── 808d6f884a960d615ace367a9fc0ca282aeb3429.nq.gz
│   ├── 81e0e3b0160803b25ca9644882086403bb8adaf0.nq.gz
│   ├── 87bef9b81c7700c84875bd90ce9500223b95d277.nq.gz
│   ├── 8fb504ffc93bb0c5e176f42a86f5c9d3ec23eb23.nq.gz
│   ├── 9e2d11643b1482eb707f6811ce24e4428392909d.nq.gz
│   ├── a6e2ac735070565f8c123dc32b7bd9ffe675338e.nq.gz
│   ├── b5b8657d33ff1de97c3649cc130d852ee1b02535.nq.gz
│   ├── b6e47617de110dea7ca47e087ff1347cc2646eda.nq.gz
│   ├── bc7b098443664a3edce25625e394ddccc38d23ef.nq.gz
│   ├── c841839ee71cd1e08a6d712e14085b98f52d8f00.nq.gz
│   ├── ce7aa98cbc233e13d58fc21776975c432b6c81eb.nq.gz
│   ├── d0d446e1db9e556f477f9f0deed2f54f07a24b94.nq.gz
│   ├── d5d601b3defe3ee187738136db5575cf4dfb8d00.nq.gz
│   ├── d8a072a566f7e4ef8aceb288531986ff06807e8b.nq.gz
│   ├── dffe460f162da9929178a7ce342532e7ba896425.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ede3573738c85fe88f253e547ad727357e6be82d.nq.gz
│   ├── edf1d1ad29f1aff117886755569f0a2b6fbca694.nq.gz
│   ├── f75bf4faab84ed6ea1cd2c2ce95cd7614f134347.nq.gz
│   └── febe560fcf4fb1ec767a92a7c5d70dd5f18cc19e.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 9cff7c8b8a24ef734ce18621a8ac6504d00d412e.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 43 files
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

[colcon/colcon-clean](https://github.com/colcon/colcon-clean)

---
*Parsed on 2026-10-17 by [repolex](https://repolex.ai)*
