# Bitnats indexer user assistance

Help users install, configure, and operate the intended cloneable Bitnats Rust
indexer using only this public repository and its public documentation.

## Current status

The Rust indexer is not implemented or runnable in this checkout. There are no
Rust source files, Cargo manifests, indexer binary, or installer. The repository
currently supplies protocol documentation, archive data, and Node.js verification
tools. Those tools are not a running indexer.

Read the [project overview](README.md) and inspect the actual checkout before
giving operational advice. For a capability missing below, report that it is
not implemented and explain which part of the user's request cannot proceed.
Do not invent installation commands, binary names, flags, configuration keys,
ports, dependencies, or supported versions.

## Installation and operation

| User task | Current support |
| --- | --- |
| Establish indexer prerequisites and supported versions | Pending implementation; no indexer toolchain or node-version requirements are defined. |
| Build or install the indexer | Pending; no Rust build target or installable indexer is supplied. |
| Configure Bitcoin Core and Ord connections | Pending; live connections and connection configuration are not implemented. |
| Select network and data directory | Pending; no indexer settings or flags exist. |
| Start indexing and inspect progress | Pending; no indexing process or progress interface exists. |
| Stop safely and resume | Pending; no index lifecycle or resume behavior is implemented. |
| Troubleshoot runtime failures | Report the missing runtime; do not suggest rebuilding an index or changing node settings as a remedy. |

## What existing checks establish

Bitcoin-derived classification and Ord-dependent inscription, provenance, and
ownership checks are distinct. Existing JavaScript helpers count leading zeros
in supplied block hashes and validate supplied artifact fields. Confirmation and
sat-placement facts must be supplied by the caller; missing facts cause an
`ExternalDependencyError`. They do not query live nodes or verify ownership.
Archive tools check local bytes against hash commitments, not live-chain validity.

The [public verification guide](docs/09-public-verification.md) documents these
optional archive tools and their prerequisites. Tests, V1 verification, and V2
reproduction are not an indexer installation or startup procedure.

## Operational boundaries

- Keep credentials private; never print them or expose authenticated RPC
  endpoints publicly.
- Before deleting or rebuilding an index, overwriting configuration, or changing
  node settings, explain the effect and obtain the user's authorization.
- Running an indexer must not initiate wallet, signing, inscription, or broadcast
  actions.
- Preserve canonical data, ordering, inscription IDs, commitments, protocol
  rules, and release status. Preserve unrelated local changes.
