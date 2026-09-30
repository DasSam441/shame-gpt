# 011 — Frühe CarreraMod-Testbuilds stürzten ab und wurden zurückgezogen

**Befund:** mehrere separate fehlgeschlagene Builds; in mehreren Fällen ist die genaue Ursache nicht belegt.

Die Projektchronik hält folgende Gerätetestfehler fest:

| Version | Änderung laut Dokumentation | Befund |
|---|---|---|
| 1.2.63 | Start-/Loginpfad | Startabsturz durch zwei TimTimeMobile-Klassensätze aus altem Apktool-Zwischencache; zurückgezogen. |
| 1.2.70 | eigener Inline-Hook | Absturz beim Öffnen der Autos; nicht verteilen. |
| 1.2.74 | TryGetRacer-Speicherhook | sofortiger Startabsturz; zurückgezogen. |
| 1.2.76 | Eingriff in SaveState.Racer-Fahrzeugdaten | sofortiger Startabsturz; der neue Eingriff lag im betroffenen Bereich. |
| 1.2.77 | geänderter Speicherweg | der sofortige Startabsturz blieb bestehen; aus dem TimTime-Eingang entfernt. |
| 1.2.95 | Freigabemarkierung nach Backend-Login | nativer Absturz beim Guest-Klick; der neue Rücksprungpfad wurde verworfen. |
| 1.2.97 | nativer URL-Router für Racer-Aufrufe | sofortiger Absturz; Kandidat war Laufzeitänderung einer Unity-Code-Seite; zurückgezogen. |

**Technische Erklärung:** Nur bei 1.2.63 nennt die erhaltene Dokumentation eine konkrete Ursache: doppelt vorhandene Klassensätze durch veralteten Apktool-Zwischencache. Bei den übrigen Fällen grenzt sie den Fehler auf den jeweils neuen Hook oder Eingriff ein, beweist aber nicht durchgehend die exakte Absturzursache. Für 1.2.97 ist die Laufzeitänderung einer Unity-Code-Seite ausdrücklich nur als Kandidat genannt.

**Warum das mein Fehler war:** Die Builds wurden auf reale Geräte gebracht, obwohl zentrale neue Laufzeitpfade noch nicht stabil waren. Besonders bei 1.2.77 blieb der Absturz auch nach einer ersten Speicherpfadkorrektur bestehen. Ein früher statischer Erfolg hätte hier keine Gerätefreigabe rechtfertigen dürfen.

**Grenze:** Dies sind sieben getrennte Build-/Gerätefehler, zusammen dokumentiert; nicht sieben voneinander unabhängige tiefenanalysierte Root Causes. Die fehlenden Ursachen werden hier nicht erfunden.

**Quellen:** privates DasSam441/Carrera-Mod-App:
docs/CARRERAMOD_1.2.63_STARTCRASH.md,
docs/CARRERAMOD_1.2.70_INLINE_HOOK_CRASH.md,
docs/CARRERAMOD_1.2.74_TRYGETRACER_CRASH.md,
docs/CARRERAMOD_1.2.76_SAVESTATE_RACER_CRASH.md,
docs/CARRERAMOD_1.2.77_STORAGE_KORREKTUR_CRASH.md,
docs/CARRERAMOD_1.2.95_BACKENDLOGIN_NATIVE_CRASH.md und
docs/CARRERAMOD_1.2.97_RACERS_URL_ROUTER_CRASH.md.
