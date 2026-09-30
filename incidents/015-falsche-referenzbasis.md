# 015 — APKs presented as “clean” or known-good still blocked login

**Finding:** two failed rebuilds with different integrity problems.

Version 1.3.2 was built from a manufacturer App Store base without TimTime classes or hooks. Guest login still did not work. The retained manufacturer file was only a base split; the matching original ABI split was missing. That build did not establish the cause of the login failure.

Version 1.3.3 was intended to reproduce the known-working CarreraMod 1.2.49 core. Guest login remained blocked. A later DEX comparison showed that Apktool had rebuilt `classes2.dex`, containing `CarreraApiLogActivity`, so it was not byte-identical to the reference; only the native library comparison had passed earlier.

**Technical explanation:** A base made only from an App Bundle base split is not a complete installable original package. Matching native libraries do not prove that the Java/DEX startup path is byte-identical. The launcher and its DEX were part of the protected login path.

**Why this was my mistake:** I presented “clean” or “known-good” builds as restoration of original behavior before checking every required ABI split and every DEX file for identity.

**Sources:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.3.2_SAUBERE_BASIS_RUECKZUG.md` and `docs/CARRERAMOD_1.3.3_KNOWN_GOOD_CORE_RUECKZUG.md`.