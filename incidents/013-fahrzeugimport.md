# 013 — TimTime vehicle data loaded, but the cars were still not visible

**Finding:** two documented, distinct import failures.

In 1.2.67, the live test loaded TimTime permissions and images, but the vehicles did not appear in Carrera’s original Unity list. The build was not approved.

In 1.2.80, the device showed a black view. The correction note identifies the cause: the Carrera catalog ID was written to `TechnicalName` instead of the `Id` field. That build was withdrawn.

**Technical explanation:** Fetching a manifest and images did not establish that a valid Carrera Racer record had been created. In the second case, the device finding identified a concrete field-mapping error in the object model.

**Why this was my mistake:** I treated successful data fetches and existing hook paths as progress before the resulting vehicle list and rendering worked on-device.

**Sources:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.2.67_TIMTIME_FILTER_TEST.md` and `docs/CARRERAMOD_1.2.80_RACERCONTROLLER_ERSTVERSUCH.md`.