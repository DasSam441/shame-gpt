# 028: Bekannte VRC-Fehlschläge gelesen, aber unzureichend berücksichtigt

Stand: 2026-09-30.

## Widerspruch in der eigenen Rückschau

Zu Beginn schrieb ich: „Ich habe die alte VRC-Historie und den aktuellen Unity-Code gelesen.“ Die Werkzeugchronik bestätigt tatsächliche Lesezugriffe auf `verlauf.md`, insbesondere die Abschnitte um S282/S283 und die spätere Abschaltung. Ich benannte schon damals, dass ein mit normalen Eingaben fahrender Bot trotz bestandener Tests bei der echten Abnahme abgelehnt worden war.

Später forderte der Nutzer erneut, die dokumentierten VRC-Versuche anzusehen. Ich antwortete, ich hätte sie „vor dem neuen Vorschlag berücksichtigen müssen“. Bei der jetzigen Archivarbeit kündigte ich zunächst pauschal „versäumte VRC-Recherche“ an. Das wäre als Behauptung, die Historie sei anfangs überhaupt nicht gelesen worden, falsch. Die vorliegende vollständige Chronik korrigiert diese Verkürzung.

## Tatsächliches Versäumnis

Die dokumentierten Warnzeichen wurden gelesen, aber nicht in ausreichende fachliche Kriterien umgesetzt. Der bekannte Unterschied zwischen bestandenen technischen Tests und einem akzeptablen Renngegner wiederholte sich: zunächst langsame kontaktfreie Runden, dann schnelle Mittellinienfahrt, schließlich weiterhin große Rekordabstände.

Die alte VRC-Dokumentation nennt bei S282 bis zu 3,12 m Linienabweichung und verspätete Lenkkorrekturen. S283 verbesserte die Linienführung, erreichte aber die damalige Rekordnähe nicht durchgehend. Danach wurde der Bot deaktiviert. Unity verwendete ebenfalls geometrische Zielverfolgung und Kurventempobegrenzung. Das belegt eine verwandte Problemklasse, nicht automatisch dieselbe physikalische Ursache.

## Späte Alternativenprüfung

ML-Agents wurde dem Nutzer erst auf „hat unity dafür nichts?“ als Alternative erläutert. Der ursprüngliche Auftrag hatte ausdrücklich nach einer besseren Lösung in Unity gefragt. Die frühe Beratung hätte den selbst programmierten Regler und das Training eines Fahrers vergleichend bewerten sollen. Aus Unitys ML-Agents-Verfügbarkeit oder einem Kart-Beispiel folgt jedoch kein Beweis, dass es unser Rekordziel erreicht. In diesem Chat wurde kein ML-Agent implementiert oder trainiert; das bleibt ein offener Ansatz, kein bereits erfolgreicher Ersatz.

## Beleggrenze

Der Fehler ist unzureichende Nutzung vorhandenen Wissens und zu pauschale spätere Selbstbeschreibung. Weder bewusste Täuschung noch die grundsätzliche Unmöglichkeit brauchbarer Unity-Rennbots ist daraus ableitbar. Quelle der VRC-Befunde: lokale `C:/XAMPP/htdocs/vrc/verlauf.md`, Einträge vom 19.09.2026 um S282/S283/S285; diese Datei ist hier nicht öffentlich gespiegelt.

## Quellen und Grenzen

Quelle: vollständig durchblätterte Nutzer- und Assistentennachrichten im Chat „Bots für Rennen prüfen“, Thread `01a0ef38-8afc-7a11-8ab3-2d77d367ceb2`, bis zum Auftrag vom 30.09.2026, auch den übrigen Chat zu dokumentieren. Werkzeugprotokolle wurden gezielt geprüft, nicht jeder Build unabhängig wiederholt. Kurze Chatauszüge werden hier als Primärbelege wiedergegeben; der vollständige private Chat wird nicht gespiegelt.

Zusätzlicher Projektbeleg: [ONLINE-BOT.md am dokumentierten Release-Commit](https://github.com/DasSam441/nanoracer-unity/blob/c69d4d28596c6a4583dc49b173a0dccd64938941/Documentation/ONLINE-BOT.md). Dieser Link kann Repository-Zugriff erfordern. Lokale Evidence-Dateien sind keine öffentlich abrufbaren Belege.
