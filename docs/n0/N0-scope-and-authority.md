# N0 — Scope and Authority

## Mission contract

N0 establishes an architectural and scientific baseline through static inspection of public sources and local documentary work. It formulates testable hypotheses, boundaries, expected evidence, and gates for future phases; it does not dynamically validate NOS3.

| Field | Value |
|---|---|
| Governance | BH-SEP v2.3 / BH-SDP v2.3 |
| Authority | `N0_DOCUMENTATION_AND_READ_ONLY` |
| Declared risk | low |
| Initial and final security state | `NOT_QUALIFIED` |
| Writable scope | the authorized workspace only |
| Revalidated observation date | 2026-11-04 (`America/Sao_Paulo`) |

## Permitted and performed

- Read public GitHub and ReadTheDocs pages.
- Inspect the workspace and create or update the authorized Markdown and JSON files.
- Verify the public commit, observed branch, release, declared submodule list, and architectural surfaces.
- Perform non-operational local validation: JSON parsing, file presence, relative links, required markers, and local SHA-256.

## Received state and traceability

At resumption, 11 N0 documents, the README, and the BH-SDP snapshot already existed and were inspected before editing. The root was not a Git worktree: `.git` was empty and Git state commands reported “not a git repository.” There was therefore no local Git history to modify.

The named `NASA-NOS3-N0-HANDOFF-v0.1` snapshot was not found in the workspace or in the bounded parent search. No replacement file was invented. The acceptance matrix records the ten criteria used, and the snapshot records this limitation.

## Prohibited and not performed

- Clone, checkout, or materialize NOS3 or submodules.
- Install dependencies or execute Docker, Vagrant, builds, simulators, or upstream scripts.
- Send commands, generate telemetry, induce faults, or conduct attacks.
- Modify external projects, remote repositories, or publish results.
- Infer security qualification from documentation.

All remained `NÃO_EXECUTADO` in the historical normative vocabulary.

## Claim classes

- **D — documented:** supported by an observed public source.
- **E — proposed extension:** a laboratory design not implemented or demonstrated.
- **U — unknown:** dependent on transitive inspection, implementation, or an experiment outside N0 authority.

A documented capability is not automatically a security control. A proposed extension is not an existing capability. Unknown evidence cannot be inferred into PASS.

## Evidence rules

1. A branch is mutable; only the full commit SHA freezes the upper reference.
2. Submodules require their own SHAs for future transitive freezing.
3. Executor logs are correlating evidence, not independent proof of effect.
4. CRC offers limited accidental-error detection, not authorization or effect authenticity.
5. The N0 PASS is documentary and does not change `NOT_QUALIFIED`.

## Out of scope

N0 did not assess flight suitability, physical safety, functional correctness, performance, real-time behavior, cryptographic effectiveness, exploitable vulnerabilities, CCSDS conformance, or fidelity between models and hardware. Independent cFS/F´ SBOM workspaces were not inspected.
