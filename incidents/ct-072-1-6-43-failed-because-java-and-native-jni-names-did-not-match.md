@{path=incidents/ct-072-1-6-43-failed-because-java-and-native-jni-names-did-not-match.md; body=# CT-072 — 1.6.43 failed because Java and native JNI names did not match.

**Finding:** documented CarreraMod/TimTime failure or incorrect claim.

**What happened:** Java declared getState/setValues and similar methods, while the library exported different names; the first configuration call raised UnsatisfiedLinkError.

**Technical explanation:** The record identifies a mismatch between the intended behavior or reported verification and the observed runtime, data, UI, or package state. The specific mismatch above is the supported technical finding; this short report does not infer a broader root cause than its evidence establishes.

**Why this was my mistake:** I implemented or described the path before confirming the relevant end-to-end behavior, or I failed to correct the attempt before presenting it as usable. The evidence below supports this individual finding and its stated limit.

**Evidence:** Private source: [`DasSam441/Carrera-Mod-App/docs/CARRERAMOD_1.6.43_NATIVE_BOUNDARY_REPAIR.md`](https://github.com/DasSam441/Carrera-Mod-App/blob/main/docs/CARRERAMOD_1.6.43_NATIVE_BOUNDARY_REPAIR.md).

**Scope:** One documented finding. Related incidents may share a root cause; this report does not claim otherwise.}.body