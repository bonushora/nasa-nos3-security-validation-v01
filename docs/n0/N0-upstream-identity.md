# N0 — Upstream Identity

## Frozen upper reference

| Item | Observation |
|---|---|
| Repository | `https://github.com/nasa/nos3` |
| Observed branch | `main` |
| Fixed commit | `5a3bdee6be9a2c67fdf994ae6db56d5c60395302` |
| Immutable page | <https://github.com/nasa/nos3/commit/5a3bdee6be9a2c67fdf994ae6db56d5c60395302> |
| Reobserved | 2026-11-04 (`America/Sao_Paulo`) |
| Displayed commit date | 2026-06-30 |
| Message | `Merge branch 'dev'` |
| Release | `v1_07_05` / Release 1.7.5 |
| Declared license | NOSA 1.3 |
| Upper-freeze state | `VERIFIED` |
| Transitive state | `PARTIAL_NOT_FROZEN` |

`main` records where the commit was observed; it is not part of the immutable identity. Stable file references use the full SHA.

## Observation method

The official `main` history displayed `5a3bdee` first, the immutable page resolved the full SHA and two parents, and the releases page associated `v1_07_05` with that commit. A read-only `git ls-remote --symref https://github.com/nasa/nos3.git HEAD refs/heads/main 'refs/tags/v1_07_05^{}'` attempt failed before remote contact with `Could not resolve host: github.com`; Git transport confirmation therefore remained `BLOCKED`.

The upper identity was `VERIFIED_BY_OFFICIAL_WEB`. Independent byte-level and transitive freezing remained pending.

## Fixed source locators

| File | Fixed locator | Content SHA-256 |
|---|---|---|
| `README.md` | `https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/README.md` | `UNAVAILABLE_RAW_BYTES` |
| `.gitmodules` | `https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/.gitmodules` | `UNAVAILABLE_RAW_BYTES` |
| `NOS3_Getting_Started.md` | `https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/docs/wiki/NOS3_Getting_Started.md` | `UNAVAILABLE_RAW_BYTES` |
| `NOS3_Architecture.md` | `https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/docs/wiki/NOS3_Architecture.md` | `UNAVAILABLE_RAW_BYTES` |
| `NOS3_Flight_Software.md` | `https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/docs/wiki/NOS3_Flight_Software.md` | `UNAVAILABLE_RAW_BYTES` |
| `NOS3_Ground_Software.md` | `https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/docs/wiki/NOS3_Ground_Software.md` | `UNAVAILABLE_RAW_BYTES` |
| `NOS3_Components.md` | `https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/docs/wiki/NOS3_Components.md` | `UNAVAILABLE_RAW_BYTES` |
| `NOS3_Simulators.md` | `https://github.com/nasa/nos3/blob/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/docs/wiki/NOS3_Simulators.md` | `UNAVAILABLE_RAW_BYTES` |

The public browser exposed content and locators but not locally hashable bytes. Empty-input hashes were rejected. This did not prevent upper commit identification, but it prevented independent byte-level and transitive claims.

## Declared submodules

The fixed `.gitmodules` displayed 47 declarations:

- cFS core/apps: `CFS_CI`, `CFS_TO`, `CFS_IO_LIB`, `cFE`, `osal`, `PSP`, `elf2cfetbl`, `SCH`, `SC`, `CF`, `LC`, `ci_lab`, `to_lab`, `hwlib`, `DS`, `FM`, `SBN`, `SBN-Client`;
- simulation: `nos_time_driver`, `sim_common`, `sim_terminal`, `truth_42_sim`;
- GSW: `OrbitInviewPowerPrediction`, `gsw-cosmos`, `gsw-ait`, `ttc-command`, `nos3_yamcs_master`;
- components/algorithms: `arducam`, `generic_reaction_wheel`, `sample`, `novatel_oem615`, `generic_fss`, `generic_css`, `generic_eps`, `generic_torquer`, `generic_radio`, `generic_imu`, `generic_magnetometer`, `CryptoLib`, `generic_adcs`, `generic_star_tracker`, `syn`, `OnAIR`, `generic_thruster`, `mgr`, `blackboard`;
- F´: `fprime-nos3`.

The earlier count of 49 was corrected: `cfdp` and `spacecop-ce` do not appear in the fixed manifest. Branch hints do not replace gitlink SHAs.

## Identifiable technologies and limits

Documented technologies include Git, Linux, Docker/Compose, optional Vagrant/VirtualBox, C/C++, Boost, CMake/Make, NOS Engine, 42, cFS/OSAL/PSP, F´, COSMOS 4, OpenC3/COSMOS 5, YAMCS, AIT, CCSDS, UDP, I2C, SPI, CAN, and UART. Complete versions and dependency resolution were not verified.

ReadTheDocs `/latest/` was used only for navigation. Fixed-commit files prevail on conflict.

Public sources observed: [NOS3 repository](https://github.com/nasa/nos3), [fixed commit](https://github.com/nasa/nos3/commit/5a3bdee6be9a2c67fdf994ae6db56d5c60395302), [NOS3 releases](https://github.com/nasa/nos3/releases), and the [NOS3 manual](https://nos3.readthedocs.io/en/latest/).

> **EN-R1 chronology note:** N1-A later recovered 44 candidate SHAs. N1-A-R2 retained them as `PARTIAL`, found no immutable tree readback, and left the root tree OID unavailable.
