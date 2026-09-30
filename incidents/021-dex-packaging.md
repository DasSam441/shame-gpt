# 021 — Apktool packaging removed the pairing/manifest client

**Finding:** two separate packaging errors in CarreraMod 1.6.20 and 1.6.27.

The full version comparison found:

- In 1.6.20, `classes5.dex` was missing after Apktool repackaging. The TimTime pairing/manifest client was therefore unavailable in the package.
- In 1.6.27, inserting a debug DEX overwrote `classes5.dex`. Only `SimulationPlusDebugControl` remained; `TimTimeVehicleClient` was missing.

Version 1.6.21 restored the missing unchanged container. Version 1.6.28 combined the client and debug code in that container.

**Technical explanation:** The final package was not checked against a complete expected list of DEX containers. A same-named container was overwritten or omitted during packaging.

**Why this was my mistake:** The APK checks did not consistently verify that every required code container remained present and complete in the final package.

**Source:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1_6_GESAMTAUDIT_2026-08-16.md`. The note counts canonical APKs 1.6.0–1.6.28 and identifies these two container losses.