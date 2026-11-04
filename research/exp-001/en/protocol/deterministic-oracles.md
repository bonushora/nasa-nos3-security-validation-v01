# EXP001-P0 deterministic oracle requirements

## Oracle inputs

The oracle consumes an immutable event set, witness-health record, authority ledger, initial/final state, scenario specification, uncertainty model, and provenance manifest. It must not query mutable runtime state after evidence sealing.

## Canonical state graph

```text
COMMAND_RECEIVED
  -> COMMAND_AUTHORIZED(allow|deny)
  -> COMMAND_DISPATCHED
  -> EFFECT_ATTEMPTED
  -> EFFECT_OBSERVED
  -> EFFECT_INDEPENDENTLY_VERIFIED
  -> EFFECT_RECONCILED
```

An allow path may stop before any later state when a failure occurs. A deny path must not produce a causally attributable dispatch/effect. Missing intermediate evidence is not inferred from later evidence; it is marked missing.

## Determinism requirements

Given identical canonical evidence bytes, oracle version, scenario, and uncertainty parameters, evaluation must produce byte-identical normalized findings and the same outcome. Rules must be versioned, ordered, side-effect free, and independent of analyst discretion after preregistration.

The oracle must:

1. validate schema and evidence hashes;
2. reject mixed experiment/run identities;
3. build causal graphs from identifiers, not timestamps alone;
4. verify authority scope, validity, and aggregate budget;
5. count independent effects without silently deduplicating real repeats;
6. distinguish missing, contradictory, late, partial, and unhealthy evidence;
7. apply measurement uncertainty and observation windows;
8. evaluate abort conditions before PASS/FAIL;
9. emit every rule evaluation and supporting evidence IDs; and
10. leave unresolved effects in an explicit reconciliation ledger.

## Core invariants

- `verified_effects(intent) <= authorized_effect_budget(intent)` unless a separately identified new grant exists.
- Retry attempts share the original grant and aggregate budget by default.
- `COMMAND_DISPATCHED` does not imply `EFFECT_OBSERVED`.
- ACK/log/telemetry does not imply `EFFECT_INDEPENDENTLY_VERIFIED`.
- Missing ACK/log/telemetry does not imply zero effects.
- A deny decision requires zero causally attributable dispatches and effects.
- Every effect is reconciled to one grant/intent or remains explicitly `UNRESOLVED`.
- Witness unhealthiness affecting a decisive interval prohibits PASS.

## Scenario oracle summary

| Scenario | Decisive condition |
|---|---|
| S01 | exactly one verified and reconciled effect under budget 1 |
| S02 | denial, zero dispatches, zero independently observed effects |
| S03 | one dispatch/attempt, zero effects, explicit failed reconciliation |
| S04 | one verified effect with missing ACK, budget consumed once |
| S05 | all attempts linked; aggregate verified effects ≤1 |
| S06 | duplicates/replays identified; aggregate verified effects ≤1 |
| S07 | post-recovery count 0 or 1 under original grant, never hidden |
| S08 | exactly one pre-restart effect; no recovery duplicate |
| S09 | effect multiset/final state equals an allowed concurrent outcome |
| S10 | independent state governs classification; contradiction surfaced |

## Uncertainty and ambiguity

The observation window must exceed the justified maximum effect latency plus capture uncertainty. State differences smaller than calibrated resolution are ambiguous. Events whose causal ordering cannot be established within uncertainty are concurrent/unknown, not arbitrarily ordered.

Any decisive ambiguity produces `INCONCLUSIVE`; containment or identity failure produces `ABORTED`. Oracle implementation itself requires separate review and authorization.

