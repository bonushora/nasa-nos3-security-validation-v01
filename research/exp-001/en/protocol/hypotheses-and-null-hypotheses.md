# EXP001-P0 hypotheses and null hypotheses

All hypotheses concern future controlled observations. None describes a demonstrated NOS3 property.

| ID | Testable hypothesis | Null hypothesis | Primary observable | Falsification / rejection rule |
|---|---|---|---|---|
| H1 | Command receipt, authorization, dispatch, effect observation, independent verification, and reconciliation are distinguishable states. | H1₀: these states cannot be distinguished reliably in the captured evidence. | complete event-state path per `intent_id` | Reject H1 if required states cannot be separately attributed within the evidence contract. |
| H2 | Acknowledgement or executor success logging is insufficient by itself to prove effect completion. | H2₀: acknowledgement/log success always agrees with independently verified effect completion. | ACK/log versus independent effect state | Reject H2 only if preregistered fault cases never produce disagreement and the study has sufficient coverage; a single sound disagreement supports H2. |
| H3 | Missing acknowledgement is insufficient by itself to prove absence of effect. | H3₀: every missing acknowledgement corresponds to no independently verified effect. | lost-ACK scenario effect count | A verified effect with missing ACK rejects H3₀. |
| H4 | Retries can be accounted for under one original authority scope and effect budget without silently creating new authority. | H4₀: retry accounting cannot distinguish attempts or constrain aggregate effect budget. | authority grant, attempt IDs, budget consumption | Reject H4 when any retry lacks lineage or aggregate effects exceed the grant without an explicit new grant. |
| H5 | Recovery reconciliation can distinguish pre-effect interruption from post-effect/pre-log interruption when evidence remains complete. | H5₀: the two interruption positions are observationally indistinguishable. | boot epochs, journal, final independent state | Reject H5 when the oracle cannot distinguish positions within declared uncertainty and evidence health. |
| H6 | A logically separate, command-incapable witness can detect disagreement between executor/log/telemetry and independent state. | H6₀: the witness provides no additional discriminating evidence beyond executor-generated channels. | divergence detection rate and false-positive control | Reject H6 if witness output is derived from the executor channel or fails negative controls. |
| H7 | Duplicate delivery and replay can be distinguished from an authorized new command using intent, attempt, freshness, and authority identifiers. | H7₀: duplicate/replay and new authorized intent are indistinguishable. | identity lineage and replay decision | Reject H7 if replayed bytes can consume a new effect budget without explicit authorization. |
| H8 | Concurrent commands sharing an authority can be reconciled against a declared serialization and aggregate budget. | H8₀: concurrent effects cannot be causally attributed or budgeted. | causal graph, schedule, final state, budget ledger | Reject H8 if two valid executions produce an unaccounted or non-deterministically classified final effect. |

## Statistical and logical treatment

H2 and H3 are primarily counterexample hypotheses: a single valid, independently verified disagreement refutes the respective universal null statement. H1, H4–H8 require predefined completeness and repeatability thresholds before execution; P0 does not invent thresholds without calibration data.

Multiple comparisons, confidence levels, effect sizes, and any stopping boundary must be preregistered before collecting subject data. An underpowered or evidence-incomplete run is `INCONCLUSIVE`, never support by absence of observed failure.

