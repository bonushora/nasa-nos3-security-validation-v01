# EXP001-P0 experimental readiness and acceptance matrix

## Documentary acceptance

| # | Required P0 deliverable/control | Evidence | Result |
|---:|---|---|---|
| 1 | Scientific protocol v0.1 | research question, design, controls, uncertainty, procedure | PASS |
| 2 | Testable and null hypotheses | H1–H8 with observables/falsification | PASS |
| 3 | Threat model and trust boundaries | TB1–TB8, rejected assumptions, witness failures | PASS |
| 4 | Independent Effect Witness contract | separation, no command authority, health, accounting | PASS |
| 5 | Canonical command/effect schema | seven event types and required identity/evidence fields | PASS |
| 6 | Authority accounting and retry semantics | grant, intent, attempt, effect, budget, replay/restart rules | PASS |
| 7 | Synthetic fault scenarios | S01–S10 with nine required definition fields | PASS |
| 8 | Deterministic oracle requirements | state graph, invariants, uncertainty, scenario rules | PASS |
| 9 | Four-state decision rules | PASS/FAIL/INCONCLUSIVE/ABORTED | PASS |
| 10 | Provenance and reproducibility contract | P0–P7, custody, isolation, comparators | PASS |
| 11 | Readiness matrix and independent states | documentary and physical gates separated | PASS |
| 12 | BH-SDP v2.3 experimental snapshot | hashes, states, limits, next phase | PASS |

`EXP001_P0_DOCUMENTATION_GREEN=PASS` is permitted only after local file, link, JSON, identifier, scenario, and hash validation. It does not authorize execution.

## Physical experiment readiness gates

| Gate | Requirement | Current state | Reason / recovery |
|---|---|---|---|
| E1 | explicit execution authorization and stop authority | `NOT_AUTHORIZED` | new bounded mission required |
| E2 | recursively frozen NOS3 provenance | `BLOCKED` | root tree/gitlink/target recursion remains incomplete |
| E3 | approved isolated checkout/environment | `NÃO_EXECUTADO` | no installation or materialization authorized |
| E4 | toolchain/image/binary/configuration hashes | `NÃO_EXECUTADO` | requires authorized provisioning |
| E5 | synthetic credentials and non-operational endpoints | `NÃO_EXECUTADO` | fixture not provisioned |
| E6 | implemented command-incapable witness | `NÃO_EXECUTADO` | contract only |
| E7 | witness calibration and uncertainty bounds | `NÃO_EXECUTADO` | implementation prerequisite |
| E8 | deterministic oracle implementation and test vectors | `NÃO_EXECUTADO` | documentary rules only |
| E9 | containment, egress, resources, reset, cleanup | `NÃO_EXECUTADO` | environment absent |
| E10 | frozen scenario, seeds, repetitions, stopping plan | `DEFERRED` | calibrations/power justification required |
| E11 | dry run against authorized non-NOS3 fixture | `NÃO_EXECUTADO` | separate execution authority required |
| E12 | independent human preregistration review | `DEFERRED` | after E1–E10 evidence exists |

`EXP001_EXECUTION_READINESS=BLOCKED`

## Independent states

```text
EXP001_P0_DOCUMENTATION_GREEN=PASS
EXP001_EXECUTION_READINESS=BLOCKED
NOS3_TRANSITIVE_PROVENANCE=BLOCKED
NOS3_EXECUTION=NOT_AUTHORIZED
ADVERSARIAL_EXPERIMENTS=NOT_EXECUTED
EXPERIMENTAL_SECURITY=NOT_QUALIFIED
REMOTE_MUTATION=NOT_AUTHORIZED
```

## Minimum next scientific phase

Recommend `EXP001-P1 — Offline Witness and Oracle Fixture`, only under new execution authority. P1 should implement schema validation, authority ledger, witness journal, deterministic oracle, and synthetic test vectors against a non-NOS3 fixture. NOS3 contact remains prohibited until E1–E12 pass.

