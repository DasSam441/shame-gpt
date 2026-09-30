# 008 — I initially blamed the wrong side for the pairing failure

**Finding:** wrong initial diagnosis, followed by a defective app path.

CarreraMod 1.6.70 was documented as a deterministic Android pairing fix and passed static checks. The first device test showed that TimTime created a pairing code, but the server saw neither a pair request nor an error report. The complete link never reached the app code; one cause was a synthetic JavaScript click on a custom-scheme link.

After that portal path was corrected, another server finding showed a successful pair request followed by a manifest fetch. This exposed a second problem in the early app initialization path: it started pairing/import before initialization finished and could abort the app. Version 1.6.71 restored the earlier flow.

**Why this was my mistake:** I treated static checks of the app path as a sufficient explanation, although the first failure occurred before the app was reached. After the portal fix, a second app failure emerged that the original acceptance check had missed.

**Source:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.6.70_PAIRING_FIX.md` and `docs/CARRERAMOD_1.6.71_PAIRING_1.4.4_PATH.md`; 2026-08-24.