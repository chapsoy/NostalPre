# nostalRE Classic Pre-Renewal build

This source tree is a Pre-Renewal gameplay variant of the nostalRE offline Android launcher.

## What is changed

- The rAthena servers are compiled with `PRERE` (`-DCMAKE_CXX_FLAGS=-DPRERE`), which disables the `RENEWAL` compile-time rules in `server/src/config/renewal.hpp`.
- The client-side skill tree, item view/shield table, and job level/AP table are generated from `server/db/pre-re/` instead of `server/db/re/`.
- The client/server packet version remains **20250716**. This is deliberate: the current nostalRE client speaks the kRO 2025-07-16 packet protocol and expects the matching `data.grf`.
- The APK is still based on the current nostalRE Renewal-oriented client. Its modern UI and graphics may still show Renewal-era elements (for example, Renewal-styled status UI or visual features), even though the server mechanics are built for Pre-Renewal.

## Build

Use the same prerequisites as the upstream nostalRE launcher (Android SDK/NDK r30, Rust target, cargo-ndk, CMake, Ninja, and Python 3), then run:

```sh
scripts/build-apk.sh
```

The output is `out/nostalre.apk`. `scripts/build-server.sh` now compiles the servers with `PRERE`.

## Important testing note

Important: this source tree now explicitly defines `PRERE` in
`server/src/config/renewal.hpp`. The rAthena map server selects
`npc/pre-re/scripts_main.conf` when `RENEWAL` is not defined
(`server/src/map/map.cpp`, `map_reloadnpc`). Do a clean build (remove the
old `out/build/server-*` and `out/android/bin` directories) so an old
Renewal binary is not reused. Do not use `--skip-native` for the first build.

This is a source-level Pre-Renewal conversion, not a verified release APK. Build the APK and test character creation, stat/skill progression, leveling, monster EXP/drop behavior, and combat formulas in-game before treating it as complete. Keep a copy of the original Renewal APK and game save before installing this variant.
