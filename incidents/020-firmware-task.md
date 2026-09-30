# 020 — The ARMv7 firmware guard failed to return Carrera’s original result

**Finding:** CarreraMod 1.6.6 was functionally invalid on ARMv7 and was blocked.

The guard at `UpdateFirmware.Run` checked the ARMv7 `memset` GOT slot but did not return the original `Task<bool>` to Carrera. The protection routine therefore changed the manufacturer method’s contract; the change could not be treated as valid.

**Technical explanation:** A hook around an asynchronous method must preserve the expected `Task<bool>` return. Checking the GOT slot is not enough if the wrapper discards the original function’s result.

**Why this was my mistake:** I focused on memory/hook protection and failed to verify that the complete asynchronous return contract was preserved.

**Source:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.6.6_ARMV7_FIRMWARE_GUARD_GESPERRT.md`.