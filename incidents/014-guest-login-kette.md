# 014 — TimTime interventions repeatedly blocked Carrera’s Guest login

**Finding:** repeated failed login/start approaches with causes that were not all the same.

The version notes record, among other issues:

- 1.2.86: the Guest crash remained after changing the Racer reference.
- 1.2.90: a hook on `RacerService.get_CarProfiles` could write to `RacerController` before login completed.
- 1.2.91: as many as 40 native hooks were installed before the Guest click and blocked login.
- 1.2.96: the version intended as a clean base still blocked Guest, showing the fault was not the TimTime API or manifest.
- 1.2.98: Guest remained blocked after the URL-router call was removed.
- 1.2.99: routing calls were removed, but the launcher was still `CarreraApiLogActivity` instead of the original Unity launcher.
- 1.3.0: the `RacerService.CarProfiles` bridge could intervene before Guest/SaveState was ready and was withdrawn.

**Technical explanation:** The variants intervened at different points in a sensitive sequence: Activity startup, hook installation, login, and Racer-state creation. A hook that runs before login completes can alter Carrera’s own state or block Guest. The record does not establish one shared root cause for every historical crash.

**Why this was my mistake:** The series shows that I used the protected login path too early and at too many points as an import strategy. The later project finding required storing manifest data at startup and importing only after the original login/SaveState path had demonstrably completed.

**Counting limit:** The seven versions above are documented bad states, not seven independently proven causes. The series also contains other unreleased intermediate builds.

**Sources:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.2.86_GUEST_CRASH_FOLLOWUP.md`, `docs/CARRERAMOD_1.2.90_CARPROFILES_LOGINFEHLER.md`, `docs/CARRERAMOD_1.2.91_START_HOOK_BLOCKIERT_GUEST.md`, `docs/CARRERAMOD_1.2.96_KERNBASIS_RUECKZUG.md`, `docs/CARRERAMOD_1.2.98_ROUTER_AUFRUF_ENTFERNT.md`, `docs/CARRERAMOD_1.2.99_API_ROUTING_AUFRUFE_ENTFERNT.md`, and `docs/CARRERAMOD_1.3.0_GUEST_LOGIN_RUECKZUG.md`.