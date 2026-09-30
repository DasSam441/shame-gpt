# 002 — Statische Postrace-Portierung klang wie Funktionsnachweis

**Befund:** irreführend und später technisch widerlegt. Basis 269.

Die historische Doku nannte den Parser „vollständig portiert“ und sagte, Carreras Originalablauf bleibe unangetastet. Die spätere Fehlerchronik stellt klar: „vollständig“ beschrieb nur statische Adress- und Paketprüfungen, keine erfolgreiche Laufzeitabnahme. Seit Build 269 wurde kein vollständiger erfolgreicher Weg vom Rennende bis zum TimTime-Eingang belegt; mehrere Builds crashten oder lieferten kein Ergebnis.

Ein späterer Crash wurde auf die Verwechslung zweier inkompatibler IL2CPP-Methoden zurückgeführt. Zusätzlich lief ein Parser synchron im Rennende-Aufrufpfad und konnte Carreras Rückkehr blockieren.

**Technisch:** Binäradressen und APK-Struktur statisch zu prüfen beweist nicht, dass Hook-Zeitpunkt, Datentypen und Laufzeitpfad stimmen. Ein synchroner Hook kann den Originalablauf trotz ausgeführter Originalinstruktionen blockieren.

**Warum mein Fehler:** Ich stellte statische Integrität so dar, dass sie wie Funktionssicherheit klang. Die Gerätebefunde widerlegten das.

**Quelle:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_269_POSTRACE_RUNTIME_FAILURE.md; Commit aa6759016f.
