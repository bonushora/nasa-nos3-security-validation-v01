# Original Portuguese evidence archive plan

The Portuguese N0-R1, N1-A, and N1-A-R2 files are immutable historical source evidence. EN-R1 does not copy, rename, relocate, redact, or otherwise migrate them.

A future, separately authorized migration may populate `archive/original-pt/` by copying the 27 source artifacts byte-for-byte while preserving their original relative paths. Each copy must be accepted only when its SHA-256 equals the source SHA-256 recorded in `evidence/historical-source-map.json`. The three governance JSON snapshots must remain machine-readable originals, never translated replacements.

This directory currently contains only this plan. It does not contain migrated evidence.

## Disclosure control

Historical artifacts containing an absolute personal filesystem path are evidence-valid but are not approved for automatic public disclosure. Their English counterparts and explanatory views use `<REDACTED_LOCAL_WORKSPACE>` or omit the path. A later publication operator must either keep the byte-identical originals outside the public repository or obtain an explicit disclosure decision; redacted derivatives must never be represented as the originals.

No archive population, Git commit, remote publication, or repository migration is authorized by EN-R1.

