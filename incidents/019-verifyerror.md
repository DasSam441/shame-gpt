# 019 — The driver-debug setter made the Activity class invalid

**Finding:** CarreraMod 1.6.0 was blocked because of a `VerifyError`.

The new method `setTimTimeDriverDebugAllowed(boolean)` used too few registers and overwrote the Activity reference with a String. When Android accessed `debugApprovedMac`, the receiver had the wrong type and the class was rejected with `VerifyError`.

Version 1.6.1 added a real local register and kept `p0` as the Activity reference. The version note says this fixed the `VerifyError`; the separate ARMv7 crash remained open.

**Why this was my mistake:** The Smali register/type check before the build did not catch that a method parameter and the Activity receiver occupied the same register position. A build artifact without DEX verification was not release-ready.

**Sources:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.6.0_DRIVER_DEBUG_VERIFYERROR.md` and `docs/CARRERAMOD_1.6.1_DRIVER_DEBUG_REGISTERFIX.md`.