# N0 — Acceptance Matrix

## Result

`N0_DOCUMENTATION_GREEN=PASS`

This documentary result coexists with `NOT_QUALIFIED` and `NOT_AUTHORIZED` for experiments.

| # | Criterion | Evidence | Result |
|---:|---|---|---|
| 1 | Upper upstream identity observed and fixed | URL, branch, full SHA, immutable commit, release, method, transport limit in [upstream identity](N0-upstream-identity.md) | PASS |
| 2 | NOS3/NOS Engine, cFS, F´, simulators, command/TLM architecture documented | [architecture](N0-nos3-architecture.md) and [cFS/F´ integration](N0-cfs-fprime-integration.md) | PASS |
| 3 | Existing, proposed, and unknown capabilities separated | D/E/U classes in [scope](N0-scope-and-authority.md) | PASS |
| 4 | Trust boundaries and threat model complete | [trust boundaries](N0-trust-boundaries.md), [threat model](N0-threat-model.md) | PASS |
| 5 | Documentary adversarial scenarios specified without execution | 18 cases in [scenario matrix](N0-adversarial-scenario-matrix.md) | PASS |
| 6 | Independent effect witness designed | separation, events, persistence, recovery, limits in [witness](N0-independent-effect-witness.md) | PASS |
| 7 | Future SBOM/provenance/integrity integration bounded | bundle, normalization, gates in [SBOM/provenance](N0-sbom-provenance-integration.md) | PASS |
| 8 | Readiness and N1 recommendation documented without expanding authority | G1–G12 in [readiness](N0-experiment-readiness.md) | PASS |
| 9 | N0 artifacts pass proportional documentary checks | presence, JSON, links, markers, counts, local SHA-256 | PASS |
| 10 | BH-SDP snapshot consistent | normative fields, independent states, evidence, hashes, limits, deferred work in [snapshot explanation](../../governance/historical/N0-sdp-snapshot.en.md) | PASS |

Accepted limits included unavailable upstream byte hashes due DNS, unresolved gitlinks for all 47 declared submodules, mutable `/latest/` documentation, no exercised behavior, and the missing named handoff file. These do not invalidate the historical documentary PASS; they prevent operational readiness and qualification.

> **EN-R1 chronology note:** N1-A and R2 later refined the provenance status. They did not retroactively change the scope of the N0 documentary PASS.
