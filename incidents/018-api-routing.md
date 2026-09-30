# 018 — API-Auswahl in TimTime gespeichert, aber in der App zunächst nicht angewendet

**Befund:** frühe Routingkonfigurationen waren kein Laufzeitnachweis; 1.6.30 installierte den Hook zu spät.

TimTime lieferte API-Quellen im Mobile-Manifest. In 1.6.29 wurden diese Werte laut späterem Audit noch nicht an einen funktionierenden Unity-Webrequest-Verbraucher weitergegeben. Ein früher Router versuchte außerdem, Sprungcode direkt in eine Unity-Code-Seite zu schreiben; dieser Ansatz stürzte ab und wurde verworfen.

1.6.30 führte einen neuen SendWebRequest-Hook ein, aber der Gerätetest zeigte anschließend, dass frühe Carrera-Konfigurationsanfragen bereits vor der Hook-Installation liefen und deshalb die Originalquelle verwendeten. Die gespeicherte Portalwahl bewies also nicht, dass Anfragen wirklich umgeleitet waren.

**Technische Erklärung:** Die Konfiguration wurde erst nach dem Login an den Router übergeben und installiert. Requests, die davor abgingen, liefen weiterhin direkt zum ursprünglichen Host. Ein weiterer früher Ansatz veränderte ausführbaren IL2CPP-Speicher und war als Absturzursache dokumentiert.

**Warum mein Fehler:** Ich setzte die gespeicherte API-Auswahl und das Vorhandensein eines Hook-Einstiegs zunächst mit wirksamem Routing gleich. Erst der beobachtete UnityWebRequest-Sendepunkt konnte belegen, welche Quelle eine echte Anfrage nutzte.

**Quellen:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_API_ROUTING_REPAIR_2026-08-17.md und docs/CARRERAMOD_1.6.30_API_ROUTING_REPARATUR.md.
