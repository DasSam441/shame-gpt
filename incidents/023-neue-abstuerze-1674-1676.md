# Drei weitere unabhängig belegte Abstürze (1.6.74–1.6.76)

Stand: 2026-09-30. Diese drei Befunde sind zusätzliche, konkrete Laufzeitfehler aus dem CarreraMod-Releaseverlauf. Sie sind nicht bloß statische Risiken.

## 1.6.74: Logger stürzte unter Android 17 mit SIGILL ab

**Befund:** Der vollständige Tombstone des betroffenen ARM64-Pixels ordnet den Absturz beim ersten 20-Hz-Takt dem globalen Dobby-Trampolin für Bionics `fputc('\n', stream)` zu. Die App starb vor dem Pairing-HTTP.

**Technischer Fehler:** Der Logger veränderte einen globalen libc-Aufrufpfad. Unter der konkret dokumentierten Android-17-Laufzeit führte der Trampolin-Aufruf zur illegalen Instruktion.

**Korrektur:** 1.6.74 entfernte die beiden globalen libc-Hooks und ersetzte sie durch lokale PLT-Slot-Weiterleitung innerhalb der Carrera-Bibliothek. Der Bericht belegt die Ursache und den Codeumbau; die Geräteabnahme des Fixes blieb ausdrücklich offen.

**Quelle:** private Projektdokumentation `docs/CARRERAMOD_1.6.74_ANDROID17_LOGGER_BUILD.md`.

## 1.6.75: Collection-Absturz durch abgeschnittene ARM64-GCHandles

**Befund:** `collectioncrash.log` dokumentiert SIGSEGV auf UnityMain beim erneuten Öffnen/Aktualisieren der Fahrzeug-Collection, in `hooked_load_cars` und `remember_car_collection`. Direkt davor hatte der Abgleich vier Fahrzeuge verarbeitet.

**Technischer Fehler:** Auf ARM64 sind IL2CPP-GCHandles pointerbreit (64 Bit). Die Bridge speicherte Rückgabe, Argumente und Handle-Felder als `uint32_t`, wodurch die oberen 32 Bit abgeschnitten wurden. Der Tombstone zeigte den verkürzten Handle und einen ungültigen Speicherzugriff.

**Korrektur:** 1.6.75 stellte die betroffenen Typen auf `uintptr_t` um und prüfte den 32-Bit-Pfad separat auf unveränderten Code. Das ist ein weiterer bestätigter Laufzeitfehler; der Fixbericht allein belegt keine spätere subjektive Nutzerabnahme.

**Quelle:** private Projektdokumentation `docs/CARRERAMOD_1.6.75_COLLECTION_GCHANDLE_FIX.md`.

## 1.6.76: Lücke in der Multidex-Reihenfolge ließ die App sofort abstürzen

**Befund:** Der interne Vorläufer enthielt `classes20.dex`, aber keine `classes19.dex`. Android ART beendet die Suche nach weiteren DEX-Dateien an der ersten Lücke; die beim Activity-Start benötigte `HornPhysicsDebugControl` wurde nicht geladen und die App stürzte sofort ab.

**Auswirkung:** Der Kandidat wurde gesperrt, nicht als Staging importiert und aus dem TimTime-Eingang entfernt. Die folgende Version 1.6.77 schloss die Sequenz bis `classes19.dex`.

**Einordnung:** Das ist ein belegter Fehler in einem gebauten internen Kandidaten, kein bestätigter Auslieferungsfehler. Diese Unterscheidung ist wichtig.

**Quelle:** private Projektdokumentation `docs/CARRERAMOD_1.6.77_HORN_PHYSICS_DEX_FIX_BUILD.md`.

## Was ich daraus ableite

Das sind drei konkrete Ursachen mit unterschiedlichen Evidenzarten: zwei durch Gerätestacks belegte Abstürze und ein interner Paket-/Startfehler. Die Projektchronik enthält weitere Kandidaten, aber ich zähle sie erst nach Abgleich auf Doppelzählung, tatsächliche Auslieferung und Gerätebefund als eigenständige Fälle. Die Gesamtzahl bisheriger Fehler ist damit weiterhin nicht bestimmt.
