@{path=incidents/ct-084-rawx-overlay-labels-were-not-reliably-tied-to-byte-sources.md; body=# CT-084 — RawX overlay labels were not reliably tied to byte sources.

**Finding:** documented CarreraMod/TimTime failure or incorrect claim.

**What happened:** 0x21/0x22/0x23 were temporarily displayed as w23/w24/w25; the mapping needed revalidation.

**Technical explanation:** The record identifies a mismatch between the intended behavior or reported verification and the observed runtime, data, UI, or package state. The specific mismatch above is the supported technical finding; this short report does not infer a broader root cause than its evidence establishes.

**Why this was my mistake:** I implemented or described the path before confirming the relevant end-to-end behavior, or I failed to correct the attempt before presenting it as usable. The evidence below supports this individual finding and its stated limit.

**Evidence:** Private source: [`DasSam441/Carrera-Mod-App/docs/chat-history/README.md`](https://github.com/DasSam441/Carrera-Mod-App/blob/main/docs/chat-history/README.md).

**Scope:** One documented finding. Related incidents may share a root cause; this report does not claim otherwise.}.body