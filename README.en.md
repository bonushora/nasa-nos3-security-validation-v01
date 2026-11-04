# SSSVL — NASA NOS3 Security Validation Research

[Português do Brasil](README.pt-BR.md) · [Bilingual index](README.md)

SSSVL (Space Systems Security Validation Lab) is an independent research program developing reproducible methods for validating security-relevant effects in simulated space-software systems. This repository contains the documentary baseline and the bilingual EXP001-P0 scientific protocol for `NASA-NOS3-SECURITY-VALIDATION-v0.1`.

> **This is an independent research initiative and is not affiliated with, sponsored by, or endorsed by NASA.**

NASA NOS3, NASA cFS, and F´ are distinct research subjects. Their use or citation does not establish endorsement, operational readiness, security qualification, or flight suitability.

## Current status

```text
PUB_R1_PUBLICATION_GREEN=PASS
EXP001_P0_DOCUMENTATION_GREEN=PASS
BILINGUAL_PUBLICATION_GREEN=PASS
NOS3_TRANSITIVE_PROVENANCE=BLOCKED
NOS3_EXECUTION=NOT_AUTHORIZED
ADVERSARIAL_EXPERIMENTS=NOT_EXECUTED
EXPERIMENTAL_SECURITY=NOT_QUALIFIED
```

PUB-R1 has already published the validated English documentary baseline at commit `778eadc9e9c091657370ba01322ac0ddf7585f2d`. Historical EN-R1 files retain their original authorization and publication statements as sealed evidence. The status above describes the current PUB-R2 bilingual candidate and does not rewrite those historical records.

## EXP001-P0

**Independent Verification of Command Effects Under Retry and Recovery in Simulated Space Systems** is a scientific experimental protocol, not a report of executed experiments.

The central hypothesis is that command authorization, command dispatch, effect completion, and independent effect verification are different states. An acknowledgement or executor log does not necessarily prove that an effect occurred, and a missing acknowledgement does not prove that no effect occurred.

EXP001-P0 provides:

- H1–H8 testable and null hypotheses;
- S01–S10 synthetic fault scenarios;
- an Independent Effect Witness contract;
- canonical command, authority, attempt, and effect semantics;
- deterministic oracles and PASS/FAIL/INCONCLUSIVE/ABORTED rules;
- evidence provenance, custody, isolation, and reproducibility requirements; and
- documentary and physical-readiness acceptance gates.

The independent witness is proposed and contractually specified, but it has not been implemented or calibrated. No NOS3, cFS, F´, container, simulator, or adversarial experiment was executed.

## Protocol navigation

- [EXP001-P0 bilingual index](research/exp-001/README.md)
- [Scientific protocol](research/exp-001/en/protocol/EXP001-P0-scientific-protocol-v0.1.md)
- [Hypotheses](research/exp-001/en/protocol/hypotheses-and-null-hypotheses.md)
- [Synthetic scenarios](research/exp-001/en/protocol/synthetic-fault-scenarios.md)
- [Independent Effect Witness](research/exp-001/en/evidence-contract/independent-effect-witness-contract.md)
- [Canonical event schema](research/exp-001/en/evidence-contract/canonical-command-effect-event-schema.json)
- [Deterministic oracles](research/exp-001/en/protocol/deterministic-oracles.md)
- [Readiness matrix](research/exp-001/en/acceptance/experimental-readiness-matrix.md)
- [Bilingual equivalence review](research/exp-001/publication/equivalence-matrix.en.md)
- [Public disclosure review](research/exp-001/publication/disclosure-review.en.md)

## Evidence and limitations

The fixed upper NOS3 reference remains commit `5a3bdee6be9a2c67fdf994ae6db56d5c60395302`. Its transitive dependency graph is not completely frozen: 44 candidate gitlink values remain `PARTIAL`, three declared entries remain `UNAVAILABLE`, and recursive provenance is blocked.

Consequently, physical experiment readiness is blocked. Documentary PASS does not establish a security property, vulnerability, exactly-once behavior, operational authorization, flight qualification, or certification.

## Repository history

The existing `docs/`, `governance/`, `evidence/`, and `archive/` paths are the previously published English documentary baseline. PUB-R2 adds bilingual scientific protocol derivatives without silently renaming or relocating the sealed historical material.

All NASA, NOS3, cFS, F´, CCSDS, and third-party names remain the property of their respective owners and identify research subjects or sources only.

