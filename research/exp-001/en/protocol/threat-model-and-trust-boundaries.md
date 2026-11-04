# EXP001-P0 threat model and trust boundaries

## Assets and objectives

Assets are command authority, effect budget, command/effect lineage, system state, simulated time, witness state, raw evidence, configuration, provenance, and outcome classification. The objective is reliable accounting: every observed effect is tied to permitted authority or explicitly remains unresolved; no missing or executor-only evidence becomes proof.

## Actors and failures

- legitimate operator/fixture with bounded synthetic authority;
- unauthorized or replaying sender;
- command receiver, authorizer, dispatcher, and effect executor;
- telemetry/log/acknowledgement producers;
- simulator/model state provider;
- independent witness and evidence custodian;
- non-malicious network, queue, scheduler, clock, storage, and restart failures;
- compromised or defective component, dependency, configuration, or instrument.

## Explicit trust boundaries

| Boundary | Inside | Outside / independent side | Required evidence |
|---|---|---|---|
| TB1 authority | grant issuer and policy | command transport/handler | immutable grant ID, scope, expiry, budget, decision |
| TB2 receipt/dispatch | ingress, authorizer, dispatcher | effect interface/model | separate receipt, authorization, and dispatch events |
| TB3 executor/effect | handler/driver/model mutation path | read-only state observer | before/after state, effect identity, uncertainty |
| TB4 executor/witness | executor logs and counters | witness process/credential/storage | independent capture provenance and health |
| TB5 system/telemetry | TO/event/log pipeline | independent state capture | sequence/drop/filter metadata and disagreement record |
| TB6 lifecycle | process/boot epoch | persistent evidence store | restart identity, journal continuity, recovery record |
| TB7 experiment/control | stimulus orchestrator | outcome evaluator/raw store | preregistration, immutable inputs, separated roles where feasible |
| TB8 software supply chain | source/build/image/config | experiment identity verifier | recursive provenance, hashes, SBOM/attestation |

TB8 is currently open because NOS3 transitive provenance is `BLOCKED`; therefore physical execution is not ready.

## Threats to validity

- acknowledgement or log emitted before effect completion;
- effect completed but acknowledgement, telemetry, or log lost;
- duplicate delivery, replay, retry, or recovery duplicates an effect;
- restart loses intent, completion, or authority consumption state;
- concurrent commands race over shared state or budget;
- telemetry filters or derived counters conceal disagreement;
- witness shares the executor's data source or failure domain;
- instrument loss/reordering/backpressure creates false absence;
- clocks make unrelated events appear ordered;
- reset is incomplete and carries state across repetitions;
- provenance or configuration drift makes runs incomparable;
- investigator changes oracle after observing results.

## Rejected assumptions

- exactly-once command delivery or effect semantics;
- a valid packet, CRC, MAC, or decode implies operational authorization;
- dispatch implies effect;
- acknowledgement or executor log proves effect;
- missing telemetry or acknowledgement proves no effect;
- two executor-derived channels are independent;
- simulated truth is automatically an independent witness;
- containers alone are a security boundary;
- documentary architecture is experimental evidence.

## Witness failure modes

The witness may miss, duplicate, reorder, corrupt, or delay records; share kernel/network/clock/storage failures; observe stale state; perturb timing; lose its journal; or be compromised. Health heartbeat, sequence gaps, drop counters, clock uncertainty, journal continuity, source independence, and calibration results must be evidence. A witness failure affecting the oracle produces `INCONCLUSIVE` or `ABORTED`, not PASS.

## Scope exclusions

P0 does not test flight hardware, operational networks, real credentials, radiation/physical effects, cryptographic algorithm strength, or cybersecurity certification. It does not assert a NOS3 vulnerability.

