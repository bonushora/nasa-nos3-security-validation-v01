# N0 — Independent Effect Witness

## Objective

The proposed witness answers which intent and authority caused which effect, how many times it occurred, and what remained after failure/restart. N0 did not implement or execute it.

```text
Tap A: command receipt / authorization --------+
Tap B: dispatch / HWLIB write ----------------+--> witness collector --> append-only journal
Tap C: model / 42 / sensor change ------------+          |                     |
Tap D: telemetry and logs --------------------+          v                     v
                                                   correlator              checkpoints
                                                       |
                                                       v
                                                 reconciliation
```

The witness must use a process and storage distinct from the sender/handler and must have no path for sending FSW or simulator command-bus messages. Sharing a host remains a documented common-mode weakness; stronger independence requires separate host, credential, clock, and storage.

## Minimum records

- Identity: `experiment_id`, `command_id`, `intent_id`, `attempt_id`, `boot_epoch`.
- Authority: pseudonymized `authority_id`, policy/version, scope, validity, decision.
- Effect: `effect_id`, type, target, before/after state or measurement, expected/observed count.
- Time: simulation tick, monotonic timestamp, source, uncertainty.
- Provenance: configuration, executable/image, and SBOM-bundle digests.
- Evidence: tap source, payload digest, sequence, and producer signature/MAC when available.

## Accounting, persistence, and recovery

The correlator maintains `RECEIVED`, `AUTHORIZED`, `DISPATCHED`, `OBSERVED`, and `RECONCILED` states per `intent_id`. Retries get new `attempt_id` values but no new effect budget. Duplicate witness events are idempotent by event key; repeated effects are counted rather than silently deduplicated.

Requirements: append-only hash-chained journal, monotonic sequence, periodic checkpoints, new `boot_epoch` on restart, idempotent replay, and reconciliation against observed state. Gaps, truncation, or head mismatch produce `EVIDENCE_INCOMPLETE`.

## Independent evidence priority

1. Model-state change captured through a separate read-only interface.
2. Redundant provider/sensor derived from a different source.
3. Traffic capture at another hop.
4. Telemetry and logs as supporting evidence.

Two logs from one process, or telemetry directly derived from the handler counter, are not two independent witnesses.

## Witness security and limits

Use read-only least privilege, no operational command key, versioned canonical format, cryptographic hashes, secret redaction, bounded retention, measured backpressure, heartbeat, drop counter, and separate health state. The witness may still alter timing, lose events, share kernel/network/clock failures, or trust a compromised source. Simulated effects do not demonstrate real physical effects.

Future phases W0–W3 progress from offline synthetic vectors to read-only fixtures, contained NOS3 integration, and stronger independence/adversarial evaluation. Each requires separate authority.
