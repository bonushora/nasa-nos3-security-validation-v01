# N1-A — Gitlink Verification

## Historical result

`GITLINK_VERIFICATION=BLOCKED`

The upper commit and 47 declarations were observed, but N1-A lacked enough evidence to verify every gitlink individually.

> **R2 clarification:** The N1-A statement that `gsw/ttc-command` was absent from the observed `gsw` listing did not demonstrate absence from the immutable tree. R2 classified its tree entry as `UNAVAILABLE`. It also established that mode/type readback was unavailable for all 47 entries.

## N1-A procedure

1. Fix URL, observed branch, and full commit through the official immutable page.
2. Read fixed raw `.gitmodules` and count 47 sections.
3. Inspect public component/FSW/GSW/simulator pages while `main` pointed to the fixed commit.
4. Extract full SHA strings from official submodule link targets.
5. Compare paths to declarations.
6. Reject empty hashes, abbreviations as final identity, and unsupported inference.

## Historical findings

- 44 candidate full SHAs were recorded in the [inventory](N1A-upstream-transitive-inventory.md).
- `fsw/tools/elf2cfetbl` and `fsw/fprime/fprime-nos3` remained `UNAVAILABLE`.
- `gsw/ttc-command` was historically marked `BLOCKED`; R2 corrected this to an unavailable immutable-tree entry.
- Root tree OID remained `UNAVAILABLE`.
- Target commit existence/reachability was not uniformly demonstrated.
- Nested submodules were not enumerated.

Git shell transport failed at DNS. The web interface did not provide Git Trees readback. No transport failure was converted into a valid SHA.

## Recovery conditions

Closure requires immutable `git ls-tree -r 5a3bdee6be9a2c67fdf994ae6db56d5c60395302` or equivalent Git Trees output, preserved bytes and SHA-256, root tree OID, all `path → mode 160000 → type commit → SHA` tuples, target reachability, and recursive `.gitmodules` enumeration.

`TRANSITIVE_FREEZE=NOT_DEMONSTRATED`
