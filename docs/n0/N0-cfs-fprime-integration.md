# N0 — cFS and F´ Integration

## Documented cFS integration

cFS is the default NOS3 flight software. The documented integration combines OSAL, a modified Linux PSP whose main tick is replaced by the NOS Engine ticker, HWLIB real/simulated I/O selection, CI/TO CCSDS/UDP command and telemetry, SC stored commands, and apps including SCH, DS, FM, LC, and CF.

These provide observation points but do not make `CI accepted`, `software bus delivered`, `device write occurred`, and `physical/simulated effect completed` equivalent.

## Documented F´ integration

NOS3 exposes F´ as a configurable FSW and GSW and declares `fsw/fprime/fprime-nos3`. Components document F´ Base IDs. Upstream documentation calls the F´ GDS proof-of-concept/unmaintained while release 1.7.5 records F´ startup improvements. Therefore:

- **D:** an F´ integration/configuration path exists;
- **D:** recent development was reported;
- **U:** effective maintenance, coverage, and parity at the fixed revision;
- **U:** equivalence of cFS and F´ command/telemetry events.

Current official cFS context describes its demo bundle as composed of cFE, OSAL, and PSP and not flight-ready or fully system-verified. Current F´ context describes components, ports, topologies, deployments, execution models, and command dispatch with sequence numbers, pending commands, status, and possible queue drops. These concepts support proposed observation points but do not identify the fixed `fprime-nos3` version or prove cFS/F´ equivalence.

## Future comparison contract

| Logical event | Proposed cFS adapter | Proposed F´ adapter | Rule |
|---|---|---|---|
| Received | CI/CCSDS ingress | GDS/dispatcher ingress | Record bytes and origin before mutable parsing. |
| Authorized | CryptoLib/policy decision, if configured | equivalent component/policy | Never infer authorization from CRC or successful decode. |
| Dispatched | Software Bus publication/consumption | port/handler invocation | Preserve causal ID across translation. |
| Effect requested | HWLIB call | component/driver command | Record target, parameters, and authority generation. |
| Effect observed | model/provider/42 state | same simulated domain | An observer outside the executor accounts for it. |
| Telemetry | TO/DS/event services | channels/events | Mark source, filter, and possible loss. |

Canonical envelope:

`{experiment_id, command_id, authority_id, attempt_id, effect_id, phase, sim_tick, monotonic_time, source, payload_digest, outcome}`

## Comparison risks

- IDs, queues, threads, and retries have different semantics.
- GSW configuration and packet dictionaries may diverge.
- Unequal instrumentation depth creates bias.
- Startup/restart may restore different states.
- Shared hardware models may mask FSW differences.

Mutable official cFS/F´ documentation was observed on 2026-11-04 and is conceptual context, not a frozen NOS3 dependency identity.

## References retained from the historical baseline

- [NOS3 flight software](https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/docs/wiki/NOS3_Flight_Software.md)
- [NOS3 ground software](https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/docs/wiki/NOS3_Ground_Software.md)
- [NOS3 components](https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/docs/wiki/NOS3_Components.md)
- [NOS3 release v1_07_05](https://github.com/nasa/nos3/releases/tag/v1_07_05)
- [NASA cFS](https://github.com/nasa/cFS)
- [F´ overview](https://fprime.jpl.nasa.gov/overview/powerful-swa/)
- [F´ command dispatch](https://fprime.jpl.nasa.gov/devel/docs/reference/system-functional/command-dispatch/)
