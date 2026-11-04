# N1-A BH-SDP snapshot — English explanatory view

This is a derived editorial explanation of `governance/N1A-sdp-snapshot.json`, not a replacement for the immutable historical JSON and not new provenance evidence.

- Source SHA-256: `c56e512acd490cf80bbf3425b6c2bc8cddf73e0a00108f2f1a30b332142b29e0`
- Protocol: BH-SDP v2.3 under BH-SEP v2.3
- Phase: N1-A transitive provenance and SBOM readiness
- Marker: `N1A_PROVENANCE_GREEN=BLOCKED`
- Acceptance result: 9 `PASS`, 1 `BLOCKED`
- Blocking criterion: 4 — individual gitlink verification
- Fixed NOS3 commit: `5a3bdee6be9a2c67fdf994ae6db56d5c60395302`
- Root Git tree OID: `UNAVAILABLE`
- Git transport: `BLOCKED_DNS_NO_EQUIVALENT_RETRY`

The source snapshot historically records `proveniencia_transitiva` as `FALHOU` and uses the unaccented string `NAO_EXECUTADO` in several fields. N1-A-R2 later clarified that evidence insufficiency was not an execution failure and used `DEFERRED` for transitive provenance. EN-R1 preserves both the historical value and the later clarification; it does not repair the source.

N1-A recorded 47 `.gitmodules` declarations, 44 candidate gitlink identities as `PARTIAL`, two entries as `UNAVAILABLE`, and a claimed absence of `gsw/ttc-command`. That absence was not demonstrated from an immutable Git tree. N1-A-R2 therefore reclassified the path as `UNAVAILABLE`. Root tree identity, complete gitlink verification, target-commit reachability, and recursive provenance remained unverified.

The local workspace path present in the historical snapshot is not reproduced in this public explanatory view. The source remains hash-preserved.

