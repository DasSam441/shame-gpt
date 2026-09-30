@{path=incidents/ct-056-sim-gas-step-cooldown-ms-was-missing.md; body=# CT-056 — SIM+ gas_step_cooldown_ms was missing.

**Finding:** documented CarreraMod/TimTime failure or incorrect claim.

**What happened:** The cooldown remained outside the JSON contract.

**Technical explanation:** The record identifies a mismatch between the intended behavior or reported verification and the observed runtime, data, UI, or package state. The specific mismatch above is the supported technical finding; this short report does not infer a broader root cause than its evidence establishes.

**Why this was my mistake:** I implemented or described the path before confirming the relevant end-to-end behavior, or I failed to correct the attempt before presenting it as usable. The evidence below supports this individual finding and its stated limit.

**Evidence:** Private source: [`DasSam441/Carrera-Mod-App/docs/CARRERAMOD_1.6.49_JSON_WIRKUNGS_AUDIT.md`](https://github.com/DasSam441/Carrera-Mod-App/blob/main/docs/CARRERAMOD_1.6.49_JSON_WIRKUNGS_AUDIT.md).

**Scope:** One documented finding. Related incidents may share a root cause; this report does not claim otherwise.}.body