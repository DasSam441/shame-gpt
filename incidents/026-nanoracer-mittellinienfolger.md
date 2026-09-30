# 026: Schnellerer Mittellinienfolger verfehlte Racing-Anforderung

Stand: 2026-09-30.

## Aussage und Gegenbefund

Nach der Tempokorrektur meldete ich „Ist korrigiert und veröffentlicht“ mit 40–47 % kürzeren Rundenzeiten. Darauf fragte der Nutzer, was das für ein Racing-Bot sei, der immer nur in der Mitte fahre. Ich bestätigte: „Der aktuelle Bot ist ein schneller Mittellinienfolger“ und „damit war deine Anforderung an einen Racing-Bot nicht erfüllt“.

## Technischer Fehler

Der Bot übernahm ausschließlich `track.centerline` als Grundspur. Vorhandene linke und rechte Streckenränder dienten nicht zur Auswahl einer Rennlinie. Mehr Tempo änderte diesen strukturellen Mangel nicht. Auch eine absichtliche Überholplanung fehlte der ersten Fassung, wie die Projektdokumentation ausdrücklich festhält.

Bereits das ursprüngliche Konzept hatte vorausschauendes Fahren und glaubwürdige Zweikämpfe beschrieben. Das anschließend freigegebene erste Online-Teilkonzept war enger und nannte vor allem reguläre Runden und Hindernisbremsen. Deshalb wird hier kein eindeutig nachgewiesener Verstoß gegen eine explizite Erstversions-Überholzusage behauptet. Belegt ist die unzureichend offengelegte Lücke zwischen dem gewünschten Racing-Bot und dem ausgelieferten Mittellinienfolger.

## Korrektur und Grenze

Erst nach der Kritik folgten eine innerhalb der Streckenbreite optimierte Linie und eine zustandsbehaftete Überholplanung. Sie waren geometrisch auf geringe Krümmung ausgerichtet, nicht nachweislich auf minimale Rundenzeit. Die späteren 54 Fälle/238 Runden und 15 Verkehrsfälle belegten die getesteten Manöver, nicht die geforderte Rekordnähe. Diese blieb unerfüllt (Fall 027).

## Quellen und Grenzen

Quelle: vollständig durchblätterte Nutzer- und Assistentennachrichten im Chat „Bots für Rennen prüfen“, Thread `01a0ef38-8afc-7a11-8ab3-2d77d367ceb2`, bis zum Auftrag vom 30.09.2026, auch den übrigen Chat zu dokumentieren. Werkzeugprotokolle wurden gezielt geprüft, nicht jeder Build unabhängig wiederholt. Kurze Chatauszüge werden hier als Primärbelege wiedergegeben; der vollständige private Chat wird nicht gespiegelt.

Zusätzlicher Projektbeleg: [ONLINE-BOT.md am dokumentierten Release-Commit](https://github.com/DasSam441/nanoracer-unity/blob/c69d4d28596c6a4583dc49b173a0dccd64938941/Documentation/ONLINE-BOT.md). Dieser Link kann Repository-Zugriff erfordern. Lokale Evidence-Dateien sind keine öffentlich abrufbaren Belege.
