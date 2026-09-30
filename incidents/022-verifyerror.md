# 022 — Dalvik register errors made debug APKs fail as soon as classes loaded

**Finding:** two separate `VerifyError` builds.

CarreraMod 1.5.6 used too few Dalvik registers in `createOverlayTools`. A graph button could overwrite the Activity reference, causing Android to abort with `VerifyError`.

CarreraMod 1.6.0 had the same error type at a different location: `setTimTimeDriverDebugAllowed(boolean)` overwrote the Activity reference with a String, and Android rejected the class when it accessed `debugApprovedMac`. Fix 1.6.1 gave the setter its own local register.

**Technical explanation:** Dalvik registers are typed storage slots for parameters and local values. If registers are miscounted or an Activity reference is confused with a String, the VM can reject the method or entire class during loading.

**Why this was my mistake:** Register and type relationships were not checked sufficiently before the builds. Both problems blocked startup before any device feature could work.

**Sources:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.5.6_GRAPH_REGISTERFEHLER.md`, `docs/CARRERAMOD_1.6.0_DRIVER_DEBUG_VERIFYERROR.md`, and `docs/CARRERAMOD_1.6.1_DRIVER_DEBUG_REGISTERFIX.md`.