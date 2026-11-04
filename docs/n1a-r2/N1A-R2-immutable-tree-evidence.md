# N1-A-R2 — Immutable Tree Evidence

## Priority-gate result

| Gate | Requirement | State |
|---|---|---|
| R2-G1 | Root tree OID for fixed commit | `BLOCKED` |
| R2-G2 | SHA, mode, and type for `elf2cfetbl` and `fprime-nos3` | `BLOCKED` |
| R2-G3 | Nature of `gsw/ttc-command` in the Git tree | `BLOCKED` |

## Preserved upper identity

- Repository: `https://github.com/nasa/nos3`.
- Historically observed branch: `main`.
- Immutable commit: `5a3bdee6be9a2c67fdf994ae6db56d5c60395302`.
- Abbreviated parents displayed by the official page: `4428de5`, `c96a34b`.
- Release `v1_07_05` points to `5a3bdee`.
- Fixed `.gitmodules` contains 47 sections.

These verify the upper reference, not its tree OID.

## Methods and results

| Method | Request | Result | Treatment |
|---|---|---|---|
| Official commit page | immutable commit URL | confirmed commit/parents | valid commit evidence |
| `tree/<commit>` page | HTML tree at full SHA | cache miss | not interpreted as absence |
| Git Trees API via web tool | recursive tree endpoint | inaccessible | `UNAVAILABLE` |
| Git commit API via shell | commit-object endpoint | DNS failed for `api.github.com` | `UNAVAILABLE` |
| HTTPS with fixed resolution | preserved SNI/certificate with observed public IP | connection refused | `UNAVAILABLE`; no retry |
| Nested pages | fixed `fsw/tools`, `fsw/fprime`, `gsw` | cache miss/incomplete listing | no mode/type/absence inference |

No empty response, cache miss, DNS failure, or HTTP error became an OID or hash.

A 40-hex candidate value alone does not prove Git object type, mode, path binding, or remote reachability.

`TREE_OID=UNAVAILABLE`

A commit URL does not mathematically reveal its tree OID without commit-object content or an equivalent authenticated response.

## R2-G2

| Path | SHA | Mode | Type | State |
|---|---|---|---|---|
| `fsw/tools/elf2cfetbl` | `UNAVAILABLE` | `UNAVAILABLE` | `UNAVAILABLE` | `BLOCKED` |
| `fsw/fprime/fprime-nos3` | `UNAVAILABLE` | `UNAVAILABLE` | `UNAVAILABLE` | `BLOCKED` |

`160000` and `commit` are expected gitlink semantics, but were not observed through `ls-tree` or Git Trees and are not marked verified.

## R2-G3 clarification

`gsw/ttc-command` is verified as a declaration in fixed `.gitmodules`. R2 did not receive its immutable tree entry. The earlier `tree/main/gsw` listing was mutable and not demonstrated complete.

- declaration: `VERIFIED`;
- gitlink existence: `UNAVAILABLE`;
- absence claim: `NOT_DEMONSTRATED`;
- gate: `BLOCKED`.

## Minimum sufficient recovery

Capture the fixed commit object and recursive tree with `truncated: false`, preserve response bytes and SHA-256, and require exact path, `mode: 160000`, `type: commit`, and full SHA for all 47 declarations. Read-only `git cat-file -p` plus `git ls-tree -r` is equivalent and does not require checkout or submodule materialization.
