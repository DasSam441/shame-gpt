# 027: Verbesserung gegen schwachen Bot statt gegen Rennleistung bewertet

Stand: 2026-09-30.

## Aussage und verspäteter Gegencheck

Ich kündigte nach bestandenen lokalen Prüfungen die Veröffentlichung an: „Die neue Rennlinie brachte gegenüber dem zuletzt veröffentlichten Mittellinien-Bot zudem 5,6–30,1 % kürzere Rundenzeiten.“ Der Nutzer lehnte das Tempo ab und fragte anschließend nach höchstens drei Sekunden Abstand zu den Streckenrekorden.

Erst darauf räumte ich ein: „Das habe ich bisher nicht belegt – ich habe ihn mit dem vorherigen Bot verglichen, nicht mit den Streckenrekorden.“ Der Vergleich gleicher Streckenfassung und Fahrzeugklasse ergab nach der damaligen Auswertung sieben Überschreitungen des Drei-Sekunden-Abstands bei acht vergleichbaren Rekorden.

| Strecke / Klasse | Rekord | Bot | Rückstand |
|---|---:|---:|---:|
| Sophienring 1 / GT3 | 18,871 s | 28,815 s | 9,944 s |
| Sophienring 2 / GT3 | 17,172 s | 24,730 s | 7,558 s |
| EifelCombo / GT3 | 31,901 s | 46,142 s | 14,241 s |

## Technische Erklärung

Eine Verbesserung gegen einen bereits als unzureichend kritisierten Bot belegt keine angemessene absolute Rennleistung. Der Median der zweiten Verbesserung betrug etwa 16,47 %, nicht 30 %. Die Spanne wurde im Chat korrekt genannt; eine pauschale 30-%-Verbesserung auf jeder Strecke wurde nicht behauptet.

Zusätzlich schrieb ich in einer früheren Fortschrittsmeldung „rund 40–47 % schneller pro Runde“, obwohl ich eine Verringerung der Rundenzeit meinte. Diese Formulierung war unpräzise: 40 % weniger Zeit entspricht bei gleicher Strecke rund 66,7 % mehr Durchschnittsgeschwindigkeit. Der spätere Abschluss sprach korrekt von kürzeren Rundenzeiten. Die Prozentwerte der zwei Stufen hatten unterschiedliche Bezugsversionen und dürfen nicht einfach addiert werden.

## Folgen und tatsächlicher Stand

Die fachlich aussagekräftige Referenzprüfung kam zu spät. Der konkrete Drei-Sekunden-Wert wurde erst an dieser Stelle vom Nutzer genannt; ein früheres Versprechen dieses Zahlenwertes ist nicht belegt. Nach der Kritik wurde die Veröffentlichung vor dem Umschalten angehalten. Der aktuelle Stand wurde später ausdrücklich nur zum Sync-Test freigegeben und am 30.09.2026 um 01:46:41 UTC veröffentlicht. Das war keine Annahme der Rennleistung.

Die Quelle der Botzeiten ist `Evidence/bot-racing-line/pace-final.json` beziehungsweise `acceptance-summary.json`. Die Rekordzahlen stammen aus dem damals im Chat protokollierten lesenden Datenbankvergleich, nicht aus einer heute wiederholten Live-Abfrage. Die Spielphysik wurde nicht zur Erreichung der Zeiten beschleunigt.

## Quellen und Grenzen

Quelle: vollständig durchblätterte Nutzer- und Assistentennachrichten im Chat „Bots für Rennen prüfen“, Thread `01a0ef38-8afc-7a11-8ab3-2d77d367ceb2`, bis zum Auftrag vom 30.09.2026, auch den übrigen Chat zu dokumentieren. Werkzeugprotokolle wurden gezielt geprüft, nicht jeder Build unabhängig wiederholt. Kurze Chatauszüge werden hier als Primärbelege wiedergegeben; der vollständige private Chat wird nicht gespiegelt.

Zusätzlicher Projektbeleg: [ONLINE-BOT.md am dokumentierten Release-Commit](https://github.com/DasSam441/nanoracer-unity/blob/c69d4d28596c6a4583dc49b173a0dccd64938941/Documentation/ONLINE-BOT.md). Dieser Link kann Repository-Zugriff erfordern. Lokale Evidence-Dateien sind keine öffentlich abrufbaren Belege.
