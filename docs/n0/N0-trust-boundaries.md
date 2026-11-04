# N0 — Trust Boundaries and Properties

## Distinct states

| Property | Operational meaning | Future observation |
|---|---|---|
| `COMMAND_RECEIVED != COMMAND_AUTHORIZED` | Decode does not grant authority. | Capture ingress plus immutable/signed policy decision and `authority_id`. |
| `COMMAND_AUTHORIZED != COMMAND_DISPATCHED` | Authority may expire, be revoked, or fail before a handler. | Separate authorization and enqueue/dequeue events linked by `command_id`. |
| `COMMAND_DISPATCHED != EFFECT_COMPLETED` | Handler invocation does not prove state change. | Dispatcher event plus independent model/42/sensor confirmation. |
| `PAYLOAD_CRC_MATCH != AUTHENTICATED_EFFECT` | CRC does not prove identity, freshness, policy, or effect. | Record CRC, cryptographic/policy result, and effect separately. |
| `SEQUENCE_GAP != RINGBUFFER_DROP` | Gaps have multiple possible causes. | Per-hop counters, occupancy/drop metrics, boot epochs. |
| `RETRY != NEW_AUTHORITY` | Retry inherits intent/scope and does not add budget. | Stable `intent_id`, new `attempt_id`, original authority/expiry/effect budget. |
| `LOG_RECORDED != INDEPENDENT_EFFECT_VERIFIED` | Executor logs can be early, wrong, or compromised. | Separate-domain witness with append-only journal and reconciliation. |

## Architectural boundaries

1. Operator → GSW: human identity, session, intent.
2. GSW → CCSDS/UDP link: serialization, sequence, optional authentication, replay.
3. Link → CI/FSW dispatcher: parsing, authorization, routing.
4. Dispatcher → app/component: concurrency, queues, retries.
5. App → HWLIB/NOS Engine: logical-effect to I/O translation.
6. NOS Engine → model/provider/42: delivery, time, simulated state.
7. FSW/model → TO/GSW: telemetry selection, delay, loss, transformation.
8. Executor → logs: evidence controlled by the subject.
9. System → witness: observation channel without command destination.
10. Code/configuration → execution: provenance, dependencies, images.

## Canonical events

Future phases need: `experiment_id`, `boot_epoch`, `command_id`, `intent_id`, `attempt_id`, `authority_id`, `effect_id`, `phase`, `source`, `target`, `sim_tick`, `monotonic_time`, `payload_digest`, `configuration_digest`, and `outcome`.

Correlation must tolerate missing events and never fill gaps by assumption. An ACK proves only its defined stage. Telemetry derived from the executor is not independent. 42 state may confirm simulated dynamics without proving the initiating cause. Timestamp order alone is insufficient across processes.

A future property may pass only with a frozen precondition, identified stimulus, at least two observation points without total common-mode failure, deterministic oracle, time window, missing-data rule, repetitions, and intact artifacts. Otherwise the result is `INCONCLUSIVE`.
