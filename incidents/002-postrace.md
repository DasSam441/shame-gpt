# 002 — Static post-race port was presented like proof of functionality

**Finding:** misleading and later disproven technically. Baseline: build 269.

The historical documentation called the parser “fully ported” and said Carrera’s original flow remained untouched. The later failure chronology clarifies that “fully” referred only to static address and package checks, not successful runtime acceptance. No complete successful path from race end to TimTime receipt was demonstrated after build 269; several builds crashed or produced no result.

A later crash was traced to confusing two incompatible IL2CPP methods. In addition, a parser ran synchronously in the race-end call path and could block Carrera’s return.

**Technical explanation:** Static checks of binary addresses and APK structure do not prove that hook timing, data types, and the runtime path are correct. A synchronous hook can block the original flow even when it executes the original instruction.

**Why this was my mistake:** I described static integrity in a way that sounded like functional confidence. Device evidence disproved that implication.

**Source:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_269_POSTRACE_RUNTIME_FAILURE.md`; commit `aa6759016f`.