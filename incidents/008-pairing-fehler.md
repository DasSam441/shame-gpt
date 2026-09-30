# 008 — Pairing-Fehler zunächst der falschen Seite zugeordnet

**Befund:** falsche Erstdiagnose, danach fehlerhafter App-Pfad.

CarreraMod 1.6.70 wurde als deterministische Reparatur des Android-Pairings dokumentiert und statisch geprüft. Der erste Gerätetest zeigte: TimTime erstellte zwar einen Pairing-Code, aber der Server sah weder den Pair-Aufruf noch einen Fehlerbericht. Der vollständige Link erreichte den App-Code nicht; Ursache war unter anderem ein künstlicher JavaScript-Klick auf den Custom-Scheme-Link.

Nachdem dieser Portalweg korrigiert war, belegte ein weiterer Serverbefund einen erfolgreichen Pair-Aufruf mit anschließendem Manifestabruf. Damit war auch der vorgezogene App-Initialisierungspfad als Fehlerquelle sichtbar: Er startete Pairing/Import vor abgeschlossener Initialisierung und konnte die App abbrechen. 1.6.71 stellte den früheren Ablauf wieder her.

**Warum mein Fehler:** Ich interpretierte statische App-Pfadprüfungen als ausreichende Erklärung, obwohl der eigentliche Fehler zuerst vor der App lag. Nach der Portalreparatur zeigte sich zusätzlich ein zweiter Fehler, der in der ursprünglichen Abnahme nicht erkannt war.

**Quelle:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1.6.70_PAIRING_FIX.md und docs/CARRERAMOD_1.6.71_PAIRING_1.4.4_PATH.md; 2026-08-24.
