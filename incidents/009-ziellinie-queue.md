# 009 — Finish-line events were lost or sent into an old session

**Finding:** version 1.6.68 passed static contract checks but failed on-device.

The documented 1.6.68 device test showed that the current crossing did not arrive. At the same time, about 200 old queued events were successfully sent to a four-day-old session that was still marked active. A later finding showed that the client discarded the current MAC when its Java vehicle mapping was missing; the orphaned regular session also blocked the virtual fallback.

**Technical explanation:** Persistent retry was intended, but the session state and vehicle mapping no longer matched the current event. Successfully transmitting old queue data did not prove that the new event arrived or that the session state was current.

**Why this was my mistake:** I treated deduplication and a persistent queue as sufficient delivery protection and presented 1.6.68 as finished virtual timing before the complete real workflow had been demonstrated.

**Source:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.6.68_VIRTUAL_TARGET_PREP.md` and `docs/CARRERAMOD_CURRENT_STATE.md`; device test 2026-08-23, correction in 1.6.69.