# N1-A-R2 BH-SDP snapshot — English explanatory view

This is a derived editorial explanation of `governance/N1A-R2-sdp-snapshot.json`. The original JSON remains the authoritative, unchanged historical record; this document creates no new Git or provenance evidence.

- Source SHA-256: `738deb0ad600d52a52a1f8a8c15ee75ce060c1c99f84fdbb1a4937afe6eb99aa`
- Protocol: BH-SDP v2.3 under BH-SEP v2.3
- Phase: N1-A-R2 provenance recovery and freeze attempt
- Marker: `N1A_R2_PROVENANCE_GREEN=BLOCKED`
- Acceptance result: 3 `PASS`, 7 `BLOCKED`, 0 `FALHOU`
- Fixed NOS3 commit: `5a3bdee6be9a2c67fdf994ae6db56d5c60395302`
- Fixed release label: `v1_07_05`
- `.gitmodules` declarations: 47, declaration set `VERIFIED`
- Root Git tree OID: `UNAVAILABLE`, state `BLOCKED`
- Transitive provenance normative state: `DEFERRED`

R2 retained 44 candidate gitlink SHAs as `PARTIAL`; it did not promote them to immutable gitlinks without mode `160000`, object type `commit`, and path binding from the fixed root tree. The entries `fsw/tools/elf2cfetbl`, `fsw/fprime/fprime-nos3`, and `gsw/ttc-command` remained `UNAVAILABLE`. Target-commit existence, reachability, nested `.gitmodules`, and recursive fixed-point coverage remained blocked.

The snapshot corrects the prospective BH-SDP classification of evidence insufficiency: the task was deferred/blocked, not a failed execution. It does not change the earlier N1-A file. The historical local workspace path is intentionally omitted from this public explanatory view.

