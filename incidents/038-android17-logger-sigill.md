# 038 — The 1.6.74 logger crashed on Android 17 with SIGILL

**Finding:** device-confirmed ARM64 startup/session crash in the 20-Hz logger path.

The full tombstone from the affected Pixel ties the crash on the first 20-Hz tick to the global Dobby trampoline for Bionic `fputc('\n', stream)`. The app terminated before the pairing HTTP request.

**Technical explanation:** The logger intercepted a global libc call. On the documented Android 17 runtime, executing through that trampoline produced an illegal instruction (`SIGILL`). This is a runtime failure, not just an unverified static risk.

**Why this was my mistake:** I introduced a process-wide libc hook for a local logging need and allowed the build to reach device testing before validating that trampoline on the target Android runtime. The correction removed the two global libc hooks and used local PLT-slot forwarding inside the Carrera library. The record does not show device acceptance of that correction.

**Limit:** The tombstone establishes the crash path for the documented device/build. It does not establish that every Android 17 device or every logger use would fail identically.

**Source:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.6.74_ANDROID17_LOGGER_BUILD.md`.