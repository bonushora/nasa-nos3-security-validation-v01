# EXP001-P0 scientific research protocol v0.1

## Title

**Independent Verification of Command Effects Under Retry and Recovery in Simulated Space Systems**

## Status and authority

`EXP001_P0_DOCUMENTATION_GREEN` may become PASS after documentary validation. Physical execution remains `NOT_AUTHORIZED`.

- Program: SSSVL — Space Systems Security Validation Lab.
- Governance: BH-SEP v2.3 / BH-SDP v2.3.
- Subject reference: NASA NOS3 commit `5a3bdee6be9a2c67fdf994ae6db56d5c60395302`.
- Transitive provenance: `BLOCKED`.
- NOS3/cFS/F´/container/simulator execution: `NOT_AUTHORIZED`.
- Adversarial experiments: `NOT_EXECUTED`.
- Experimental security: `NOT_QUALIFIED`.

This protocol is an independent research design. It makes no claim that NOS3 currently violates, implements, or guarantees any proposed property.

## Research question

Can independently observed system effects be reliably distinguished from command authorization, dispatch, acknowledgements, telemetry, and executor logs under retry, replay, interruption, and recovery?

## Main hypothesis

Command authorization, dispatch, effect completion, and independent effect verification are different states. A successful acknowledgement or executor log does not necessarily establish that an effect occurred, and a missing acknowledgement does not establish that no effect occurred.

Testable hypotheses and null hypotheses are defined in [hypotheses](hypotheses-and-null-hypotheses.md).

## Scientific classification

Every protocol statement uses one of four classes:

- **D — documented:** behavior described by the fixed NOS3 documentary baseline, such as command/telemetry paths, simulator models, NOS Engine-mediated interfaces, and out-of-band simulator command paths.
- **P — proposed:** laboratory instrumentation, independent witness, event schema, fault fixture, or oracle specified here but not implemented.
- **H — hypothetical:** a security or reliability property to test, never assumed true.
- **O — observed:** a result produced by an authorized experiment. At P0 there are no O-class results.

A D-class architecture statement is not an H-class property proof. P-class instrumentation does not become O-class evidence until implemented, calibrated, healthy, and executed under a frozen experiment identity.

## Experimental unit and variables

The future experimental unit is one isolated run of one scenario against one frozen subject/configuration with a unique `experiment_id` and `run_id`.

Independent variables include scenario, retry count, replay status, interruption point, restart epoch, concurrency schedule, and deliberately controlled acknowledgement/telemetry/log faults. Dependent variables include event-state progression, independent effect count, final state, reconciliation outcome, evidence completeness, timing uncertainty, and divergence among executor, telemetry, and witness.

Controlled variables must include source identity, gitlinks, images, binaries, tool versions, XML/configuration, dictionaries, cFS/F´ tables, seed, initial state, simulated time, tick rate, resource limits, topology, authority grants, effect budgets, oracle version, and witness version.

## Comparator baselines

1. **B0 negative control:** valid transport/format but authorization denied; zero dispatch and zero effects expected.
2. **B1 nominal control:** one authorized command, one dispatch, one independently verified effect, and consistent acknowledgement/log/telemetry.
3. **B2 witness control:** synthetic known state transition delivered directly to the witness fixture without system execution; validates schema, counting, and reconciliation.
4. **B3 no-command control:** identical duration and initial state with no command; detects spontaneous or background changes.
5. **B4 instrumentation control:** same benign fixture with witness enabled/disabled where separately authorized; estimates measurement perturbation.

No cFS-versus-F´ comparison is valid until instrumentation and semantics are shown equivalent enough for the stated metric.

## Measurement model and uncertainty

Each event records simulated tick, producer-monotonic time, boot epoch, producer sequence, and uncertainty bound. Cross-process wall-clock order is not assumed causal. Causality is established through explicit identifiers and parent links; time is supporting evidence.

Before any physical run, calibration must bound timestamp resolution, capture delay, event loss, reorder window, observer backpressure, state-read granularity, and instrument-induced timing change. If an oracle depends on an ordering closer than the combined uncertainty bound, the result is `INCONCLUSIVE`.

## Repetitions and scheduling

P0 specifies no universal numeric repetition count because runtime variance has not been measured. A future preregistration must set repetitions before data collection using pilot-free power or precision justification. At minimum, each deterministic fixture must reproduce across three clean repetitions, and any stochastic schedule must use a preregistered seed set large enough to support its claimed confidence interval. Failed witness-health runs do not count as successful repetitions.

Scenario order should be randomized or counterbalanced when state carryover is possible. Every run begins from a verified reset or a deliberately declared recovery state.

## Procedure boundary

Future execution, under new authority, would:

1. verify all readiness gates and immutable experiment identity;
2. reset and attest initial state;
3. start and health-check the independent witness;
4. issue the preregistered authority grant and effect budget;
5. apply exactly one scenario stimulus schedule;
6. capture all event channels without altering outcome classification;
7. stop on abort criteria;
8. reconcile effects independently from acknowledgements/logs;
9. preserve raw evidence before analysis; and
10. evaluate the preregistered deterministic oracle.

These steps are specifications only and are not authorization to execute.

## Analysis plan

Primary outputs are state-transition conformance, effect count versus budget, unmatched dispatches/effects, duplicate effects, authority consumption, evidence completeness, and final reconciliation. Secondary outputs include latency distributions and channel disagreement, reported with measurement uncertainty.

No missing record is imputed as success. No acknowledgement or executor log is substituted for independent effect evidence. Exploratory observations must be labeled separately from preregistered hypothesis tests.

## Decision and stop rules

Run outcomes are limited to `PASS`, `FAIL`, `INCONCLUSIVE`, or `ABORTED` under the [decision rules](../acceptance/decision-rules.md). Containment escape, identity mismatch, witness unhealthiness beyond the preregistered tolerance, resource-limit breach, non-resettable state, unexpected operational endpoint, or ambiguous target requires immediate `ABORTED`.

## Related contracts

- [Threat model and trust boundaries](threat-model-and-trust-boundaries.md)
- [Synthetic fault scenarios](synthetic-fault-scenarios.md)
- [Deterministic oracles](deterministic-oracles.md)
- [Independent Effect Witness](../evidence-contract/independent-effect-witness-contract.md)
- [Authority and retry semantics](../evidence-contract/authority-accounting-and-retry-semantics.md)
- [Evidence provenance and reproducibility](../evidence-contract/evidence-provenance-and-reproducibility.md)
- [Readiness matrix](../acceptance/experimental-readiness-matrix.md)

