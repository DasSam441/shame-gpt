# 010 — A packaging error nearly doubled the APK size

**Finding:** defect in 1.6.71, discovered only in the next build.

The later packaging audit records that 1.6.71 additionally marked `.so` libraries as uncompressed. As a result, the APK grew to about 299 MB instead of the usual 135 MB. The document explicitly says 1.6.71 is not a valid packaging reference; the error was found by direct comparison during build 1.6.72.

**Technical explanation:** `apktool.yml` specified an incorrect ZIP compression rule for native libraries. The app might still start, but the distribution artifact became more than twice as large.

**Why this was my mistake:** Acceptance checks covered signature, alignment, DEX, and functional paths, but missed the package-size comparison and the changed compression rules. The report records the correction only in the successor build.

**Source:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.6.71_PAIRING_1.4.4_PATH.md`, “Retrospective packaging finding”; 2026-08-24.