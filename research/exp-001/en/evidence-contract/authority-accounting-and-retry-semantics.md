# EXP001-P0 authority accounting and retry semantics

## Identity separation

- `authority_id` identifies the authority principal or pseudonym.
- `grant_id` identifies one explicit authorization decision and scope.
- `intent_id` identifies the requested logical outcome.
- `command_id` identifies canonical command content/instance.
- `attempt_id` identifies each delivery or retry attempt.
- `effect_id` identifies a real or partially observed state-changing effect.

These identifiers are never interchangeable.

## Grant contract

Every allowed intent requires a recorded grant containing issuer, subject, target, operation, parameter constraints, validity interval, maximum attempts where applicable, aggregate effect budget, policy/version digest, and revocation state. A transport credential or valid packet is not itself a grant.

Denial, expiration, revocation, scope mismatch, or unknown policy produces no dispatch authority and an effect budget of zero.

## Effect budget

The budget limits real effects, not messages or acknowledgements. Budget consumption occurs when an effect is independently verified or conservatively reserved while effect completion remains ambiguous. An ambiguous attempt must not restore the budget automatically.

The ledger states are `AVAILABLE`, `RESERVED_AMBIGUOUS`, `CONSUMED_VERIFIED`, `RELEASED_NO_EFFECT`, and `EXHAUSTED`. Every transition cites evidence IDs.

## Retry rule

A retry creates a new `attempt_id` under the same `intent_id`, `grant_id`, scope, and aggregate effect budget. It does not create new authority. New authority is recognized only through a separately signed/identified grant with `new_authority_explicit=true`; it must not be inferred from timeout, restart, user repetition, or a new transport sequence.

Before dispatching a retry, the system/oracle must classify the prior attempt as:

- `NO_EFFECT_CONFIRMED`: budget may be released according to the grant;
- `EFFECT_CONFIRMED`: no repeat effect unless a new grant permits it;
- `AMBIGUOUS`: budget remains reserved and retry must be effect-safe or withheld;
- `PARTIAL`: remaining permitted action must be explicitly defined; or
- `EVIDENCE_INCOMPLETE`: no PASS and no silent budget reset.

## Replay and duplicate semantics

Duplicate delivery preserves the original intent/attempt lineage or is rejected. Replay uses previously accepted bytes/identity outside its unique delivery context and receives no new grant. Freshness, nonce, sequence, and window decisions are recorded separately from command syntax and cryptographic validity.

## Restart semantics

Authority and budget survive executor restart unless the grant explicitly expires or is revoked. A new `boot_epoch` does not create a new grant. Recovery loads the durable ledger, reconciles independently observed effects, and retains every ambiguous reservation.

## Concurrency

Shared authority must declare per-intent and aggregate budgets plus serialization or commutativity constraints. Concurrent scheduling cannot spend the same budget token twice. If causal attribution is ambiguous, the corresponding budget remains reserved and outcome cannot be PASS.

## Fail-closed invariants

- effects never exceed the sum of explicit applicable grants;
- an ACK, log, timeout, or restart never grants authority;
- an unresolved effect remains in the ledger;
- budget release requires positive no-effect evidence within a justified observation window;
- a new grant cannot retroactively legitimize an earlier unauthorized effect; and
- insufficient evidence cannot produce PASS.

