@{path=incidents/ct-103-i-used-the-wrong-time-contract-in-the-live-target-payload.md; body=# CT-103 — I used the wrong time contract in the Live-Target payload.

**Finding:** documented CarreraMod/TimTime failure or incorrect claim.

**What happened:** The first Android path sent lapTimeMs; the user corrected that only the original crossing timestamp should be sent. TimTime derives lap time from consecutive timestamps. Same chat.

**Technical explanation:** The record identifies a mismatch between the intended behavior or reported verification and the observed runtime, data, UI, or package state. The specific mismatch above is the supported technical finding; this short report does not infer a broader root cause than its evidence establishes.

**Why this was my mistake:** I implemented or described the path before confirming the relevant end-to-end behavior, or I failed to correct the attempt before presenting it as usable. The evidence below supports this individual finding and its stated limit.

**Evidence:** Archived Codex chat transcript: “Plan Live-Target transmission.” (accessible in the user’s archive; not mirrored here).

**Scope:** One documented finding. Related incidents may share a root cause; this report does not claim otherwise.}.body