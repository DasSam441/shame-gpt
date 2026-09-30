# Fallindex

Stand 2026-09-30. Kein Vollständigkeitsanspruch. Die Fehlerfamilien können mehrere Versionen umfassen; Builds derselben Annahme zählen nicht automatisch als unabhängige Ursachen.

| ID | Projekt | Befund |
|---|---|---|
| 001 | CarreraMod | 1.6.25 als ARMv7-Fix beschrieben; späterer Kontrollflussbefund widerlegt das. |
| 002 | CarreraMod | Statische Postrace-Prüfung klang wie Funktionsnachweis; mehrere Geräteabläufe scheiterten. |
| 003 | CarreraMod | Mehrere ausgelieferte JSON-Felder und Schalter wirkungslos. |
| 004 | CarreraMod | Signierte APK gebaut, obwohl kein Build beauftragt war. |
| 005 | TimTime | Grobe Inventur als „Punkt 1“ präsentiert; Lücken und widersprüchliche Rollenzahlen. |
| 006 | TimTime | Unity-Plattformbuilds mit nachgewiesenem Gerätezugriff vermischt. |
| 007 | CarreraMod | Fahrzeugbild-Crash einer falschen Ursache zugeschrieben; Korrektur scheiterte erneut. |
| 008 | CarreraMod / TimTime | Pairing-Fehler zunächst der falschen Seite zugeordnet; 1.6.70 scheiterte auch im App-Pfad. |
| 009 | CarreraMod / TimTime | Ziellinienereignisse gingen verloren; alte Queue-Ereignisse liefen in eine verwaiste Session. |
| 010 | CarreraMod | APK-Verpackungsfehler ließ Datei von etwa 135 MB auf etwa 299 MB anwachsen. |
| 011 | CarreraMod | Sieben frühe Testbuilds stürzten ab oder wurden zurückgezogen. |
| 012 | CarreraMod | Zwölf wiederholte ARMv7-Versuche derselben Absturzklasse plus späterer fehlgeschlagener Versuch. |
| 013 | CarreraMod | Fahrzeugdaten wurden geladen, aber Fahrzeuge fehlten oder zeigten schwarz. |
| 014 | CarreraMod | Wiederholte Guest-Login-Eingriffe blockierten den Herstellerpfad. |
| 015 | CarreraMod | Als saubere/known-good Basis ausgegebene APKs blockierten weiterhin Guest. |
| 016 | CarreraMod | Native Bibliotheksersetzung brach Logger/BANDEN; Folgefix stürzte via JNI ab. |
| 017 | CarreraMod | Als vollständig bezeichneter JSON-Vertrag hatte fehlenden JNI-Pfad und globale Sperrregression. |
| 018 | CarreraMod | API-Auswahl war gespeichert, aber nicht rechtzeitig auf echte Requests angewendet. |
| 019 | CarreraMod | DEX-Registerfehler machte Driver-Debug-Klasse unverifizierbar. |
| 020 | CarreraMod | ARMv7-Firmware-Guard verletzte den Task<bool>-Rückgabevertrag. |
| 021 | CarreraMod | Apktool ließ Pairing-DEX fehlen oder überschrieb ihn in zwei Builds. |
| 022 | CarreraMod | Dalvik-Registerfehler erzeugte zwei nicht startfähige Debug-APKs. |
| 023 | CarreraMod | 1.6.74 Logger-SIGILL, 1.6.75 abgeschnittener GCHandle, 1.6.76 Multidex-Lücke (interner Kandidat). |
| 024 | NanoRacer / Android | Installationshilfe erfolglos; Zahlungsprofil-Pflicht zu spät geprüft; unbelegte Adress-/Profilvermutung. |
| 025 | NanoRacer | [Pauschales 79,2-km/h-Limit; kontaktfreie Runden belegten kein brauchbares Renntempo.](incidents/025-nanoracer-bot-tempolimit.md) |
| 026 | NanoRacer | [Tempo erhöht, aber weiterhin ausschließlich Mittellinie und zunächst keine Überholplanung.](incidents/026-nanoracer-mittellinienfolger.md) |
| 027 | NanoRacer | [Zu später Rekordvergleich: sieben von acht Fällen über +3 Sekunden; Prozentformulierung unpräzise.](incidents/027-nanoracer-tempo-benchmark.md) |
| 028 | NanoRacer / VRC | [VRC-Historie tatsächlich gelesen, Lehren unzureichend umgesetzt; spätere Rückschau zu pauschal.](incidents/028-nanoracer-vrc-vorwissen.md) |
| 029 | NanoRacer | [Alte Objekte blieben in Daten/Erzeugung; Knopfentfernung allein genügte nicht.](incidents/029-nanoracer-altobjekte.md) |
| 030 | NanoRacer | [Falsche Hindernis-/Nebeneinander-Fixtures sowie korrigierte Linien- und Überholfehler.](incidents/030-nanoracer-test-und-planungsfehler.md) |
| 031 | NanoRacer / Archiv | [Repetitive Kommunikation, offene APK-Verfügbarkeit, unpräzise Selbstkritik und zu enger Erstbericht.](incidents/031-nanoracer-kommunikation-und-archiv.md) |

Die 226 gescannten Versionsdokumente enthalten auch Fortschritts- und Abnahmeberichte; die Zahl 226 ist keine Fehlerzahl. Die Fallberichte trennen belegte Fehler, Folgeversuche und offene Ursachen.

[Bericht 024: Android-Installation und Registrierung](incidents/024-nanoracer-android-installation-registrierung.md)

[Prüfumfang des gesamten NanoRacer-Bot-/Android-Chats](incidents/nanoracer-chat-pruefumfang-2026-09-30.md). Die Berichte gruppieren Fehlerfamilien; 31 Berichte bedeutet nicht 31 unabhängige technische Ursachen.
