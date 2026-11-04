# N1-A-R2 — Acceptance Matrix

## Result

`N1A_R2_PROVENANCE_GREEN=BLOCKED`

| # | Criterion | Evidence | State |
|---:|---|---|---|
| 1 | Prior-baseline integrity | N0-R1/N1-A snapshot hashes and 19 internal hashes reproduced in [scope](N1A-R2-scope-and-authority.md) | PASS |
| 2 | Commit and tree identity | commit confirmed; `TREE_OID=UNAVAILABLE` in [tree evidence](N1A-R2-immutable-tree-evidence.md) | BLOCKED |
| 3 | Reconciliation of 47 declarations | 47 rows, no complete immutable entry readback in [reconciliation](N1A-R2-gitlink-reconciliation.md) | BLOCKED |
| 4 | Git object type and mode | unavailable for all 47; `160000/commit` not inferred | BLOCKED |
| 5 | Two pending gitlinks recovered | `elf2cfetbl`, `fprime-nos3` remain unavailable | BLOCKED |
| 6 | `gsw/ttc-command` resolved | declaration verified; tree existence/absence unproven | BLOCKED |
| 7 | Commit existence/reachability | initial 0/17 due cache miss; circuit stopped | BLOCKED |
| 8 | Recursive coverage | no target-commit internal manifest verified in [recursive provenance](N1A-R2-recursive-provenance.md) | BLOCKED |
| 9 | Local-document integrity | six R2 artifacts, links, counts, JSON, hashes validated | PASS |
| 10 | BH-SDP/matrix conformity | historical snapshot preserved; R2 uses normative states and provenance `DEFERRED` | PASS |

There were 3 `PASS`, 7 `BLOCKED`, and 0 `FALHOU`. Evidence/transport blockage is not an execution failure. All criteria were mandatory, so the aggregate state remained `BLOCKED`.
