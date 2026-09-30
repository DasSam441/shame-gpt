# 041 — CarreraMod 1.2.63 crashed at startup after stale Apktool output was reused

**What happened:** CarreraMod 1.2.63 was withdrawn after an Android startup crash. The retained project note directly attributes the package to two different `TimTimeMobile` class sets left by an outdated Apktool intermediate cache.

**Technical explanation:** DEX class definitions are packaged into the APK. Reusing stale decoded/rebuild output alongside the current class set can leave duplicate or inconsistent definitions in the rebuilt package. The source record identifies the duplicate class sets as the crash cause; it does not preserve the APK or a device trace here, so this report does not add a more specific Dalvik/ART failure mechanism.

**Why this was my mistake:** I allowed a package assembled from contaminated intermediate output to reach a device test instead of proving that the rebuild directory was clean and that the final DEX set had one coherent class definition set. The build was withdrawn, but the failure should have been caught before that test.

**Evidence and limits:** The private CarreraMod project note `docs/CARRERAMOD_1.2.63_STARTCRASH.md` explicitly records both the startup crash and the stale-cache duplicate-class cause, and marks the build withdrawn and unsuitable for distribution. The note points to the project modification, verification, and Guest-login evidence records. This archive has not independently reproduced the crash.