# N1-A-R2 — Scope, Authority, and Preservation

## Decision

`N1A_R2_PROVENANCE_GREEN=BLOCKED`

R2 preserved and organized valid evidence but did not obtain the immutable tree object or recursive coverage. Insufficient evidence is represented as `DEFERRED` in the normative provenance state, not as an execution failure.

## Bounded authority

- Program: SSSVL — Space Systems Security Validation Lab.
- Project: `NASA-NOS3-SECURITY-VALIDATION-v0.1`.
- Governance: BH-SEP v2.3 / BH-SDP v2.3.
- Phase: N1-A-R2 public static read-only inspection and local documentation.
- Risk: low.
- Public edition workspace reference: `<REDACTED_LOCAL_WORKSPACE>`.
- Fixed upstream: `https://github.com/nasa/nos3` at `5a3bdee6be9a2c67fdf994ae6db56d5c60395302`.

The original absolute local path remains in the immutable Portuguese source and is omitted only from this public derivative. A mutable HEAD never replaced the fixed commit.

## Pre-edit R2 readback

| Baseline | Physical verification | Result |
|---|---|---|
| N0-R1 | 13 artifacts; snapshot SHA-256 `097eda1c7eaa93382cba268597f858d53e4e61db47e21c3a34da9f34280d5006`; 12 hashes reproduced | `PASSOU` |
| N1-A | 8 artifacts; snapshot SHA-256 `c56e512acd490cf80bbf3425b6c2bc8cddf73e0a00108f2f1a30b332142b29e0`; 7 hashes reproduced | `PASSOU` |
| JSON | both snapshots parsed with `jq` | `PASSOU` |
| Pre-patch physical divergence | none | `NOT_APPLICABLE` |

The 21 prior files remained unchanged. The original N1-A snapshot was retained as historical evidence rather than repaired in place.

## Performed / not performed

Performed: public read-only queries, bounded Git Trees/HTTPS attempts, fixed commit/release/manifest inspection, 47-declaration comparison, local documentation and hashing.

Not performed: clone, checkout, archive download, submodule materialization, installation, build, Docker, Vagrant, upstream scripts, NOS3/cFS/F´/simulator execution, adversarial experiments, independent SBOM workspace access, remote writing, push, PR, or publication.

## BH-SDP semantic correction

N1-A used `FALHOU` for transitive provenance even though no provenance execution produced a false result. R2 uses `DEFERRED` for insufficient evidence and keeps the aggregate gate `BLOCKED`. It also uses normative `NÃO_EXECUTADO` values with their required spelling.

Primary evidence is documented in [immutable tree evidence](N1A-R2-immutable-tree-evidence.md).

Primary historical sources: [immutable commit](https://github.com/nasa/nos3/commit/5a3bdee6be9a2c67fdf994ae6db56d5c60395302), [release v1_07_05](https://github.com/nasa/nos3/releases/tag/v1_07_05), and [fixed `.gitmodules`](https://raw.githubusercontent.com/nasa/nos3/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/.gitmodules).
