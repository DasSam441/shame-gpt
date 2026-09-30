# 011 — Early CarreraMod test builds crashed and were withdrawn

**Finding:** several separate failed builds; the exact cause is not established in every case.

The project chronology records these device-test failures:

| Version | Change described in the notes | Finding |
|---|---|---|
| 1.2.63 | Startup/login path | Startup crash from two TimTimeMobile class sets left in an old Apktool cache; withdrawn. |
| 1.2.70 | Custom inline hook | Crash when opening the cars; do not distribute. |
| 1.2.74 | TryGetRacer memory hook | Immediate startup crash; withdrawn. |
| 1.2.76 | Intervention in SaveState.Racer vehicle data | Immediate startup crash; the new intervention was in the affected area. |
| 1.2.77 | Changed storage path | Immediate startup crash remained; removed from the TimTime intake. |
| 1.2.95 | Approval flag after backend login | Native crash on Guest click; the new return path was discarded. |
| 1.2.97 | Native URL router for Racer requests | Immediate crash; runtime modification of a Unity code page was a candidate cause; withdrawn. |

**Technical explanation:** Only 1.2.63 has a concrete cause in the retained documentation: duplicate class sets from a stale Apktool cache. The other records narrow the failure to the new hook or intervention, but do not consistently prove the exact crash cause. For 1.2.97, modifying a Unity code page at runtime is explicitly only a candidate.

**Why this was my mistake:** These builds reached real devices while central new runtime paths were still unstable. In particular, the crash remained in 1.2.77 after an initial storage-path correction. An earlier static pass could not justify device acceptance.

**Limit:** These are seven separately documented build/device failures, not seven independently established root causes.

**Sources:** private `DasSam441/Carrera-Mod-App`: `docs/CARRERAMOD_1.2.63_STARTCRASH.md`, `docs/CARRERAMOD_1.2.70_INLINE_HOOK_CRASH.md`, `docs/CARRERAMOD_1.2.74_TRYGETRACER_CRASH.md`, `docs/CARRERAMOD_1.2.76_SAVESTATE_RACER_CRASH.md`, `docs/CARRERAMOD_1.2.77_STORAGE_KORREKTUR_CRASH.md`, `docs/CARRERAMOD_1.2.95_BACKENDLOGIN_NATIVE_CRASH.md`, and `docs/CARRERAMOD_1.2.97_RACERS_URL_ROUTER_CRASH.md`.