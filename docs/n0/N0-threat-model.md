# N0 — Initial Threat Model

## Assets and objectives

Assets include command authority, command integrity/order, FSW state, simulated-effect state/count, telemetry, logs, simulated time, configuration, keys, images/binaries, and provenance. Objectives are that only valid authority produces permitted effects; every effect is causally attributable and accounted for; retries do not expand authority; recovery does not duplicate effects; and an independent witness detects divergence.

## Actors and zones

- Legitimate operator and GSW.
- Compromised or rogue GSW, with or without valid credentials.
- Compromised process, container, or component.
- Tampered dependency, submodule, or image.
- Non-malicious network, queue, scheduler, storage, or restart failure.
- Observer/witness, which may also fail and is not assumed perfect.

## Threats

| ID | Threat | Example failure | Consequence | Minimum future evidence |
|---|---|---|---|---|
| T01 | Unauthorized command | well-formed packet passes CI | improper effect | receipt, authority decision, effect |
| T02 | Replay | same command/counter returns | repeated effect | command ID, nonce/sequence, window, effect count |
| T03 | Effect duplication | retry and original complete | double actuation | attempt IDs under one intent/effect budget |
| T04 | Lost/delayed response | effect occurs without ACK/TLM | unsafe retry or false failure | clocks, ACK, model state, witness |
| T05 | Intermediate restart | crash between intent persistence and completion mark | loss/duplication | before/after journal, boot epoch, reconciliation |
| T06 | Concurrency | conflicting commands interleave | non-serializable state | phase order, locks/queues, final state |
| T07 | Accumulated authority exposure | valid credentials at multiple GSWs | lockout/authorized abuse | authority ID, scope, expiry, accumulated use |
| T08 | Logs diverge from effects | executor logs success early | false assurance | executor log versus independent state/witness |
| T09 | Telemetry manipulation | TO/table/radio/GSW alters or omits | deceived operator | independent captures, digest, sequence |
| T10 | Dependency integrity | gitlink/image/package changes | altered behavior | locks, SBOM, signature, digest, attestation |

## Assumptions explicitly rejected

NOS3 is not presumed resistant to these threats. Containers and separate buses are not treated as cryptographic boundaries. CryptoLib alone does not solve operational authorization, abuse of a valid key, exactly-once behavior, or effect authenticity. Valid CRC/CCSDS, command-success events, or coherent telemetry do not prove an authorized effect. 42 is simulated truth for models, not automatically an independent witness.

The mutable [Rogue Ground Station](https://nos3.readthedocs.io/en/latest/Scenario_Rogue_Ground_Station.html) scenario, reobserved on 2026-11-04, illustrates that channel authenticity and operational legitimacy differ; its branch-specific material is not part of the fixed N0 revision, and N0 did not execute it.

## Laboratory residual risks

Instrumentation may alter timing, IDs may collide, witness and executor may share failures, snapshots may expose secrets, scenarios may exercise only debug paths, and irreproducible configuration may invalidate comparison. These become readiness gates.
