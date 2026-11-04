# N1-A — Upstream Transitive Inventory

> **Historical record with later clarification:** N1-A used mutable `tree/main` pages as observational bridges and classified `gsw/ttc-command` as a blocking declaration/tree divergence. N1-A-R2 later determined that this did not prove absence from the immutable tree. The R2 state for that entry is `UNAVAILABLE`; every recovered SHA below remains a `PARTIAL` candidate.

## Upper identity

| Field | Value | Historical state |
|---|---|---|
| URL | `https://github.com/nasa/nos3` | `VERIFIED` |
| Observed branch | `main` | `VERIFIED` on observation date |
| Commit | `5a3bdee6be9a2c67fdf994ae6db56d5c60395302` | `VERIFIED` by immutable page/release |
| Root Git tree OID | `UNAVAILABLE` | API/Git transport unavailable |
| `.gitmodules` | `https://raw.githubusercontent.com/nasa/nos3/5a3bdee6be9a2c67fdf994ae6db56d5c60395302/.gitmodules`; 47 counted sections | displayed content `VERIFIED` |
| Transitive freeze | not demonstrated | `BLOCKED` |

Evidence codes: `M` fixed `.gitmodules`; `C`, `F`, `G`, and `S` are observational component, FSW, GSW, and simulator tree pages. These are not immutable tree-object readback.

## Historical 47-entry inventory

