# N1-A-R2 — Recursive Provenance

## Result

`RECURSIVE_PROVENANCE=BLOCKED`

| Layer | Universe | Verified | Partial | Unavailable/blocked |
|---|---:|---:|---:|---:|
| NOS3 reference | 1 commit | 1 commit | tree 0 | 1 tree OID |
| First-level declarations | 47 | 47 declarations | 44 candidate SHAs | 3 SHAs |
| First-level mode/type | 47 | 0 | 0 | 47 |
| Target reachability | 47 | 0 reproducibly | 0 | 47 |
| Target-commit `.gitmodules` | 47 | 0 | 0 | 47 |
| Complete recursive graph | unknown | 0 | 0 | blocked |

Immutable target URLs of the form `https://github.com/<owner>/<repo>/commit/<sha>` were formed for the 44 candidates. An initial representative group of 17 returned 17 web-transport cache misses. The equivalent failure was not repeated for the remaining 27. Cache miss does not mean a commit is absent; reachability is `UNAVAILABLE`, not `INVALID`, and a 40-hex format does not prove a remote object.

No target-commit `.gitmodules` was read. The mutable current `fprime-nos3` page displayed a `.gitmodules`, suggesting possible recursion, but the applicable fixed gitlink was unavailable. That observation cannot be assigned to the fixed subject.

## Completion procedure

1. Query each declared URL at the exact verified gitlink.
2. Confirm immutable commit existence/reachability.
3. Read `<repo>/<sha>/.gitmodules`, distinguishing proven 404 from transport failure.
4. Verify every nested path/mode/type/SHA tuple.
5. Repeat to a fixed point with cycle detection over normalized `(URL, SHA)`.
6. Preserve status code, bytes, length, timestamp, and SHA-256.
7. Set `recursive_complete: true` only when no edge remains partial.

This can use static APIs without clone or checkout. `N1B_READINESS=DEFERRED`.
