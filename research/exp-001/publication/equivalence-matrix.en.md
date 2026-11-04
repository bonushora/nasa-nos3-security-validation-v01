# EXP001-P0 bilingual semantic-equivalence matrix

Status: `PASS`  
Policy: SSSVL Bilingual Publication Policy v1.0  
Scope: PUB-R2 public candidate

This matrix records the final technical comparison between the English and Brazilian Portuguese variants. It does not create experimental evidence. Exact byte identities for every pair are recorded in `source-to-translation-manifest.json`.

## Pair-level review

| Pair | Preserved content | Result |
|---|---|---|
| ROOT-README | status markers, independent-research disclaimer, limitations, navigation | PASS |
| EXP001-INDEX | protocol scope, navigation, proposed-witness status | PASS |
| EXP001-PROTOCOL | question, hypothesis, D/P/H/O classes, controls, repetitions, uncertainty | PASS |
| EXP001-HYPOTHESES | H1–H8, H1₀–H8₀, observables, falsification meaning | PASS |
| EXP001-THREATS | assets, threats, TB1–TB8, rejected assumptions, exclusions | PASS |
| EXP001-SCENARIOS | S01–S10 and all nine required fields per scenario | PASS |
| EXP001-ORACLES | state graph, invariants, scenario rules, ambiguity treatment | PASS |
| EXP001-WITNESS | logical separation, no command authority, health, failure treatment | PASS |
| EXP001-EVENT-SCHEMA | schema ID, keys, constraints, enums, seven event identifiers | PASS |
| EXP001-AUTHORITY | identifiers, grant contract, budget, retry/replay/restart rules | PASS |
| EXP001-PROVENANCE | P0–P7 evidence layers, custody, isolation, reproducibility | PASS |
| EXP001-DECISIONS | PASS / FAIL / INCONCLUSIVE / ABORTED and precedence | PASS |
| EXP001-READINESS | 12 documentary criteria, E1–E12 physical gates, independent states | PASS |
| EXP001-SNAPSHOT | normative keys/states, evidence hashes, limits, derived status | PASS |
| FUTURE-ARCHIVAL-METADATA | language, version, commit/hash/DOI fields and authorization limits | PASS |

## Identifier and meaning controls

| Control | Required equivalence | Result |
|---|---|---|
| Hypotheses | H1–H8 and their null hypotheses retain the same test and rejection semantics | PASS |
| Scenarios | S01–S10 retain preconditions, authority/effect budget, stimulus, expected observations, witness, failure/ambiguity, oracle, acceptance, and reproducibility | PASS |
| Events | `COMMAND_RECEIVED`, `COMMAND_AUTHORIZED`, `COMMAND_DISPATCHED`, `EFFECT_ATTEMPTED`, `EFFECT_OBSERVED`, `EFFECT_INDEPENDENTLY_VERIFIED`, `EFFECT_RECONCILED` are byte-identical identifiers | PASS |
| Trust boundaries | TB1–TB8 retain the same inside/outside roles and evidence requirements | PASS |
| Authority identities | `authority_id`, `grant_id`, `intent_id`, `command_id`, `attempt_id`, `effect_id`, and `boot_epoch` are unchanged | PASS |
| Ledger states | `AVAILABLE`, `RESERVED_AMBIGUOUS`, `CONSUMED_VERIFIED`, `RELEASED_NO_EFFECT`, `EXHAUSTED` are unchanged | PASS |
| Prior-attempt states | `NO_EFFECT_CONFIRMED`, `EFFECT_CONFIRMED`, `AMBIGUOUS`, `PARTIAL`, `EVIDENCE_INCOMPLETE` are unchanged | PASS |
| Oracles | Canonical state ordering, effect-budget invariants, and S01–S10 expected classifications are equivalent | PASS |
| Decisions | `PASS`, `FAIL`, `INCONCLUSIVE`, and `ABORTED` retain their definitions and precedence | PASS |
| Evidence states | `BLOCKED`, `NOT_AUTHORIZED`, `NOT_EXECUTED`, `NOT_QUALIFIED`, and BH-SDP normative values remain unchanged where schema compatibility requires them | PASS |
| Counts | 8 hypotheses, 10 scenarios, 9 scenario fields, 7 event types, 8 trust boundaries, 12 documentary criteria, 12 physical gates, and 4 decision states agree | PASS |
| Git identity | NOS3 commit `5a3bdee6be9a2c67fdf994ae6db56d5c60395302` is identical | PASS |
| Scientific limits | No execution, no adversarial result, no complete transitive provenance, no security qualification, and no NASA endorsement are equally explicit | PASS |

## Reviewed differences

The prose language and language-specific links differ by design. The Portuguese event-schema derivative translates only human-readable title and description fields. Its schema ID, field names, constraints, enumerations, and event identifiers remain unchanged. The Portuguese BH-SDP representation translates free text and adds derivation metadata; normative machine-readable states and references to the sealed English source hashes remain unchanged. These differences do not change scientific authority or evidentiary weight.

No paired artifact is `REVIEW_REQUIRED`.

