# EXP001-P0 synthetic fault-scenario specification

All scenarios are P-class specifications. No scenario has been executed, and none asserts existing NOS3 nonconformance. Inputs, authority grants, state changes, and faults must be synthetic and non-operational.

## S01 — Successful single command and verified single effect

- **Preconditions:** attested clean initial state; healthy witness; no background command; one deterministic target.
- **Authority/effect budget:** grant G1 permits one intent and exactly one target effect; one initial attempt.
- **Stimulus:** submit one valid authorized command without injected fault.
- **Expected observations:** all seven canonical states occur once in causal order; acknowledgement/log/telemetry are consistent supporting channels.
- **Witness requirements:** independent before/after state capture, effect count, health, and causal binding.
- **Failure/ambiguity:** zero or multiple effects, missing required event, unhealthy witness, or final-state uncertainty.
- **Deterministic oracle:** one authorized intent, one dispatch lineage, one independently verified effect, reconciled budget 1/1.
- **Acceptance:** PASS only when the complete oracle and evidence-health gates hold; otherwise FAIL, INCONCLUSIVE, or ABORTED per cause.
- **Reproducibility:** frozen identities, seed, initial state, grant, command bytes, timing schedule, and at least three clean deterministic repetitions.

## S02 — Command rejected before dispatch

- **Preconditions:** clean state; healthy witness; synthetic command structurally valid but outside grant scope or with explicit deny policy.
- **Authority/effect budget:** grant G2 permits zero effects for this command/target.
- **Stimulus:** submit the denied command once.
- **Expected observations:** `COMMAND_RECEIVED` and negative `COMMAND_AUTHORIZED`; no dispatch, attempt, observed effect, or state change.
- **Witness requirements:** independent no-change observation for the full oracle window plus health/drop evidence.
- **Failure/ambiguity:** dispatch/effect occurs, authorization record absent, background state changes overlap, or observation window is incomplete.
- **Deterministic oracle:** denial decision bound to command; dispatch count 0; independently observed target delta 0; budget remains 0/0.
- **Acceptance:** PASS for correct rejection; FAIL for any attributable dispatch/effect; INCONCLUSIVE for insufficient no-change evidence.
- **Reproducibility:** fixed deny policy/version, command bytes, window duration, state tolerance, and negative-control run.

## S03 — Command dispatched without effect

- **Preconditions:** healthy witness; controlled fixture able to suppress the effect after dispatch without altering authorization.
- **Authority/effect budget:** one authorized intent; maximum one effect.
- **Stimulus:** authorize and dispatch once; inject a synthetic post-dispatch/pre-effect suppression.
- **Expected observations:** receipt, authorization, dispatch, and effect attempt; no independently observed effect; explicit failed/timeout reconciliation.
- **Witness requirements:** independent target state and sufficient window to distinguish delay from no effect.
- **Failure/ambiguity:** effect appears after the window, witness resolution cannot detect it, or suppression point is not evidenced.
- **Deterministic oracle:** dispatch count 1; attempted count 1; verified effect count 0; unresolved late possibility must be zero within justified window.
- **Acceptance:** PASS when no effect is independently established and outcome is not mislabeled success; FAIL if executor success is promoted despite contradictory state.
- **Reproducibility:** fixed suppression hook, timing window, target tolerance, initial state, and repetitions.

## S04 — Effect completed but acknowledgement lost

- **Preconditions:** nominal command path and independent state capture; controlled ACK-drop fixture after effect.
- **Authority/effect budget:** one authorized intent, exactly one permitted effect; retry initially disabled.
- **Stimulus:** execute nominal command and drop acknowledgement after effect completion.
- **Expected observations:** all effect states through independent verification; acknowledgement absent; reconciliation records effect despite missing ACK.
- **Witness requirements:** effect evidence independent of acknowledgement, executor log, and telemetry transport.
- **Failure/ambiguity:** ACK is dropped before the specified point, effect state is stale, or witness cannot establish completion.
- **Deterministic oracle:** verified effect count 1 and ACK count 0 under the same intent; budget consumed 1/1.
- **Acceptance:** PASS only if missing ACK is not interpreted as no effect; FAIL if outcome permits a fresh effect budget automatically.
- **Reproducibility:** exact ACK-drop point, causal marker, timeout, and independent state snapshot preserved.

## S05 — Retry after ambiguous completion

- **Preconditions:** S04-compatible fixture; first attempt may complete while its response is lost; retry policy preregistered.
- **Authority/effect budget:** one intent with aggregate effect budget 1 across attempts A1 and A2 unless explicit new grant is issued.
- **Stimulus:** lose first response, then submit a retry with the same intent and a new `attempt_id`.
- **Expected observations:** both attempts retain G5 scope; reconciliation prevents or detects a second effect; ambiguity remains explicit until independent state resolves it.
- **Witness requirements:** durable effect identity/count across retries and boot epochs; no executor-only deduplication proof.
- **Failure/ambiguity:** attempts cannot be linked, first effect cannot be resolved, or final count exceeds measurement precision.
- **Deterministic oracle:** total independently verified effects for the intent must not exceed 1; any second effect without new grant is FAIL.
- **Acceptance:** PASS for one accounted effect or a safely suppressed retry with reconciliation; INCONCLUSIVE when the count remains ambiguous.
- **Reproducibility:** retry timeout, idempotency key, attempt lineage, schedule, grant, and final-state capture fixed.

## S06 — Duplicate delivery and replay

