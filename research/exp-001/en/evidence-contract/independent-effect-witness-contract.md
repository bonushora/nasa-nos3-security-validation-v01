# EXP001-P0 Independent Effect Witness contract

## Purpose

The witness establishes whether and how an effect occurred independently of command acknowledgement, telemetry, and executor-generated logs. It does not decide command authorization and must not issue commands.

## Mandatory separation

The witness must be logically separate from the executor and must not possess a command-sending credential, command-bus write path, simulator control path, or authority grant usable against the system under test. Read-only least privilege is mandatory.

Minimum acceptable separation for an initial contained fixture is a distinct process, credential, append-only journal, and capture interface. Shared host/kernel/network/clock/storage are declared common-mode risks. Stronger phases should separate host, capture path, clock source, and evidence storage.

Executor-generated logs, acknowledgements, handler counters, or telemetry derived directly from those counters are supporting evidence only. Two channels derived from the same executor fact are not independent witnesses.

## Required observations

The witness records canonical events for:

- state before the effect window;
- effect attempt visible at a non-executor boundary when available;
- state change or no-change observation with uncertainty;
- independently verified effect identity/count;
- final reconciliation against intent, authority, attempt, and budget;
- heartbeat, sequence, drop, backpressure, restart, clock, and journal health.

It must distinguish all seven canonical event types and preserve unknown/missing states rather than filling gaps.

## Evidence sources, in descending independence

1. read-only model/state interface not controlled by the command handler;
2. redundant provider/sensor derived from a distinct source;
3. capture at a separate transport or hardware-abstraction hop;
4. independently computed final-state invariant;
5. telemetry, ACKs, and executor logs as corroboration only.

The protocol must name the source actually used and its shared failure domains. “Simulated truth” is not automatically independent if the executor writes or controls it.

## Journal and continuity

The witness journal is append-only and hash chained. Each record carries producer sequence, prior-record digest, `boot_epoch`, monotonic time, simulated tick where available, and canonical payload digest. Periodic checkpoints preserve chain head and latest sequence outside the executor lifecycle.

Restart creates a new boot epoch. Recovery verifies the prior chain, preserves unresolved effects, and never discards an unmatched event. Gap, truncation, incompatible head, or unbounded loss produces `EVIDENCE_INCOMPLETE`.

## Health contract

Required health evidence includes:

- startup attestation and configuration digest;
- heartbeat interval and missed-heartbeat count;
- input/output sequence continuity;
- explicit dropped-event and backpressure counters;
- storage availability and flush/checkpoint state;
- clock source, resolution, drift estimate, and uncertainty;
- restart and shutdown markers;
- calibration result and version.

If witness health is insufficient during a decisive interval, PASS is prohibited.

## Effect accounting

The witness assigns or observes an `effect_id` that cannot be confused with `command_id` or `attempt_id`. Duplicate evidence records are deduplicated by event identity; repeated real effects remain separate and are counted. Partial or reversible state changes remain recorded as partial effects.

Each effect ends in one of: `VERIFIED_AND_RECONCILED`, `VERIFIED_UNRECONCILED`, `NOT_OBSERVED_WITH_COMPLETE_WINDOW`, `PARTIAL`, `AMBIGUOUS`, or `EVIDENCE_INCOMPLETE`.

## Failure modes and required outcome

| Witness failure | Required treatment |
|---|---|
| sequence gap/drop in decisive interval | `INCONCLUSIVE` unless independent redundant evidence closes the exact gap |
| journal/hash discontinuity | `ABORTED` or `INCONCLUSIVE` |
| command authority discovered | `ABORTED`; witness independence invalid |
| stale/derived state source | `INCONCLUSIVE` and independence claim withdrawn |
| time uncertainty exceeds oracle boundary | `INCONCLUSIVE` |
| witness changes system state | `ABORTED` |
| shared failure compromises executor and witness | `INCONCLUSIVE` or `ABORTED` |

## Implementation gate

This contract is documentary. Witness code, deployment, calibration, and containment do not exist in P0 and require separate authorization and validation.

