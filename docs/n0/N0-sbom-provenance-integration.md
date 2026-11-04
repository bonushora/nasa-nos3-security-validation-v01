# N0 — Future SBOM and Provenance Integration

## Principle

Component integrity and behavioral security are independent dimensions. SBOM/provenance identifies what was selected or built; behavioral experiments examine what occurred under a defined stimulus and configuration. Neither substitutes for the other.

Future cFS and F´ SBOM research outputs must be consumed only as immutable exported artifacts, without importing or modifying their projects.

## Per-experiment bundle

- `source`: NOS3 commit, every submodule gitlink, patch state.
- `build`: toolchain, flags, generators, reproducible timestamps, attestations.
- `runtime`: image, binary, library/plugin, and configuration digests.
- `sbom`: CycloneDX or SPDX identity/version plus SHA-256.
- `behavior`: scenario, canonical events, witness journal, results, limitations.
- `link`: `experiment_id` and `provenance_bundle_digest` on every record.

| Dimension | cFS | F´ | Future normalization |
|---|---|---|---|
| Core | cFE, OSAL, PSP | F´ framework/topology | purl/CPE where applicable plus repo/commit |
| Apps/components | cFS apps/HWLIB | components/deployment | logical unit plus produced binary |
| Interfaces | Software Bus, CCSDS, HWLIB | ports, commands, channels | canonical event and interface version |
| Generated data | tables, mission definitions | topology dictionaries/generated data | digest and generator version |
| Runtime | cFS executable/libraries | deployment/libraries | loaded-artifact digest |

## Provenance gates

1. Freeze upper tree and gitlinks.
2. Validate SBOM and eliminate floating references.
3. Match build/runtime digests.
4. Match configuration and dictionaries.
5. Explicitly map cFS/F´ differences.
6. Treat known vulnerabilities as context, not behavioral verdicts.

N0 read, imported, or modified no independent SBOM project. This is a proposed interface only.
