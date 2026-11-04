# N1-A — Provenance Evidence Model

This model defines future evidence. It does not claim that builds, images, binaries, or experiments existed in N1-A.

| Layer | Minimum evidence | Identity |
|---|---|---|
| P0 — mission | authority, phase, risk, environment, operator/process | `mission_id` + snapshot hash |
| P1 — source | repository, commit, tree OID, `.gitmodules`, recursive gitlinks | commit/tree SHA + manifest SHA-256 |
| P2 — tool | name, exact version, supplier, binary/image, parameters | executable/image SHA-256 |
| P3 — configuration | files, permitted variables, flags, redacted secrets | ordered path+SHA-256 set |
| P4 — build | subject, materials, authorized command, timestamps, result | attestation/DSSE or equivalent + hash |
| P5 — product | binaries, images, tables, SBOMs, logs | length + SHA-256 per artifact |
| P6 — experiment | scenario, input, environment, clock, oracle | unique `experiment_id` |
| P7 — witness | independent events, sequence, monotonicity, persistence | `witness_stream_id` + hash/signature |

```json
{
  "repository": "https://github.com/nasa/nos3",
  "commit": "<40-hex>",
  "tree": "<40-hex>",
  "submodule_manifest_sha256": "<64-hex>",
  "entries": [{"path": "...", "url": "...", "gitlink": "<40-hex>", "state": "VERIFIED"}],
  "recursive_complete": true
}
```

`recursive_complete` is true only after traversing every target commit’s internal manifests. It remains false.

## Experiment and witness binding

Before execution, the experiment identity must bind the authorizing snapshot, source manifest, independent SBOMs, tool/config/image/binary hashes, scenario inputs, and witness identity/configuration. A recommended form is `nos3:<phase>:<UTC>:<digest-prefix>` over a declared canonical serialization.

Witness events minimally include:

```text
experiment_id, witness_stream_id, sequence, monotonic_time,
wall_time, source, event_type, subject_digest, payload_digest,
previous_event_digest, policy_decision
```

The witness stays outside the system-under-test write boundary. Sequence loss, clock regression, chain break, or experiment-ID mismatch fails closed.

## Integrity and custody

SHA-256 is the minimum for preserved bytes; absence is never hashed as evidence. Store read-only/content-addressed artifacts when authorized. Copies record source, destination, actor/process, time, size, and before/after hashes. Redaction creates a separately hashed derivative. Unsourced timestamps are informative only. in-toto/DSSE/SLSA remain `PROPOSED`.

| State | Condition |
|---|---|
| `VERIFIED` | authorized bytes/object and reproducible identity readback |
| `PARTIAL` | valid evidence with a missing mandatory link |
| `UNAVAILABLE` | required read did not occur or return content |
| `BLOCKED` | mandatory gate cannot close |
| `INVALID` | hash, signature, identity, or chain diverges |

No aggregation promotes a non-verified state by inference or majority.
