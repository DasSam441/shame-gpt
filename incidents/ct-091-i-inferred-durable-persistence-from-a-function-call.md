@{path=incidents/ct-091-i-inferred-durable-persistence-from-a-function-call.md; body=# CT-091 — I inferred durable persistence from a function call.

**Finding:** documented CarreraMod/TimTime failure or incorrect claim.

**What happened:** I saw saveState() and claimed settings were saved without waiting for server confirmation. The later server finding was HTTP 409.

**Technical explanation:** The record identifies a mismatch between the intended behavior or reported verification and the observed runtime, data, UI, or package state. The specific mismatch above is the supported technical finding; this short report does not infer a broader root cause than its evidence establishes.

**Why this was my mistake:** I implemented or described the path before confirming the relevant end-to-end behavior, or I failed to correct the attempt before presenting it as usable. The evidence below supports this individual finding and its stated limit.

**Evidence:** Archived Codex chat transcript: “Evening races / saved rounds.” (accessible in the user’s archive; not mirrored here).

**Scope:** One documented finding. Related incidents may share a root cause; this report does not claim otherwise.}.body