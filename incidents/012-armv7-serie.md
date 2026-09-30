# 012 — Repeated ARMv7 attempts despite the same continuing crash

**Finding:** at least twelve repeated builds in the same failure class, followed by one later, separately authorized attempt.

The project chronology counts twelve versions in the 1.6 line that again targeted the same ARMv7 Unity null pointer even though the previous device test had already reproduced it:

- 1.6.3–1.6.6: four variants of native call/pointer handling;
- 1.6.18–1.6.24: seven variants of hook timing, vehicle import, and `memset` protection;
- 1.6.25: another attempt whose special branch was never executed because the Smali control flow had been misread.

The later chronology says the crash persisted. Version 1.6.53 was another explicitly authorized single attempt, this time targeting the corrected `memcpy` location; its device test also failed and ARMv7 support was discontinued.

**Technical explanation:** A recurring null jump in the same native IL2CPP library was addressed with changing hook and memory paths without resolving the exact cause early enough. In 1.6.25, the analysis also contained a control-flow error. For 1.6.53, the dump showed that the earlier guard protected a `memset` address rather than the `memcpy` path that actually crashed; the correction still did not pass the device test.

**Why this was my mistake:** I kept attempting changes after the latest device test had already shown the same failure class. The later project rule therefore requires suitable ABI evidence before further attempts instead of trial and error.

**Counting limit:** The twelve attempts are the documented count for 1.6.3–1.6.25; the 1.6.26 isolation test was explicitly excluded. Version 1.6.53 came later and is stated separately. These are attempts in the same crash class, not twelve proven distinct causes.

**Sources:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_ARMV7_ABBRUCH.md` and `docs/CARRERAMOD_1.6.53_ARMV7_MEMCPY_GUEST_FIX.md`.