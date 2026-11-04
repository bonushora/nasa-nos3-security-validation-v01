# EXP001-P0 evidence provenance and reproducibility contract

## Experiment identity

Before execution, a canonical manifest must bind:

- protocol, hypothesis, scenario, oracle, and schema versions;
- governance snapshot and explicit authorization;
- NOS3 repository commit and root tree;
- every recursively resolved gitlink and target reachability proof;
- cFS or F´ subject identity without modifying independent workspaces;
- source, toolchain, dependency, image, binary, configuration, dictionary, and table hashes;
- SBOM/attestation identities;
- witness software/configuration/calibration;
- synthetic grant, command bytes, fault schedule, seed, initial state, timing, resources, and topology;
- analyst code and normalized-output format.

The manifest receives an `experiment_identity_digest`. Any mismatch creates a distinct experiment and blocks comparison.

## Provenance layers

| Layer | Required evidence |
|---|---|
| P0 governance | authority, risk, stop authority, snapshot |
| P1 subject source | repository, commit, tree, recursive gitlinks |
| P2 build/tooling | versions, inputs, invocation, environment |
| P3 artifacts | binaries/images/configurations and SHA-256 |
| P4 run inputs | scenario, seed, grant, command, fault schedule |
| P5 instrumentation | witness identity, schema, calibration, health |
| P6 raw outputs | immutable events, captures, state snapshots, logs |
| P7 analysis | oracle version, rule trace, findings, decision |

NOS3 P1 remains incomplete because transitive provenance is `BLOCKED`. Therefore execution readiness remains blocked even though P0 documentation can pass.

## Evidence custody

Raw evidence is written append-only, hashed at capture, and sealed before analysis. A manifest records relative path, media type, byte length, SHA-256, producer, capture time, custody event, and any redaction derivative. Originals are never overwritten by normalized or public derivatives.

Chain-of-custody changes are separately signed or otherwise authenticated under an approved future implementation. Credential material and operational secrets must not enter the evidence set.

## Reproducibility package

A reproducibility package contains the canonical manifest, raw evidence index, normalized events, oracle input/output, rule trace, uncertainty/calibration report, deviations, and human review. It must support byte-level identity checks and clearly distinguish unavailable proprietary/external inputs.

Reproduction means another authorized analyst can reconstruct the same oracle input and decision from preserved evidence; it does not require recreating a real spacecraft effect.

## Comparator and repetition controls

Baselines and negative controls use the same subject identity, instrumentation, resource limits, and observation window as the corresponding fault run except for the preregistered independent variable. Run order, reset proof, seeds, repetition count, exclusions, and stopping rules are fixed before subject-data inspection.

## Isolation requirements

Future execution requires isolated non-operational networks, synthetic keys/data, explicit egress policy, resource limits, reset/cleanup evidence, no operational endpoint, and emergency stop authority. Witness and evidence storage should be separated from the subject according to the stated independence level.

## Reproducibility failures

Missing identity, mutable dependency, unrecorded deviation, hash mismatch, incomplete reset, unknown seed, unavailable oracle version, or broken custody prevents PASS. The run is `INCONCLUSIVE` or `ABORTED` according to whether evidence validity or containment was lost.

