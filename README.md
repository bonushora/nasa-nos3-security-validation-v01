# SSSVL — NASA NOS3 Security Validation Research

SSSVL (Space Systems Security Validation Lab) is an independent research program developing reproducible methods for validating security-relevant effects in simulated space-software systems. This repository prepares the documentary baseline for `NASA-NOS3-SECURITY-VALIDATION-v0.1`.

> **This is an independent research initiative and is not affiliated with, sponsored by, or endorsed by NASA.**

NASA NOS3, NASA cFS, and F´ are distinct research subjects. NOS3 is the simulation and integration environment under study; cFS and F´ are alternative flight-software frameworks whose integrations may later be compared under separately authorized, controlled experiments. Their names, history, or use do not constitute evidence that this independent project is qualified, endorsed, operationally ready, or suitable for flight.

## Current status

```text
DOCUMENTATION_STATUS=PASS
TRANSITIVE_PROVENANCE_STATUS=BLOCKED
EXPERIMENTAL_SECURITY_STATUS=NOT_QUALIFIED
REMOTE_PUBLICATION=NOT_AUTHORIZED
NOS3_EXECUTION=NOT_AUTHORIZED
```

`DOCUMENTATION_STATUS=PASS` applies only to the EN-R1 preparation and its local editorial checks. It does not override the blocked provenance gate or qualify any security property.

## Scientific objective

The project investigates whether command intent, authority, dispatch, and completed simulated effect can be distinguished and independently reconciled across NOS3 integrations. The central scientific questions include:

- whether a received command was authorized before dispatch;
- whether dispatch produced the intended effect, no effect, a partial effect, or an ambiguous effect;
- whether retry, replay, loss, delay, restart, or concurrency can duplicate or conceal effects;
- whether telemetry and executor logs agree with an independent witness;
- whether cFS and F´ can be compared without unequal instrumentation;
- whether every result can be attributed to an immutable, transitively resolved software identity.

SBOMs support software supply-chain traceability, but they are not the name or central scientific mission of SSSVL and do not prove behavioral security.

## Research phases

| Phase | Purpose | Documentary result | Security result |
|---|---|---|---|
| N0 / N0-R1 | architecture, threat model, trust boundaries, witness design, scenarios | `N0_DOCUMENTATION_GREEN=PASS` | `NOT_QUALIFIED` |
| N1-A | first-level provenance and SBOM integration contracts | `N1A_PROVENANCE_GREEN=BLOCKED` | `NOT_QUALIFIED` |
| N1-A-R2 | immutable-tree and recursive-provenance recovery | `N1A_R2_PROVENANCE_GREEN=BLOCKED` | `NOT_QUALIFIED` |
| EN-R1 | publication-ready English documentary preparation | `EN_R1_DOCUMENTATION_GREEN=PASS` | `NOT_QUALIFIED` |

N1-A historically reported that `gsw/ttc-command` was absent from an observed directory listing. N1-A-R2 clarified that absence was not demonstrated by an immutable tree and reclassified the entry as `UNAVAILABLE`. The 44 recovered SHA values remain `PARTIAL`; the root Git tree OID and recursive provenance remain unavailable.

The historical N0-R1 observation was revalidated on 2026-11-04 in `America/Sao_Paulo`. Its 10 documentary criteria passed. An earlier count of 49 submodules was corrected to 47 after `cfdp` and `spacecop-ce` were found absent from the fixed manifest. The local root was not a Git worktree, the named handoff file was not found, Git transport was DNS-blocked, and the recommended N1 sequence remained conditional on readiness gates G1–G12. These facts are chronology, not new EN-R1 findings.

## Evidence available

- fixed upper NOS3 commit: `5a3bdee6be9a2c67fdf994ae6db56d5c60395302`;
- observed release: `v1_07_05`;
- fixed `.gitmodules` declaration count: 47;
- architecture, threat model, trust boundaries, independent-witness design, and 18 proposed adversarial scenarios;
- first-level transitive inventory containing 44 candidate SHAs and 3 unavailable entries;
- SBOM and provenance evidence contracts;
- immutable historical Portuguese snapshots and reproducible local hashes;
- English source mapping, semantic review, and public-disclosure review.

No build, simulator, flight-software framework, upstream script, fault injection, or adversarial experiment was executed to produce this documentation.

## Experimental limitations

- The NOS3 root Git tree OID has not been recovered.
- No one of the 47 declared entries has immutable readback of `mode: 160000`, `type: commit`, and SHA as a complete tuple.
- Two submodule SHAs and the `gsw/ttc-command` tree entry remain unavailable.
- Target-commit reachability and nested `.gitmodules` files are not verified.
- The independent witness is designed, not implemented.
- The scenarios are specifications, not results.
- Simulated effects do not demonstrate physical spacecraft effects.

## Repository organization proposed by EN-R1

```text
README.md                         public project overview
docs/n0/                         English N0 documentary baseline
docs/n1a/                        English N1-A historical baseline
docs/n1a-r2/                     English R2 clarification baseline
governance/historical/           English explanatory views of immutable snapshots
governance/EN-R1-sdp-snapshot.json
archive/original-pt/             planned byte-for-byte Portuguese archive
evidence/                        mapping, semantic review, disclosure, validation
```

The current EN-R1 files are staging artifacts. Final migration and remote publication are outside this mission.

## Governance and authorization

The documentary work follows BH-SEP v2.3 and BH-SDP v2.3. Authorization is phase-specific and fail-closed. A documentation PASS does not authorize publication, cloning, installation, build, NOS3 execution, cFS/F´ execution, adversarial simulation, fault injection, or cybersecurity qualification.

## Reproducibility requirements

A future technical result must bind the experiment identifier to the governance snapshot, NOS3 commit and tree, recursively verified gitlinks, tool and image digests, configuration hashes, SBOM references, scenario inputs, witness identity, and preserved outputs. Missing provenance, unhealthy witness data, or ambiguous effects require `INCONCLUSIVE`, `ABORTED`, or a blocked gate—not PASS.

## Documentation index

- [N0 scope and authority](docs/n0/N0-scope-and-authority.md)
- [N0 architecture](docs/n0/N0-nos3-architecture.md)
- [N0 threat model](docs/n0/N0-threat-model.md)
- [Independent effect witness](docs/n0/N0-independent-effect-witness.md)
- [N1-A transitive inventory](docs/n1a/N1A-upstream-transitive-inventory.md)
- [N1-A-R2 reconciliation](docs/n1a-r2/N1A-R2-gitlink-reconciliation.md)
- [Semantic equivalence review](evidence/semantic-equivalence-matrix.md)
- [Public disclosure review](evidence/disclosure-review.md)
- [EN-R1 governance snapshot](governance/EN-R1-sdp-snapshot.json)

## Independent research disclaimer

All NASA, NOS3, cFS, F´, CCSDS, and third-party names remain the property of their respective owners. References identify research subjects and sources only. Nothing in this repository claims certification, flight qualification, operational approval, NASA affiliation, or endorsement.
