# 025: Rennbot mit pauschal 79,2 km/h ausgeliefert

Stand: 2026-09-30.

## Aussage und Gegenbefund

Der erste Abschluss betonte: „54 Fahrtests, 162 Runden, keine Bandenkontakte“. Der Nutzer beanstandete anschließend, wie langsam der Bot sei. Meine Antwort bestätigte: „Ich habe den Bot auf maximal 79,2 km/h begrenzt“.

## Technischer Fehler

Der erste Bot erhielt ein festes Limit von 22 m/s (= 79,2 km/h), ein Kurvenbudget von 7 m/s² und ein Bremsbudget von 5 m/s². Die pauschal vorsichtige Fahrplanung wurde nicht ausreichend gegen die tatsächliche Leistungsfähigkeit der drei Fahrzeugklassen geprüft. Kontaktfreie langsame Runden konnten die Testkriterien erfüllen, ohne einen brauchbaren Renngegner zu ergeben.

Das Problem war die unzureichende fachliche Abnahme, nicht eine nachgewiesene Fälschung der 162 Runden. Der Abschluss wies auf die offene Spielgefühl-Abnahme hin, stellte aber weder das niedrige Tempolimit noch einen tragfähigen Tempovergleich in den Vordergrund.

## Folgen und Korrektur

Der Nutzer musste die zu geringe Geschwindigkeit nach der Auslieferung melden. Erst danach wurden Klassenhöchstgeschwindigkeit, Bremsleistung und höhere Kurvenvorgaben berücksichtigt. Die Korrektur erreichte lokal 207 kontaktfreie Runden und bis etwa 212 km/h. Das behob noch nicht die fehlende Rennlinie; siehe Fall 026.

Belege: `Evidence/online-bot/driving.json`, `Evidence/bot-pace-cleanup/pace-comparison.json` und die Abschnitte zur ersten Fassung und Pace correction in ONLINE-BOT.md. Das spätere Ziel Rekord +3 Sekunden war zu Beginn noch nicht ausdrücklich festgelegt und wird nicht rückwirkend als damals zugesagter Zahlenwert dargestellt.

## Quellen und Grenzen

Quelle: vollständig durchblätterte Nutzer- und Assistentennachrichten im Chat „Bots für Rennen prüfen“, Thread `01a0ef38-8afc-7a11-8ab3-2d77d367ceb2`, bis zum Auftrag vom 30.09.2026, auch den übrigen Chat zu dokumentieren. Werkzeugprotokolle wurden gezielt geprüft, nicht jeder Build unabhängig wiederholt. Kurze Chatauszüge werden hier als Primärbelege wiedergegeben; der vollständige private Chat wird nicht gespiegelt.

Zusätzlicher Projektbeleg: [ONLINE-BOT.md am dokumentierten Release-Commit](https://github.com/DasSam441/nanoracer-unity/blob/c69d4d28596c6a4583dc49b173a0dccd64938941/Documentation/ONLINE-BOT.md). Dieser Link kann Repository-Zugriff erfordern. Lokale Evidence-Dateien sind keine öffentlich abrufbaren Belege.
