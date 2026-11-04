# N0 — NOS3 Architecture

## Static view

NOS3 is documented as a development, integration/test, and simulated-operations suite. The default topology uses containers and Docker networks; spacecraft group flight software and component simulators, while central services may be shared. Ground software sends commands and receives telemetry. NOS Engine connects FSW to hardware models, while 42 provides dynamics and environmental data.

```text
Operator / GSW
    | CCSDS over debug or radio UDP links
    v
CI/TO in FSW (cFS default; F´ selectable)
    | HWLIB and bus APIs
    v
NOS Engine <---- NOS Time Driver
    | I2C / SPI / CAN / UART / discrete connections
    v
Hardware models <---- data providers <---- 42 simulated truth
    |
    +---- out-of-band command bus (SimTerminal/UDP, simulation faulting)
```

## Inventory and classification

| Area | Documented capability (D) | Proposed extension (E) / unknown (U) |
|---|---|---|
| Isolation | Processes in containers and networks by group/spacecraft. | This does not demonstrate security isolation; policy and escape resistance are U. |
| NOS Engine | Nodes, buses, I2C/SPI/CAN/UART plug-ins, time distribution. | Audit interceptors, causal IDs, and independent capture are E. |
| FSW | cFS default, Linux OSAL, modified PSP, HWLIB, CI/TO, heritage apps. | End-to-end authorization semantics are U. |
| F´ | Selectable as FSW/GSW, component Base IDs, dedicated submodule. | Upstream calls portions proof-of-concept/unmaintained; parity is U. |
| Hardware models | Generic C++/Boost components and provider-decoupled data. | Hardware fidelity and fault coverage are U. |
| Dynamics | 42 supplies position, attitude, vectors, environment; NOS Engine drives time. | Truth authenticity and controlled adversarial perturbation are E. |
| Ground | COSMOS 4/5, YAMCS, F´ GDS, and AIT; CI/TO UDP is not for flight operations. | Operator identity and uniform policy across GSWs are U. |
| Command/TLM | CCSDS secondary headers, debug/radio paths, TO telemetry filtering. | Command–authorization–dispatch–effect correlation is not a documented primitive. |
| Lifecycle | launch/stop/clean and XML configuration. | Mid-transaction restart, deterministic recovery, and quiescence are U. |
| Faults | Simulator backdoors through NOS Terminal/UDP and cited NOS Engine fault injection. | Catalog, atomicity, reproducibility, and coverage require implementation/testing. |

N0 found no separately fixed upper reference for NOS Engine implementation in `.gitmodules`; its effective version and provenance remained U.

## Security-relevant flows

In cFS, CI ingests CCSDS commands over UDP and TO emits telemetry. Direct debug and radio paths exist; the radio TO path starts closed and is enabled by command. `to_config.c` filters telemetry. Missing GSW telemetry may therefore mean filtering, loss, delay, or no event—it does not prove absence of effect.

HWLIB selects real or simulated interfaces at build time. Simulated-model callbacks respond to NOS Engine messages, and models may consume 42 truth data. Simulator command connections are out of band and differ from real hardware buses.

NOS Time Driver distributes ticks. A local bus/process order does not establish global causality; future work needs simulated ticks, monotonic clocks, sequence counters, and causal identifiers.

Documentation describes preparation, build, launch, stop, clean, and Igniter control, but no guarantee was found for consistent checkpointing, exactly-once restart behavior, log flushing, or transactional recovery.

## Extension surfaces and limits

XML selects simulators, libraries, connections, and providers. `SimIHardwareModel::command_callback` accepts out-of-band control. Models/providers are extensible, and GSW dictionaries and FSW tables expand command/telemetry surfaces. Conflicting documentation about current versus future bus-fault capabilities requires version-specific implementation verification.

This analysis did not inspect all 47 submodules, generated code, images, binaries, effective configurations, or runtime behavior. No security property is inferred from architecture.

## Fixed references

- [Architecture](https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/docs/wiki/NOS3_Architecture.md)
- [Simulators](https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/docs/wiki/NOS3_Simulators.md)
- [Ground software](https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/docs/wiki/NOS3_Ground_Software.md)
- [Components](https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/docs/wiki/NOS3_Components.md)
