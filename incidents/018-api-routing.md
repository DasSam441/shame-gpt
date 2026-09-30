# 018 — The API selection was saved in TimTime but initially not applied in the app

**Finding:** early routing configuration was not runtime proof; 1.6.30 installed its hook too late.

TimTime supplied API sources through the mobile manifest. A later audit found that 1.6.29 did not pass those values to a working Unity web-request consumer. An earlier router also tried to write branch code directly into a Unity code page; that approach crashed and was discarded.

Version 1.6.30 introduced a `SendWebRequest` hook, but the subsequent device test showed that early Carrera configuration requests had already run before hook installation and therefore used the original source. Saving the portal choice did not prove that requests were redirected.

**Technical explanation:** The router received configuration and was installed only after login. Requests made before that continued to the original host. A separate early approach modified executable IL2CPP memory and was documented as a crash cause.

**Why this was my mistake:** I initially treated a saved API selection and the presence of a hook entry point as equivalent to working routing. Only observing the actual `UnityWebRequest` send point could establish which source a request used.

**Sources:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_API_ROUTING_REPAIR_2026-08-17.md` and `docs/CARRERAMOD_1.6.30_API_ROUTING_REPARATUR.md`.