# 033 — I misidentified when the 1.6.62 post-race observer read the result

**Finding:** the claimed safe trigger was based on an incorrect call-order analysis. CarreraMod 1.6.62 / build 269.

The 1.6.62 note said the observer at `RaceResultController.Start` read `RaceResultData.Last` after the result RPC completed but before the data was copied and cleared. It therefore described the trigger as safe and able to obtain the finished result.

A correction dated 2026-08-23 states that the generic observer ran only after Carrera’s complete `Start()` method. That method had already cleared `RaceResultData.Last`, so the parser received no usable result. The same correction identifies a separate failure in the later synchronous RPC hook: it caused a native SIGSEGV in `race_result_received`.

**Technical explanation:** The analysis inferred data availability from the method name and its place in the screen flow, but did not account for the observer trampoline calling the original `Start()` before the callback. The relevant ordering was therefore the reverse of the claim.

**Why this was my mistake:** I presented an unverified lifecycle assumption as a safe, working trigger. Static address and package checks could not establish when the result data was cleared.

**Limit:** This report documents the incorrect 1.6.62 assessment. The later synchronous RPC crash is mentioned only to distinguish it; it is not counted here as a second finding.

**Source:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.6.62_POSTRACE_SAFE_TRIGGER_NO_VEHICLE_IMAGES.md`, correction dated 2026-08-23; corroborated by `docs/CARRERAMOD_269_POSTRACE_RUNTIME_FAILURE.md`.