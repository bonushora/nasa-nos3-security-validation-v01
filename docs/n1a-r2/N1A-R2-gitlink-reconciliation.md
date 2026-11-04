# N1-A-R2 — Reconciliation of 47 Declarations and Gitlinks

## Reading rule

- `M`: fixed `.gitmodules` declaration.
- `N1-TL`: candidate SHA preserved from an official link target observed during N1-A.
- `R2-TREE`: required immutable Git Trees/`ls-tree` response; unavailable.
- `160000?` / `commit?`: expected gitlink semantics, not observed verification.

All 44 SHA values are `PARTIAL` candidates. No entry was promoted to `VERIFIED` because immutable path/mode/type/SHA readback and target reachability were missing.

| # | Path | Declared URL | Observed mode | Observed type | Candidate SHA | Source | State | Reachability/recursion |
|---:|---|---|---|---|---|---|---|---|
| 1 | `fsw/apps/ci` | `https://github.com/nasa-itc/CFS_CI.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `01a9e51472454fd3f2262bf97ad5b3be861f0d22` | M+N1-TL | `PARTIAL` | not demonstrated |
| 2 | `fsw/apps/to` | `https://github.com/nasa-itc/CFS_TO.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `666a8d17c87ac4f5dae1719dc218f9146468d062` | M+N1-TL | `PARTIAL` | not demonstrated |
| 3 | `fsw/apps/io_lib` | `https://github.com/nasa-itc/CFS_IO_LIB.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `b98953eea7b187cebf8028eb62824f306693c135` | M+N1-TL | `PARTIAL` | not demonstrated |
| 4 | `fsw/cfe` | `https://github.com/nasa-itc/cFE.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `87e273743f3d07ed9216462b461e9f398ff96c87` | M+N1-TL | `PARTIAL` | not demonstrated |
| 5 | `fsw/osal` | `https://github.com/nasa-itc/osal.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `08a79bb6ac02b9ced8aa555853ecdd96e5ebc1a7` | M+N1-TL | `PARTIAL` | not demonstrated |
| 6 | `fsw/psp` | `https://github.com/nasa-itc/PSP.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `d0a5d6fa4093d473a929fde42a0983e489d89d4a` | M+N1-TL | `PARTIAL` | not demonstrated |
| 7 | `fsw/tools/elf2cfetbl` | `https://github.com/nasa-itc/elf2cfetbl.git` | `UNAVAILABLE` | `UNAVAILABLE` | `UNAVAILABLE` | M | `UNAVAILABLE` | entry/target unavailable |
| 8 | `fsw/apps/sch` | `https://github.com/nasa-itc/SCH.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `8e8073e4c76fe41beb82e38e54cfcda7bc661156` | M+N1-TL | `PARTIAL` | not demonstrated |
| 9 | `fsw/apps/sc` | `https://github.com/nasa-itc/SC.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `4ff66c2b7f9d02eb7806bb3d085e1cfeb1f4ae72` | M+N1-TL | `PARTIAL` | not demonstrated |
| 10 | `fsw/apps/cf` | `https://github.com/nasa-itc/CF.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `03bd8ad39533e1709e30fd33b6d3f0455092ce4b` | M+N1-TL | `PARTIAL` | not demonstrated |
| 11 | `fsw/apps/lc` | `https://github.com/nasa-itc/LC.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `5daef363c95d71c1ff3c5e9dcd4dddab560e8b39` | M+N1-TL | `PARTIAL` | not demonstrated |
| 12 | `sims/nos_time_driver` | `https://github.com/nasa-itc/nos_time_driver.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `0c097273431cf8a4882559518b704d8c8621b74f` | M+N1-TL | `PARTIAL` | not demonstrated |
| 13 | `sims/sim_common` | `https://github.com/nasa-itc/sim_common.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `0dbcb2ead4e5625a2a163c0fabe04157dd7e375e` | M+N1-TL | `PARTIAL` | not demonstrated |
| 14 | `sims/sim_terminal` | `https://github.com/nasa-itc/sim_terminal.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `d6603c66bd6c25c59c239a197ef915c257845df3` | M+N1-TL | `PARTIAL` | not demonstrated |
| 15 | `gsw/OrbitInviewPowerPrediction` | `https://github.com/nasa-itc/OrbitInviewPowerPrediction.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `0eed643eeaa9bcc35020b0b38399c25b616421c2` | M+N1-TL | `PARTIAL` | not demonstrated |
| 16 | `gsw/cosmos` | `https://github.com/nasa-itc/gsw-cosmos.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `5e45ff376d017cc517ff9d03995109b59254e518` | M+N1-TL | `PARTIAL` | not demonstrated |
| 17 | `sims/truth_42_sim` | `https://github.com/nasa-itc/truth_42_sim.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `2f05258a4040e195322d8aacc51a01cb3d687a15` | M+N1-TL | `PARTIAL` | not demonstrated |
| 18 | `fsw/apps/ci_lab` | `https://github.com/nasa-itc/ci_lab.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `5dd2cf50a827c4837c867a0bdc58b5295caf61c1` | M+N1-TL | `PARTIAL` | not demonstrated |
| 19 | `fsw/apps/to_lab` | `https://github.com/nasa-itc/to_lab.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `6ae88fd1c2bb931d233c0051c88b787447bd5bb6` | M+N1-TL | `PARTIAL` | not demonstrated |
| 20 | `fsw/apps/hwlib` | `https://github.com/nasa-itc/hwlib.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `d65f77dea94467b7cb71053eb2f58f7a0cde3b02` | M+N1-TL | `PARTIAL` | not demonstrated |
| 21 | `components/arducam` | `https://github.com/nasa-itc/arducam.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `d123f505885e8796e645c21550422340804c911d` | M+N1-TL | `PARTIAL` | not demonstrated |
| 22 | `components/generic_reaction_wheel` | `https://github.com/nasa-itc/generic_reaction_wheel.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `9a669563371809c4d131e1a468a7cc4405f8c605` | M+N1-TL | `PARTIAL` | not demonstrated |
| 23 | `components/sample` | `https://github.com/nasa-itc/sample.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `9d1a76dc391fefe7a42314052c1f10fa527f526b` | M+N1-TL | `PARTIAL` | not demonstrated |
| 24 | `components/novatel_oem615` | `https://github.com/nasa-itc/novatel_oem615.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `8fca4b5e0db6dc00cd4745be334e7b895fc45b66` | M+N1-TL | `PARTIAL` | not demonstrated |
| 25 | `fsw/apps/ds` | `https://github.com/nasa-itc/DS.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `568b29324ff58b3af287e5138182c817810055f8` | M+N1-TL | `PARTIAL` | not demonstrated |
| 26 | `fsw/apps/fm` | `https://github.com/nasa-itc/FM.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `c5dac232f30965f011bcb31e671a4010b0ea0cfd` | M+N1-TL | `PARTIAL` | not demonstrated |
| 27 | `components/generic_fss` | `https://github.com/nasa-itc/generic_fss.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `ceb89220d60fe187d69934baf5612d1373493fc1` | M+N1-TL | `PARTIAL` | not demonstrated |
| 28 | `components/generic_css` | `https://github.com/nasa-itc/generic_css.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `8690e1671b8a008324e51f6be6984f5141fa46bc` | M+N1-TL | `PARTIAL` | not demonstrated |
| 29 | `components/generic_eps` | `https://github.com/nasa-itc/generic_eps.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `1aad19930ada314091d5be0b75bfd4379a39765d` | M+N1-TL | `PARTIAL` | not demonstrated |
| 30 | `components/generic_torquer` | `https://github.com/nasa-itc/generic_torquer.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `6e0392e54b10ed7bc69e43fdaff64e8f514cd4ff` | M+N1-TL | `PARTIAL` | not demonstrated |
| 31 | `components/generic_radio` | `https://github.com/nasa-itc/generic_radio.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `a2effa73715ab4fe2fdc41e549ae2dca81214d98` | M+N1-TL | `PARTIAL` | not demonstrated |
| 32 | `components/generic_imu` | `https://github.com/nasa-itc/generic_imu.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `67a86ad93eaf762aa3087aa62a512e7ba1a2dbcb` | M+N1-TL | `PARTIAL` | not demonstrated |
| 33 | `components/generic_mag` | `https://github.com/nasa-itc/generic_magnetometer.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `7d6833f23a133bb76dc08dcb20c4d5e0e1a8dd68` | M+N1-TL | `PARTIAL` | not demonstrated |
| 34 | `components/cryptolib` | `https://github.com/nasa/CryptoLib.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `d4f91523b7f2f247b89bbde9e156cd8420e2cb86` | M+N1-TL | `PARTIAL` | not demonstrated |
| 35 | `components/generic_adcs` | `https://github.com/nasa-itc/generic_adcs.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `09a604fc10c8c79981ffeb2ee1792c7719674a10` | M+N1-TL | `PARTIAL` | not demonstrated |
| 36 | `components/generic_star_tracker` | `https://github.com/nasa-itc/generic_star_tracker.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `3e4fa235b43fb4479995009ff63a1a3c15d08023` | M+N1-TL | `PARTIAL` | not demonstrated |
| 37 | `components/syn` | `https://github.com/nasa-itc/syn.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `721c8d1756559aa3374a90c3cd2887b52405ee8d` | M+N1-TL | `PARTIAL` | not demonstrated |
| 38 | `fsw/apps/sbn` | `https://github.com/nasa-itc/SBN.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `240f90f56641d43e5db1dae457d7ef8772a1c659` | M+N1-TL | `PARTIAL` | not demonstrated |
| 39 | `fsw/apps/sbn_client` | `https://github.com/nasa-itc/SBN-Client.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `1cafda865b5f40d3fc9839b916ef5d6e0b2ff935` | M+N1-TL | `PARTIAL` | not demonstrated |
| 40 | `components/onair/fsw` | `https://github.com/nasa-itc/OnAIR.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `aa5559c0f234eba263041b6007573f16870194e5` | M+N1-TL | `PARTIAL` | not demonstrated |
| 41 | `gsw/ait` | `https://github.com/sphinxdefense/gsw-ait.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `478a6c8a0adb5066545732ce2b0f927f0be7420f` | M+N1-TL | `PARTIAL` | not demonstrated |
| 42 | `gsw/ttc-command` | `https://github.com/sphinxdefense/ttc-command` | `UNAVAILABLE` | `UNAVAILABLE` | `UNAVAILABLE` | M | `UNAVAILABLE` | existence and absence both unproven |
| 43 | `components/generic_thruster` | `https://github.com/nasa-itc/generic_thruster.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `0ff68370fbac15291e67316ac60aff3a89115f70` | M+N1-TL | `PARTIAL` | not demonstrated |
| 44 | `fsw/fprime/fprime-nos3` | `https://github.com/nasa-itc/fprime-nos3.git` | `UNAVAILABLE` | `UNAVAILABLE` | `UNAVAILABLE` | M | `UNAVAILABLE` | entry/target unavailable |
| 45 | `components/mgr` | `https://github.com/nasa-itc/mgr.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `e4f56752df4549ffe074b79d768374f51099357b` | M+N1-TL | `PARTIAL` | not demonstrated |
| 46 | `components/blackboard` | `https://github.com/nasa-itc/blackboard` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `953bfe372ad3cf0715fb1f974b0415a921a4d913` | M+N1-TL | `PARTIAL` | not demonstrated |
| 47 | `gsw/yamcs` | `https://github.com/nasa-itc/nos3_yamcs_master.git` | `UNAVAILABLE (160000?)` | `UNAVAILABLE (commit?)` | `a51559bc668c4708b860882c3a39dd4f63fee909` | M+N1-TL | `PARTIAL` | not demonstrated |

| Individual state | Count |
|---|---:|
| `VERIFIED` | 0 |
| `PARTIAL` | 44 |
| `UNAVAILABLE` | 3 |
| `BLOCKED` | 0 — aggregate gate only |
| `INVALID` | 0 |

`RECONCILIATION_GATE=BLOCKED`
