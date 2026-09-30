# 013 — TimTime-Fahrzeugimport: Daten geladen, Autos trotzdem nicht sichtbar

**Befund:** zwei dokumentierte, unterschiedliche Importfehler.

Bei 1.2.67 wurden TimTime-Freigaben und Bilder im Live-Test geladen, die Fahrzeuge erschienen aber nicht in Carreras originaler Unity-Liste. Der Build wurde nicht freigegeben.

Bei 1.2.80 war die Geräteansicht schwarz. Die Korrekturdokumentation benennt die Ursache: Die Carrera-Katalog-ID wurde in TechnicalName statt in das Id-Feld geschrieben. Der Stand wurde zurückgezogen.

**Technische Erklärung:** Manifest-/Bildabruf war nicht gleichbedeutend mit erfolgreicher Anlage eines gültigen Carrera-Racer-Datensatzes. Im zweiten Fall belegte das Gerät einen konkreten Feldzuordnungsfehler im Objektmodell.

**Warum mein Fehler:** Ich behandelte erfolgreiche Datenabrufe und vorhandene Hookpfade als Fortschritt, bevor die resultierende Fahrzeugliste und ihre Darstellung auf dem Gerät funktionierten.

**Quellen:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1.2.67_TIMTIME_FILTER_TEST.md und docs/CARRERAMOD_1.2.80_RACERCONTROLLER_ERSTVERSUCH.md.
