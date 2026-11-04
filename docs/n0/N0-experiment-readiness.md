# N0 — Future Experiment Readiness

## Decision

| Dimension | State |
|---|---|
| N0 documentary baseline | `READY` |
| Upper NOS3 reference | `FROZEN` at full commit |
| Transitive/submodule reference | `NOT_READY` |
| Executable environment | `NOT_PROVISIONED` |
| Independent witness | `DESIGNED_NOT_IMPLEMENTED` |
| Scenarios | `SPECIFIED_NOT_EXECUTED` |
| Security qualification | `NOT_QUALIFIED` |
| Operational authorization | `NOT_AUTHORIZED` |

## Mandatory gates before operational N1

- G1 — explicit phase, scope, risk, owners, and stop authority.
- G2 — isolated approved checkout; verify upper SHA and all gitlinks.
- G3 — hashes/SBOM/attestations for source, toolchain, images, binaries, configuration.
- G4 — selected threat/scenario with oracle and defined `INCONCLUSIVE`.
- G5 — synthetic data/keys only; no operational endpoint, secret, or asset.
- G6 — network/resource containment, egress policy, reset, cleanup, isolation evidence.
- G7 — implemented witness with tested health/drop counters and no command authority.
- G8 — functional/timing baseline for instrumentation perturbation.
- G9 — persistence, retention, redaction, chain-of-custody plan.
- G10 — dry run against an authorized non-NOS3 fixture or mock.
- G11 — abort on containment escape, divergent provenance, unhealthy witness, resource excess, or ambiguous target.
- G12 — human review before external claims.

## Suggested safe order

1. Transitive freeze and SBOM.
2. Offline synthetic witness vectors.
3. No-fault baseline.
4. Benign loss/delay/duplication.
5. Restart and concurrency.
6. Authority/replay/telemetry adversarial cases.
7. cFS/F´ comparison only after instrumentation parity.

The first N1 mission was recommended to resolve and record all 47 gitlinks, capture source bytes and hashes, prepare SBOM/provenance evidence, and validate the witness schema with offline fixtures—not adversarial execution. Every future report must separate environment, identity, hypothesis, stimulus, evidence, analysis, and limitations. “No observed failure” does not mean “secure.”
