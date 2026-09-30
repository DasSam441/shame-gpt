@{path=incidents/ct-036-1-2-90-carprofiles-hook-ran-before-login-completed.md; body=# CT-036 — 1.2.90 — CarProfiles hook ran before login completed.

**Finding:** documented CarreraMod/TimTime failure or incorrect claim.

**What happened:** It could write to Carrera’s RacerController during Guest login.

**Technical explanation:** The record identifies a mismatch between the intended behavior or reported verification and the observed runtime, data, UI, or package state. The specific mismatch above is the supported technical finding; this short report does not infer a broader root cause than its evidence establishes.

**Why this was my mistake:** I implemented or described the path before confirming the relevant end-to-end behavior, or I failed to correct the attempt before presenting it as usable. The evidence below supports this individual finding and its stated limit.

**Evidence:** Private source: [`DasSam441/Carrera-Mod-App/docs/CARRERAMOD_1.2.90_CARPROFILES_LOGINFEHLER.md`](https://github.com/DasSam441/Carrera-Mod-App/blob/main/docs/CARRERAMOD_1.2.90_CARPROFILES_LOGINFEHLER.md).

**Scope:** One documented finding. Related incidents may share a root cause; this report does not claim otherwise.}.body