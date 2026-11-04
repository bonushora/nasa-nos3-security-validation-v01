# N0 — Adversarial Scenario Matrix

All scenarios are future specifications, not executions. “Expected secure outcome” is a desired laboratory oracle, not a NOS3 claim.

| ID | Future stimulus | Boundary | Observation/oracle | Expected secure outcome | N0 state |
|---|---|---|---|---|---|
| A01 | Structurally valid command without authority | received/authorized | ingress, policy, effect taps | rejection; zero effects | SPECIFIED |
| A02 | Byte-for-byte replay inside/outside window | authenticated/fresh | sequence, authority, count | no more than allowed effect; explicit replay | SPECIFIED |
| A03 | Lose ACK after effect and force retry | dispatch/effect | ACK, intent/attempt, witness | retry does not duplicate effect | SPECIFIED |
| A04 | Duplicate message at two hops | transport/dispatcher | per-hop counters, effect count | defined detection or idempotence | SPECIFIED |
| A05 | Delay response past timeout | effect/response | timestamps, independent state | timeout creates no new authority | SPECIFIED |
| A06 | Restart after persisting intent, before completion | lifecycle | journal, boot epoch, final state | deterministic recovery, no hidden effect | SPECIFIED |
| A07 | Restart after effect, before success log | effect/log | witness vs executor journal | reconciled, not repeated | SPECIFIED |
| A08 | Concurrent conflicting commands | queue/handler | causality, final state | explicit serialization policy | SPECIFIED |
| A09 | Flood from valid-key GSW | accumulated authority | per-authority use, counters, availability | limits/isolation or explicit failure | SPECIFIED |
| A10 | Forge/omit TO or radio telemetry | effect/TLM | model state vs hop captures | divergence detected | SPECIFIED |
| A11 | Sequence gap without ring-buffer drop | producer/transport | per-hop/drop counters | no unsupported attribution | SPECIFIED |
| A12 | Ring-buffer drop without visible gap | buffer/consumer | occupancy/drop, IDs | drop accounted for | SPECIFIED |
| A13 | Valid CRC, invalid MAC/policy | CRC/authentication | separate results | zero effects | SPECIFIED |
| A14 | Alter success log without state change | executor/witness | chain heads, independent state | divergence signaled | SPECIFIED |
| A15 | Swap submodule/image/configuration | provenance/execution | SBOM, gitlink, digest, attestation | refuse or mark non-comparable | SPECIFIED |
| A16 | Manipulate tick/clock | time/causality | multiple sources, monotonicity | invalid temporal evidence detected | SPECIFIED |
| A17 | Out-of-band command to model | command bus/FSW | SimTerminal tap, effects | separate origin; no FSW attribution | SPECIFIED |
| A18 | TO filter hides a true effect | effect/visibility | witness, TO table | no inference of no effect from no TLM | SPECIFIED |

Every future run must freeze commit/gitlinks, image digests, FSW/GSW, XML, dictionaries, cFS/F´ tables, synthetic keys, seed, initial time, tick rate, resources, topology, fault schedule, oracle, repetitions, timeout, and abort criteria.

Allowed outcomes are `PASS`, `FAIL`, `INCONCLUSIVE`, or `ABORTED`. Missing data, unhealthy witness, divergent provenance, or unfrozen configuration require `INCONCLUSIVE/ABORTED`.
