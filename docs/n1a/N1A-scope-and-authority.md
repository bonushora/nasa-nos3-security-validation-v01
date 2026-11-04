# N1-A — Scope, Authority, and Preservation

## Historical result

`N1A_PROVENANCE_GREEN=BLOCKED`

N1-A produced a documentary transitive-provenance baseline but did not demonstrate all mandatory gitlinks. It was not security qualification, operational authorization, or authorization for N1-B.

> **EN-R1 editorial note:** This translation preserves the N1-A historical statement that one declaration lacked a corresponding observed tree entry. N1-A-R2 later established that the HTML listing was not immutable-tree proof and reclassified `gsw/ttc-command` as `UNAVAILABLE`, not demonstrated absent. The 44 candidate SHAs remain `PARTIAL`.

## Authority

- Project: `NASA-NOS3-SECURITY-VALIDATION-v0.1`.
- Governance: BH-SEP v2.3 / BH-SDP v2.3.
- Phase: documentary N1-A and read-only public static inspection.
- Risk: low.
- Public edition workspace reference: `<REDACTED_LOCAL_WORKSPACE>`.
- Upstream: `https://github.com/nasa/nos3`, observed branch `main`, commit `5a3bdee6be9a2c67fdf994ae6db56d5c60395302`.

The absolute local path in the Portuguese source is intentionally omitted from this derived public counterpart; the source remains unchanged and its hash preserves the original value.

## N0-R1 preservation

Before N1-A modification, 13 non-empty N0 artifacts, valid JSON, all 12 internally recorded hashes, and snapshot SHA-256 `097eda1c7eaa93382cba268597f858d53e4e61db47e21c3a34da9f34280d5006` were verified. The workspace was not a Git worktree. None of the 13 files changed.

## Performed

- Non-operational local inspection.
- Read-only inspection of official public pages and fixed `.gitmodules`.
- Documentary enumeration of declarations, candidate gitlinks, and limits.
- Future SBOM and provenance contracts.
- JSON, relative-link, count, and local SHA-256 checks.

## Not performed

No clone, checkout, repository archive, submodule materialization, installation, build, Docker, Vagrant, upstream script, NOS3/cFS/F´ execution, simulator, adversarial test, external SBOM workspace access, credential use, push, PR, or publication.

## Evidence states

| State | N1-A use |
|---|---|
| `VERIFIED` | identity demonstrated by immutable official source or locally hashable bytes |
| `PARTIAL` | valid evidence exists but immutable confirmation, reachability, or recursion is missing |
| `UNAVAILABLE` | the necessary source did not deliver bytes/identity |
| `BLOCKED` | a mandatory requirement cannot close without evidence/reconciliation |

The upper commit was verified. N1-A recorded 47 declarations, 44 candidate full SHAs, two unavailable full values, and one alleged declaration/tree divergence. R2 later corrected the last item to an unavailable tree entry and retained the aggregate provenance gate as blocked.
