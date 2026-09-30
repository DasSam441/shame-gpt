# 017 — The JSON fix called complete still had ineffective switches

**Finding:** follow-up failures after the 1.6.49 audit.

Version 1.6.50 was described as a “complete TimTime JSON contract.” A later note corrected that statement: a native endpoint was still missing for `simulation_plus.speed_steering_min_throttle_percent`. A second follow-up found that root `enabled:false` was incorrectly applied as a global lock over individual mod switches.

Version 1.6.52 removed that global branch. Values in 1.6.50 could therefore remain ineffective despite passing static DEX, JSON, and signature checks.

**Technical explanation:** A field path can exist in Java/DEX and still terminate at a JNI endpoint that the native library does not export. The global lock also changed profile semantics: a root value overrode module-specific `available`/`enabled` values.

**Why this was my mistake:** I called the contract complete without tracing every field to its native consumer, and the aggregate static checks missed the missing binding. The next correction introduced a new profile regression.

**Sources:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.6.50_JSON_VERTRAG_BUILD.md` and `docs/CARRERAMOD_1.6.52_OPTIONAL_MODS_PROFILE_ROUTING.md`.