# N1-A — Readiness, Gates, and Next Phase

## Historical state

`N1A_PROVENANCE_GREEN=BLOCKED`

Documentation/contracts were reviewable; transitive provenance was not frozen.

| Gate | Requirement | N1-A state | Evidence/pending item |
|---|---|---|---|
| G1 | intact N0-R1 baseline | `PASS` | 13 files, snapshot, 12 hashes |
| G2 | upper NOS3 identity | `PASS` | URL, `main`, full commit, immutable page |
| G3 | 47 declarations inventoried | `PASS` | 47 rows and URLs |
| G4 | every gitlink individually verified | `BLOCKED` | 44 candidates, two unavailable, one historical alleged divergence |
| G5 | sources and limits recorded | `PASS` | source codes, mutable bridge, transport limits |
| G6 | cFS/F´ SBOM contract | `PASS` | subjects, hashes, deltas, fail-closed rules |
| G7 | provenance model | `PASS` | P0–P7, custody, witness binding |
| G8 | external projects preserved | `PASS` | no independent workspace access/modification |
| G9 | eight N1-A artifacts validated | `PASS` | presence, JSON, links, counts, hashes |
| G10 | consistent BH-SDP snapshot | `PASS` | independent states, limits, next step |

G4 was mandatory and non-compensable.

Open risks were an orphan/mismatched declaration, two unavailable full SHAs, mutable `tree/main` evidence, incomplete target reachability/recursion, future external SBOMs, and no build/tool/image evidence.

> **R2 outcome:** R2 did not recover the immutable tree. It corrected `gsw/ttc-command` to `UNAVAILABLE`, retained 44 SHAs as `PARTIAL`, and found mode/type/reachability/recursion still blocked.

The minimum recovery remains:

1. restore read-only Git Trees API or trusted Git transport;
2. capture the root tree OID and `ls-tree -r` for the fixed commit, preserving response bytes and SHA-256;
3. resolve `elf2cfetbl` and `fprime-nos3`, and reconcile `gsw/ttc-command`;
4. confirm existence/reachability for all 47 expected targets;
5. enumerate recursive `.gitmodules` by immutable object without checkout/materialization while that remains outside authority; and
6. issue a new snapshot and matrix before reevaluating `N1A_PROVENANCE_GREEN`.

N1-B required separate authorization and remained `NOT_AUTHORIZED`; no N1-B execution occurred. Its readiness was deferred.
