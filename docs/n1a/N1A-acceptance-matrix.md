# N1-A — Acceptance Matrix

## Historical result

`N1A_PROVENANCE_GREEN=BLOCKED`

| # | Mandatory criterion | Historical evidence | Result |
|---:|---|---|---|
| 1 | Intact N0-R1 baseline | 13 artifacts, snapshot SHA-256 `097eda1c7eaa93382cba268597f858d53e4e61db47e21c3a34da9f34280d5006`, 12 internal hashes | PASS |
| 2 | Preserved upper NOS3 identity | URL, `main`, full commit, limits in [inventory](N1A-upstream-transitive-inventory.md) | PASS |
| 3 | Complete declared-submodule inventory | 47 rows with path, URL, identity, type, relation, dependencies, state, source | PASS |
| 4 | Gitlinks individually verified | 44 candidates, two unavailable, historical `ttc-command` issue in [verification](N1A-gitlink-verification.md) | BLOCKED |
| 5 | Sources and limits recorded | M/C/F/G/S, mutable bridge, API/transport, recursion limits | PASS |
| 6 | Complete SBOM integration contract | external envelopes, cFS, F´, aggregate, S1–S8 | PASS |
| 7 | Complete provenance evidence model | P0–P7, custody, witness association | PASS |
| 8 | No external project modified | local/public read-only scope | PASS |
| 9 | N1-A documents present and validated | eight files, JSON, links, counts, markers, hashes | PASS |
| 10 | Consistent BH-SDP v2.3 snapshot | identity, authority, risk, evidence, limits, next step in [snapshot explanation](../../governance/historical/N1A-sdp-snapshot.en.md) | PASS |

All criteria were mandatory. Criterion 4 made the aggregate result `BLOCKED` despite nine documentary passes.

> **R2 clarification:** the alleged `gsw/ttc-command` absence was not immutable-tree evidence. R2 preserved the gate as blocked but changed the entry to `UNAVAILABLE`; no candidate SHA became verified.