- **Preconditions:** clean state; fixture can duplicate transport delivery and later replay identical bytes; freshness policy fixed.
- **Authority/effect budget:** one original intent, aggregate effect budget 1; duplicates/replays receive no new authority.
- **Stimulus:** deliver the same command twice at a controlled hop, then replay it inside or outside the declared freshness window.
- **Expected observations:** duplicate/replay classification, preserved original identity, explicit rejection or idempotent handling, no unbudgeted effect.
- **Witness requirements:** command-byte digest, per-hop sequences, freshness evidence, and independent effect count.
- **Failure/ambiguity:** duplicate source/hop unknown, replay window uncertain, or bytes map to a new intent without explicit grant.
- **Deterministic oracle:** one authority grant and effect budget; total verified effects ≤1; every extra delivery accounted as duplicate/replay.
- **Acceptance:** FAIL for any ungranted second effect; PASS for correct classification/accounting; INCONCLUSIVE for incomplete hop evidence.
- **Reproducibility:** exact duplication hop, count, delay, replay window, bytes, and seed recorded.

## S07 — Restart before effect completion

- **Preconditions:** persistent witness journal; controlled restart point after authorization/dispatch but before independently observed effect.
- **Authority/effect budget:** one intent, aggregate budget 1 across boot epochs.
- **Stimulus:** restart the executor/system at the preregistered pre-effect boundary, then allow recovery.
- **Expected observations:** new `boot_epoch`, preserved or explicitly abandoned intent, no hidden effect, and deterministic reconciliation.
- **Witness requirements:** journal continuity independent of executor restart, before/after state, restart marker, and gap accounting.
- **Failure/ambiguity:** restart boundary not evidenced, state changes during blind interval, or recovery loses authority ledger.
- **Deterministic oracle:** final verified effect count is either 0 with explicit cancellation or 1 with preserved original grant; never unaccounted.
- **Acceptance:** PASS for deterministic reconciled recovery; FAIL for duplicate/ungranted effect; INCONCLUSIVE for blind-interval ambiguity.
- **Reproducibility:** restart trigger, boundary marker, persistence configuration, recovery timeout, and initial state fixed.

## S08 — Restart after effect but before success logging

- **Preconditions:** controlled post-effect/pre-log restart hook; persistent independent witness and authority ledger.
- **Authority/effect budget:** one intent, one total effect across restarts.
- **Stimulus:** complete the effect, capture it independently, then restart before executor success log/ACK persistence.
- **Expected observations:** effect verified in the earlier epoch, missing success log, new epoch recovery reconciles rather than repeating effect.
- **Witness requirements:** pre-restart independent effect record durably available after restart, with chain continuity.
- **Failure/ambiguity:** effect timing relative to restart uncertain, journal not durable, or target state is reversible without trace.
- **Deterministic oracle:** effect count remains exactly 1; recovery records completed/reconciled status and consumes no new budget.
- **Acceptance:** FAIL if recovery repeats the effect without new authority; PASS for one reconciled effect; INCONCLUSIVE for continuity failure.
- **Reproducibility:** hook position, persistence flush policy, restart epoch, final state, and recovery schedule preserved.

## S09 — Concurrent commands with shared authority

- **Preconditions:** two distinguishable intents target shared state; declared serialization/commutativity rule; deterministic scheduler fixture or recorded seed.
- **Authority/effect budget:** one shared grant with explicit per-intent and aggregate limits; no implicit borrowing.
- **Stimulus:** release both commands according to a preregistered concurrent schedule.
- **Expected observations:** separate intent/attempt lineage, declared ordering or commutative result, complete budget ledger, independently verified final state.
- **Witness requirements:** causal identifiers, state transitions at sufficient granularity, scheduler evidence, and no command authority.
- **Failure/ambiguity:** intermediate effects cannot be resolved, schedule differs from preregistration, or final state admits multiple unmatched histories.
- **Deterministic oracle:** observed effect multiset and final state equal one allowed serialized/commutative outcome and stay within aggregate budget.
- **Acceptance:** PASS for one allowed fully attributed outcome; FAIL for lost/duplicate/unbudgeted effect; INCONCLUSIVE for causal ambiguity.
- **Reproducibility:** release barrier, seed, scheduler policy, target initial state, authority split, and repetitions recorded.

## S10 — Telemetry or executor log inconsistent with independent state

- **Preconditions:** healthy independent state observer; fixture can omit, delay, or falsify only the supporting telemetry/log channel.
- **Authority/effect budget:** scenario declares either one permitted effect or zero-effect negative control.
- **Stimulus:** execute the declared command outcome while making telemetry or executor log report the opposite outcome.
- **Expected observations:** independent state and supporting channel disagree; divergence is explicit and not silently resolved in favor of executor output.
- **Witness requirements:** source-independent effect evidence, channel provenance, sequence/drop/filter metadata, and health.
- **Failure/ambiguity:** witness derives from the manipulated channel, state observation is stale, or manipulation affects the actual effect path.
- **Deterministic oracle:** outcome follows independently verified state; inconsistent channel is marked contradictory supporting evidence.
- **Acceptance:** PASS when divergence is detected and classified; FAIL when false supporting evidence is promoted to effect proof; INCONCLUSIVE when independence fails.
- **Reproducibility:** manipulated channel, transformation, timing, target state, expected contradiction, and negative control fixed.

## Global scenario constraints

Every scenario must use the canonical event schema, immutable experiment identity, synthetic authority, explicit effect budget, calibrated witness, preregistered oracle, raw evidence preservation, and the four-state decision system. Insufficient evidence never becomes PASS.

