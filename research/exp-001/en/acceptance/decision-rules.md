# EXP001-P0 decision rules

## Outcome vocabulary

Only four run outcomes are permitted:

### PASS

All preregistered scenario invariants hold; authority/effect accounting is complete; independent evidence is healthy and sufficient; provenance and configuration match; no abort condition occurred; and every effect is reconciled. PASS applies only to the tested hypothesis, subject identity, configuration, and evidence window.

### FAIL

Complete, healthy, attributable evidence demonstrates violation of a preregistered invariant—for example an ungranted effect, effect count above budget, recovery duplicate, undetected contradiction, or incorrect deterministic classification. FAIL is not used for missing evidence or inability to execute.

### INCONCLUSIVE

The run remained contained, but evidence cannot decide the oracle: witness gap, excessive uncertainty, ambiguous effect, incomplete observation window, unresolved causal attribution, insufficient repetitions, or comparator invalidity. Insufficient evidence is always INCONCLUSIVE, never PASS.

### ABORTED

The run must stop or is invalidated by containment escape, identity/provenance mismatch, unexpected operational endpoint, witness command authority, non-resettable state, resource-limit breach, unapproved deviation, or loss of stop control. No PASS/FAIL security conclusion may be drawn from an aborted run.

## Evaluation precedence

1. Validate authorization, subject identity, provenance, containment, and stop-control prerequisites. Failure yields `ABORTED` or no run.
2. Validate schema, custody, witness health, calibration, completeness, and uncertainty. Decisive insufficiency yields `INCONCLUSIVE`.
3. Evaluate deterministic invariants. Demonstrated violation yields `FAIL`.
4. Confirm every required positive and negative criterion plus repetitions. Only then yield `PASS`.

Outcome precedence is not used to hide a demonstrated invariant violation behind unrelated missing supporting telemetry. The rule trace records each finding; the final classification follows the preregistered policy for decisive evidence.

## Universal PASS requirements

- exact experiment identity and authorized scenario;
- synthetic, scoped authority and explicit effect budget;
- complete causal identifiers for every attempt/effect;
- healthy command-incapable independent witness;
- calibrated observation window and uncertainty;
- raw evidence sealed before oracle evaluation;
- deterministic oracle/rule trace reproduced;
- negative control and reset proof valid;
- required repetitions satisfied; and
- no unresolved or partially observed effect omitted from the ledger.

## Universal FAIL conditions

- verified effect without applicable grant;
- verified effects exceed aggregate budget;
- denied command produces attributable dispatch/effect;
- retry/replay creates unauthorized additional effect;
- restart duplicates or hides an effect under complete evidence;
- executor-only evidence is accepted as independent proof contrary to the oracle;
- a required contradiction is not surfaced despite healthy independent evidence; or
- final state/effect multiset violates the preregistered allowed set.

## Study-level interpretation

A scenario PASS does not establish system security, exactly-once semantics, operational readiness, flight qualification, or behavior outside the tested configuration. A study hypothesis is supported or rejected only under its preregistered aggregation rule and uncertainty statement. “No observed failure” is not “secure.”

