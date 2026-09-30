# 040 — The internal 1.6.76 candidate had a Multidex gap and could not load its startup class

**Finding:** package/startup error in an internal candidate; not a confirmed distribution failure.

The internal 1.6.76 predecessor contained `classes20.dex` but no `classes19.dex`. Android ART stopped looking for later DEX files at the first missing number. The Activity startup path needed `HornPhysicsDebugControl`, which was consequently unavailable and caused an immediate app crash.

**Technical explanation:** Numbered Multidex containers must form a continuous sequence. A later DEX file after a gap is not a substitute for the missing container when the runtime enumerates the package.

**Why this was my mistake:** The package verifier allowed a missing intermediate DEX file in a build candidate. The candidate was later blocked, removed from the TimTime intake, and retained in a recoverable location. The subsequent 1.6.77 packaging note records the continuous sequence through `classes19.dex`.

**Limit:** The source calls this an internal predecessor/candidate and says it was not imported to staging. This is not described as an end-user release incident.

**Source:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.6.77_HORN_PHYSICS_DEX_FIX_BUILD.md`.