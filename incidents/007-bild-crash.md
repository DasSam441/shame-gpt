# 007 — Fahrzeugbild-Crash der falschen Ursache zugeschrieben

**Befund:** erste Ursachenannahme widerlegt; Folgekorrektur scheiterte.

CarreraMod 1.6.58 stürzte beim ersten Öffnen der Kollektion mit TimTime-Fahrzeugbildern ab. Die erste Analyse machte einen unmittelbar ausgelösten zweiten LoadCars-Aufbau verantwortlich. 1.6.59 entfernte diesen zweiten Aufruf; der dokumentierte Gerätetest zeigte danach exakt denselben Fehler.

> „Damit war der zweite LoadCars-Aufruf nicht die eigentliche Ursache.“

Der Download funktionierte, Serverprotokolle zeigten erfolgreiche Bildantworten; der native Unity-Crash wurde im Java-Crashreport nicht erfasst.

**Warum mein Fehler:** Ich machte aus einer auffälligen Reihenfolge eine Ursachenfeststellung und lieferte darauf eine Korrektur, bevor der Fehler reproduzierbar der Stelle zugeordnet war. Der erneute Gerätetest widerlegte die Annahme.

**Quelle:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1.6.58_TIMTIME_VEHICLE_IMAGES.md, 2026-08-22; Build 1.6.59-Gerätebefund.
