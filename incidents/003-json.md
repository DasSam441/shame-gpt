# 003 — JSON settings had no effect

**Finding:** defective. CarreraMod 1.6.49 / code 195.

A later effect audit traced JSON fields through DEX/Java code to native setters. Among its findings:
- The root `enabled` value did not reliably disable mods.
- `module_handling` values were not read from JSON.
- `offtrack_brake.available` was ignored.
- `simulation_plus` throttle-jump values were not bound to JSON.
- `start_min` and `tx_byte_10` had no parser/setter path.
- `automatic_logging.on_start_min` was always set to false.

**Technical explanation:** Existing dialogs and JSON keys are not enough. A value must flow from the parser to the effective native call; a missing JNI path or an overriding local value makes it inert.

**Why this was my mistake:** The shipped UI suggested configurability that the program did not fully implement. Only a field-by-field effect check exposed the gaps.

**Source:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.6.49_JSON_WIRKUNGS_AUDIT.md`; as of 2026-08-20.