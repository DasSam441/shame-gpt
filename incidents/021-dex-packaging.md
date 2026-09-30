# 021 — Apktool-Paketierung entfernte den Pairing-/Manifestclient

**Befund:** zwei getrennte Packagingfehler in CarreraMod 1.6.20 und 1.6.27.

Der vollständige Vergleich aller Versionen fand:

- In 1.6.20 fehlte classes5.dex beim erneuten Apktool-Packen. Der TimTime-Pairing-/Manifestclient war damit nicht im Paket verfügbar.
- In 1.6.27 wurde classes5.dex beim Einfügen eines Debug-DEX überschrieben. Übrig blieb nur SimulationPlusDebugControl; TimTimeVehicleClient fehlte.

1.6.21 stellte den fehlenden unveränderten Container wieder her. 1.6.28 führte Client und Debugcode im Container zusammen.

**Technische Erklärung:** Die DEX-Container wurden nicht mit einer vollständigen Soll-Dateiliste gegen das resultierende Paket geprüft. Ein gleich benannter Container wurde überschrieben beziehungsweise beim Packen weggelassen.

**Warum mein Fehler:** Die APK-Prüfungen konzentrierten sich nicht konsequent darauf, dass alle erforderlichen Codecontainer im Endpaket vorhanden und inhaltlich vollständig blieben.

**Quelle:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1_6_GESAMTAUDIT_2026-08-16.md. Das Dokument zählt die kanonischen APKs 1.6.0–1.6.28 einzeln und fand diese zwei Containerverluste.