| # | Path | Declared URL | Observed identity | Type / relationship | Identifiable dependencies | N1-A state | Source |
|---:|---|---|---|---|---|---|---|
| 1 | `fsw/apps/ci` | `https://github.com/nasa-itc/CFS_CI.git` | `01a9e51472454fd3f2262bf97ad5b3be861f0d22` | command app; cFS/NOS3 | cFE, CCSDS; recursion uninspected | `PARTIAL` | M+F |
| 2 | `fsw/apps/to` | `https://github.com/nasa-itc/CFS_TO.git` | `666a8d17c87ac4f5dae1719dc218f9146468d062` | telemetry app; cFS/NOS3 | cFE, CCSDS | `PARTIAL` | M+F |
| 3 | `fsw/apps/io_lib` | `https://github.com/nasa-itc/CFS_IO_LIB.git` | `b98953eea7b187cebf8028eb62824f306693c135` | library; cFS/NOS3 | cFE/OSAL | `PARTIAL` | M+F |
| 4 | `fsw/cfe` | `https://github.com/nasa-itc/cFE.git` | `87e273743f3d07ed9216462b461e9f398ff96c87` | core framework; cFS | OSAL, PSP, cFS apps | `PARTIAL` | M+F |
| 5 | `fsw/osal` | `https://github.com/nasa-itc/osal.git` | `08a79bb6ac02b9ced8aa555853ecdd96e5ebc1a7` | OS abstraction; cFS | platform/RTOS | `PARTIAL` | M+F |
| 6 | `fsw/psp` | `https://github.com/nasa-itc/PSP.git` | `d0a5d6fa4093d473a929fde42a0983e489d89d4a` | platform support; cFS | cFE, OSAL, platform | `PARTIAL` | M+F |
| 7 | `fsw/tools/elf2cfetbl` | `https://github.com/nasa-itc/elf2cfetbl.git` | full gitlink not recovered | table tool; cFS | ELF/cFE | `UNAVAILABLE` | M |
| 8 | `fsw/apps/sch` | `https://github.com/nasa-itc/SCH.git` | `8e8073e4c76fe41beb82e38e54cfcda7bc661156` | scheduler app; cFS/NOS3 | cFE | `PARTIAL` | M+F |
| 9 | `fsw/apps/sc` | `https://github.com/nasa-itc/SC.git` | `4ff66c2b7f9d02eb7806bb3d085e1cfeb1f4ae72` | stored-command app; cFS/NOS3 | cFE | `PARTIAL` | M+F |
| 10 | `fsw/apps/cf` | `https://github.com/nasa-itc/CF.git` | `03bd8ad39533e1709e30fd33b6d3f0455092ce4b` | CFDP app; cFS/NOS3 | cFE, transport | `PARTIAL` | M+F |
| 11 | `fsw/apps/lc` | `https://github.com/nasa-itc/LC.git` | `5daef363c95d71c1ff3c5e9dcd4dddab560e8b39` | limit-checker app; cFS/NOS3 | cFE | `PARTIAL` | M+F |
| 12 | `sims/nos_time_driver` | `https://github.com/nasa-itc/nos_time_driver.git` | `0c097273431cf8a4882559518b704d8c8621b74f` | time driver; NOS3/sim | NOS Engine | `PARTIAL` | M+S |
| 13 | `sims/sim_common` | `https://github.com/nasa-itc/sim_common.git` | `0dbcb2ead4e5625a2a163c0fabe04157dd7e375e` | simulation library | NOS Engine, C++ | `PARTIAL` | M+S |
| 14 | `sims/sim_terminal` | `https://github.com/nasa-itc/sim_terminal.git` | `d6603c66bd6c25c59c239a197ef915c257845df3` | simulation terminal | sim_common/NOS Engine | `PARTIAL` | M+S |
| 15 | `gsw/OrbitInviewPowerPrediction` | `https://github.com/nasa-itc/OrbitInviewPowerPrediction.git` | `0eed643eeaa9bcc35020b0b38399c25b616421c2` | GSW analysis | orbit/configuration | `PARTIAL` | M+G |
| 16 | `gsw/cosmos` | `https://github.com/nasa-itc/gsw-cosmos.git` | `5e45ff376d017cc517ff9d03995109b59254e518` | ground station | CCSDS command/TLM | `PARTIAL` | M+G |
| 17 | `sims/truth_42_sim` | `https://github.com/nasa-itc/truth_42_sim.git` | `2f05258a4040e195322d8aacc51a01cb3d687a15` | dynamics/truth | 42, sim_common | `PARTIAL` | M+S |
| 18 | `fsw/apps/ci_lab` | `https://github.com/nasa-itc/ci_lab.git` | `5dd2cf50a827c4837c867a0bdc58b5295caf61c1` | lab command app | cFE | `PARTIAL` | M+F |
| 19 | `fsw/apps/to_lab` | `https://github.com/nasa-itc/to_lab.git` | `6ae88fd1c2bb931d233c0051c88b787447bd5bb6` | lab telemetry app | cFE | `PARTIAL` | M+F |
| 20 | `fsw/apps/hwlib` | `https://github.com/nasa-itc/hwlib.git` | `d65f77dea94467b7cb71053eb2f58f7a0cde3b02` | hardware library | cFE, simulated interfaces | `PARTIAL` | M+F |
| 21 | `components/arducam` | `https://github.com/nasa-itc/arducam.git` | `d123f505885e8796e645c21550422340804c911d` | component/simulator | sim_common, HWLIB | `PARTIAL` | M+C |
| 22 | `components/generic_reaction_wheel` | `https://github.com/nasa-itc/generic_reaction_wheel.git` | `9a669563371809c4d131e1a468a7cc4405f8c605` | component/simulator | sim_common, HWLIB | `PARTIAL` | M+C |
| 23 | `components/sample` | `https://github.com/nasa-itc/sample.git` | `9d1a76dc391fefe7a42314052c1f10fa527f526b` | sample component; cFS/F´ | sim_common, HWLIB | `PARTIAL` | M+C |
| 24 | `components/novatel_oem615` | `https://github.com/nasa-itc/novatel_oem615.git` | `8fca4b5e0db6dc00cd4745be334e7b895fc45b66` | GPS component | sim_common, HWLIB | `PARTIAL` | M+C |
| 25 | `fsw/apps/ds` | `https://github.com/nasa-itc/DS.git` | `568b29324ff58b3af287e5138182c817810055f8` | data-storage app | cFE, filesystem | `PARTIAL` | M+F |
| 26 | `fsw/apps/fm` | `https://github.com/nasa-itc/FM.git` | `c5dac232f30965f011bcb31e671a4010b0ea0cfd` | file-manager app | cFE, filesystem | `PARTIAL` | M+F |
| 27 | `components/generic_fss` | `https://github.com/nasa-itc/generic_fss.git` | `ceb89220d60fe187d69934baf5612d1373493fc1` | component/simulator | sim_common, HWLIB | `PARTIAL` | M+C |
| 28 | `components/generic_css` | `https://github.com/nasa-itc/generic_css.git` | `8690e1671b8a008324e51f6be6984f5141fa46bc` | component/simulator | sim_common, HWLIB | `PARTIAL` | M+C |
| 29 | `components/generic_eps` | `https://github.com/nasa-itc/generic_eps.git` | `1aad19930ada314091d5be0b75bfd4379a39765d` | component/simulator | sim_common, HWLIB | `PARTIAL` | M+C |
| 30 | `components/generic_torquer` | `https://github.com/nasa-itc/generic_torquer.git` | `6e0392e54b10ed7bc69e43fdaff64e8f514cd4ff` | component/simulator | sim_common, HWLIB | `PARTIAL` | M+C |
| 31 | `components/generic_radio` | `https://github.com/nasa-itc/generic_radio.git` | `a2effa73715ab4fe2fdc41e549ae2dca81214d98` | component/simulator | sim_common, network | `PARTIAL` | M+C |
| 32 | `components/generic_imu` | `https://github.com/nasa-itc/generic_imu.git` | `67a86ad93eaf762aa3087aa62a512e7ba1a2dbcb` | component/simulator | sim_common, HWLIB | `PARTIAL` | M+C |
| 33 | `components/generic_mag` | `https://github.com/nasa-itc/generic_magnetometer.git` | `7d6833f23a133bb76dc08dcb20c4d5e0e1a8dd68` | component/simulator | sim_common, HWLIB | `PARTIAL` | M+C |
| 34 | `components/cryptolib` | `https://github.com/nasa/CryptoLib.git` | `d4f91523b7f2f247b89bbde9e156cd8420e2cb86` | protection library | CCSDS, crypto backend | `PARTIAL` | M+C |
| 35 | `components/generic_adcs` | `https://github.com/nasa-itc/generic_adcs.git` | `09a604fc10c8c79981ffeb2ee1792c7719674a10` | component/simulator | sim_common, 42 dynamics | `PARTIAL` | M+C |
| 36 | `components/generic_star_tracker` | `https://github.com/nasa-itc/generic_star_tracker.git` | `3e4fa235b43fb4479995009ff63a1a3c15d08023` | component/simulator | sim_common, HWLIB | `PARTIAL` | M+C |
| 37 | `components/syn` | `https://github.com/nasa-itc/syn.git` | `721c8d1756559aa3374a90c3cd2887b52405ee8d` | component/simulator | sim_common, HWLIB | `PARTIAL` | M+C |
| 38 | `fsw/apps/sbn` | `https://github.com/nasa-itc/SBN.git` | `240f90f56641d43e5db1dae457d7ef8772a1c659` | bus-network app | cFE, network | `PARTIAL` | M+F |
| 39 | `fsw/apps/sbn_client` | `https://github.com/nasa-itc/SBN-Client.git` | `1cafda865b5f40d3fc9839b916ef5d6e0b2ff935` | SBN client | SBN, cFE | `PARTIAL` | M+F |
| 40 | `components/onair/fsw` | `https://github.com/nasa-itc/OnAIR.git` | `aa5559c0f234eba263041b6007573f16870194e5` | app/component | cFE, OnAIR | `PARTIAL` | M+C |
| 41 | `gsw/ait` | `https://github.com/sphinxdefense/gsw-ait.git` | `478a6c8a0adb5066545732ce2b0f927f0be7420f` | ground station | command/TLM | `PARTIAL` | M+G |
| 42 | `gsw/ttc-command` | `https://github.com/sphinxdefense/ttc-command` | N1-A alleged no corresponding observed entry | GSW command tool | uninspected | `BLOCKED` historically; `UNAVAILABLE` in R2 | M+G |
| 43 | `components/generic_thruster` | `https://github.com/nasa-itc/generic_thruster.git` | `0ff68370fbac15291e67316ac60aff3a89115f70` | component/simulator | sim_common, HWLIB | `PARTIAL` | M+C |
| 44 | `fsw/fprime/fprime-nos3` | `https://github.com/nasa-itc/fprime-nos3.git` | full gitlink not recovered | F´ deployment | F´, NOS3 components | `UNAVAILABLE` | M |
| 45 | `components/mgr` | `https://github.com/nasa-itc/mgr.git` | `e4f56752df4549ffe074b79d768374f51099357b` | manager/component | cFE, configuration | `PARTIAL` | M+C |
| 46 | `components/blackboard` | `https://github.com/nasa-itc/blackboard` | `953bfe372ad3cf0715fb1f974b0415a921a4d913` | data component | cFE, shared data | `PARTIAL` | M+C |
| 47 | `gsw/yamcs` | `https://github.com/nasa-itc/nos3_yamcs_master.git` | `a51559bc668c4708b860882c3a39dd4f63fee909` | ground station | CCSDS command/TLM | `PARTIAL` | M+G |

## Historical counts and branch hints

N1-A counted 47 declarations, 44 recovered full SHA strings, two unavailable full values, one alleged blocking divergence, and 0 fully transitively frozen entries. R2 superseded only the divergence interpretation, not the SHA candidates.

Explicit branch hints: `main` for 14 entries; `master` for 5; `nos3-main` for 4; `nos3-dev` for `gsw/yamcs`. The other 23 entries had no explicit branch. Branch hints are mutable and do not replace gitlinks.
