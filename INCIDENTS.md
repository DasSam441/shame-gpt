# Incident index

Status as of 2026-09-30. This archive is incomplete. A report may group several occurrences of the same failure family; the report count is not a count of independent root causes.

| ID | Project | Finding |
|---|---|---|
| 001 | CarreraMod | Version 1.6.25 was described as the ARMv7 fix; later control-flow evidence contradicted that claim. |
| 002 | CarreraMod | Static post-race checks were presented as functional proof; several result flows failed. |
| 003 | CarreraMod | Multiple delivered JSON fields and switches had no effect. |
| 004 | CarreraMod | A signed APK was built although no build had been requested. |
| 005 | TimTime | A rough inventory was presented as “point 1”; omissions and conflicting role counts remained. |
| 006 | TimTime | Unity platform builds were confused with verified hardware access. |
| 007 | CarreraMod | A vehicle-build crash was attributed to the wrong cause; the correction failed again. |
| 008 | CarreraMod / TimTime | Pairing failure was first assigned to the wrong side; version 1.6.70 also failed in the app path. |
| 009 | CarreraMod / TimTime | Finish-line events were lost; stale queued events reached the wrong session. |
| 010 | CarreraMod | APK packaging failure increased the file from about 135 MB to about 299 MB. |
| 011 | CarreraMod | Seven early test builds crashed or were withdrawn. |
| 012 | CarreraMod | Six repeated ARMv7 attempts shared the crash class; a later attempt also failed. |
| 013 | CarreraMod | Vehicle data imported, but vehicles were missing or rendered black. |
| 014 | CarreraMod | Repeated guest-login interventions blocked the intended recovery path. |
| 015 | CarreraMod | APKs presented as clean/known-good references still blocked guest access. |
| 016 | CarreraMod | Native library replacement broke logging and BANDE; a JNI follow-up regressed them. |
| 017 | CarreraMod | A purportedly complete JSON contract omitted a JNI path and introduced a global lock regression. |
| 018 | CarreraMod | API selection was saved but not applied to real requests in time. |
| 019 | CarreraMod | DEX register failure left the driver debug class unverifiable. |
| 020 | CarreraMod | ARMv7 firmware guard violated the `Task<bool>` return contract. |
| 021 | CarreraMod | APK tooling omitted or overwrote pairing DEX across two builds. |
| 022 | CarreraMod | Dalvik register failures produced two debug APKs that would not start. |
| 023 | CarreraMod | Version 1.6.74 logger SIGILL, 1.6.75 cut GCHandle, 1.6.76 Multidex errors (internal candidate). |
| 024 | NanoRacer / Android | Installation assistance failed; payment-profile requirements were checked late; address/profile assumptions were unsupported. |
| 025 | NanoRacer | A hard 79.2 km/h cap; contact-free laps did not establish usable race pace. |
| 026 | NanoRacer | Speed increased, but behavior remained line-following and then jumped; no overtaking plan. |
| 027 | NanoRacer | Later record comparison: seven of eight cases exceeded by 3+ seconds; imprecise percentage claims. |
| 028 | NanoRacer / VRC | VRC history was read, but lessons were applied incompletely; later review was too superficial. |
| 029 | NanoRacer | Old objects remained in data/generation; removing keyboard focus alone did not suffice. |
| 030 | NanoRacer | Incorrect blocker/side-by-side fixes; corrected line and overtake errors. |
| 031 | NanoRacer / Archive | Repetitive communication, uncertain APK availability, imprecise self-criticism, and too-narrow initial scope. |
| 032 | CarreraMod / TimTime | [80 additional numbered findings from version notes and chat corrections](incidents/032-carrera-timtime-80-additional-findings.md); these are details, not 80 independent causes. |

The 226 searched CarreraMod version notes include progress and acceptance records and do not represent 226 errors. Findings distinguish observed failures, repeated attempts, hypotheses, and unresolved causes.