# 016 — Replacing a native library broke existing features; the follow-up crashed at startup

**Finding:** regression in 1.6.42 and startup blocker in 1.6.43.

Version 1.6.42 replaced the shared `carreraapilog` library with an older variant for OFFTRACK BRK. The same library also provided state for 20-Hz logging and BANDE TEST. On the device, the logger did not start; its hook reported “not ready,” and values fell back to defaults.

Version 1.6.43 was intended to move OFFTRACK into a separate bridge, but it crashed immediately at startup. The documented cause was a JNI naming mismatch: Java declared `getState`/`setValues`/`isEnabled`/`setEnabled`, while the library exported only the names prefixed with `native`. The first call raised `UnsatisfiedLinkError`.

**Why this was my mistake:** The repair addressed one required native export by replacing an entire library and missed its other consumers. In the next build, the compiled JNI symbols were not checked against the Java declarations.

**Technical limit:** The notes establish both concrete mechanisms. They do not prove that every other function in either APK was affected.

**Sources:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.6.42_FUNKTIONS_DEBUG_JSON_AUDIT.md` and `docs/CARRERAMOD_1.6.43_NATIVE_BOUNDARY_REPAIR.md`.