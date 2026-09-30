# 012 — Wiederholte ARMv7-Versuche trotz unverändertem Absturz

**Befund:** mindestens zwölf wiederholte Builds derselben Fehlerklasse plus ein späterer separat freigegebener Versuch.

Die Projektchronik zählt zwölf Versionen in der 1.6-Reihe, die erneut auf denselben ARMv7-Unity-Nullzeiger zielten, obwohl der vorherige Gerätetest ihn bereits reproduziert hatte:

- 1.6.3–1.6.6: vier Varianten der nativen Aufruf-/Zeigerbehandlung;
- 1.6.18–1.6.24: sieben Varianten von Hook-Zeitpunkt, Fahrzeugimport und memset-Schutz;
- 1.6.25: ein weiterer Versuch, dessen Sonderzweig wegen falsch gelesenen Smali-Kontrollflusses gar nicht ausgeführt wurde.

Die spätere Chronik sagt, der Absturz blieb bestehen. 1.6.53 war ein weiterer ausdrücklich freigegebener Einzelversuch mit korrigierter memcpy-Stelle; auch dieser Gerätetest scheiterte und ARMv7 wurde eingestellt.

**Technische Erklärung:** Ein wiederkehrender Nullsprung in derselben nativen IL2CPP-Bibliothek wurde mit wechselnden Hook- und Speicherpfaden bearbeitet, ohne die genaue Ursache früh genug korrekt aufzulösen. In 1.6.25 kam zusätzlich ein Kontrollflussfehler in der Analyse hinzu. Für 1.6.53 belegt der Dump eine frühere falsche memset-Adresse statt des tatsächlich abstürzenden memcpy-Pfads; die Korrektur reichte im Gerätetest trotzdem nicht aus.

**Warum mein Fehler:** Ich setzte wiederholt auf weitere Änderungen, obwohl der letzte Gerätetest dieselbe Fehlerklasse bereits gezeigt hatte. Die spätere Projektregel verlangt genau deshalb keinen Trial-and-Error-Fortgang ohne passende ABI-Metadaten.

**Zählgrenze:** Die zwölf Versuche sind ein dokumentierter Zähler für 1.6.3–1.6.25; der 1.6.26-Isolationstest war darin ausdrücklich nicht enthalten. 1.6.53 liegt später und wird separat genannt. Es sind Buildversuche derselben Absturzklasse, nicht zwölf bewiesene verschiedene Ursachen.

**Quellen:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_ARMV7_ABBRUCH.md und docs/CARRERAMOD_1.6.53_ARMV7_MEMCPY_GUEST_FIX.md.
