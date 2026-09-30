# 007 — I attributed the vehicle-image crash to the wrong cause

**Finding:** the first causal hypothesis was disproven; the follow-up correction also failed.

CarreraMod 1.6.58 crashed when the collection was first opened with TimTime vehicle images. The initial analysis blamed an immediately triggered second `LoadCars` rebuild. Version 1.6.59 removed that second call; the documented device test then reproduced exactly the same failure.

> “That showed the second `LoadCars` call was not the actual cause.”

The download worked and server logs showed successful image responses; the native Unity crash was not captured by the Java crash reporter.

**Why this was my mistake:** I turned a suspicious sequence into a causal conclusion and shipped a correction before the failure had been tied to that code path. The repeated device test disproved the hypothesis.

**Source:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.6.58_TIMTIME_VEHICLE_IMAGES.md`, 2026-08-22; device finding for build 1.6.59.