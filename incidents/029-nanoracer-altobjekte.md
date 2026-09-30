# 029: Alte Pylonen und Reifen trotz Entfernungswunsch weiter sichtbar

Stand: 2026-09-30.

## Nutzerbefund und eigene Aussage

Der Nutzer beanstandete neben dem langsamen Bot, dass alte Pylonen und Reifen trotz vorheriger Anweisung weiterhin vorhanden seien. Ich bestätigte: „Nur die Editor-Knöpfe verschwanden. Im veröffentlichten Streckenpool stecken weiterhin 312 alte Pylonen und 71 Reifenstapel.“

## Technischer Befund

Das Entfernen von Bedienknöpfen entfernt weder gespeicherte Objektinstanzen noch den Code, der diese aus Streckendaten wieder erzeugt. Der sichtbare Istzustand und der gewünschte Zustand „überall weg“ wurden deshalb nicht erreicht. In der ersten gemeinsamen Bot-Veröffentlichung erwähnte ich sogar noch „die drei vergrößerten Pylonen“ als Teil parallel abgestimmter Änderungen.

## Verantwortung und Beleggrenze

Die ursprüngliche Entfernung beziehungsweise Knopfänderung stammte aus paralleler Projektarbeit. Dieser Chat belegt das verbliebene Problem, meine gemeinsame Release-Kommunikation und die anschließende Korrektur. Er enthält nicht den gesamten ursprünglichen Auftrag und dessen Implementierung. Deshalb wird die Urheberschaft der früheren Teilentfernung nicht pauschal diesem Chat zugeschrieben. Ebenso ist das genaue zeitliche Verhältnis der Vergrößerungs- und Entfernungsanweisungen hier nicht vollständig belegt.

## Korrektur

Nach ausdrücklicher Freigabe wurden alte Typen `cone` und `tires` aus aktiven Strecken-/Editor-Daten entfernt und ihr erneutes Einlesen beziehungsweise Veröffentlichen unterbunden. Neue Paketobjekte blieben erhalten. Der lokale Nachweis `Evidence/bot-pace-cleanup/data-integrity.json` meldet `remainingLegacyObjects: 0`, erhaltene andere Platzierungen und erhaltene Track-/Ghost-Schlüssel. Der dokumentierte Fehler wurde damit für den geprüften Datenumfang korrigiert; er wird nicht als heute weiterhin vorhanden dargestellt.

## Quellen und Grenzen

Quelle: vollständig durchblätterte Nutzer- und Assistentennachrichten im Chat „Bots für Rennen prüfen“, Thread `01a0ef38-8afc-7a11-8ab3-2d77d367ceb2`, bis zum Auftrag vom 30.09.2026, auch den übrigen Chat zu dokumentieren. Werkzeugprotokolle wurden gezielt geprüft, nicht jeder Build unabhängig wiederholt. Kurze Chatauszüge werden hier als Primärbelege wiedergegeben; der vollständige private Chat wird nicht gespiegelt.

Zusätzlicher Projektbeleg: [ONLINE-BOT.md am dokumentierten Release-Commit](https://github.com/DasSam441/nanoracer-unity/blob/c69d4d28596c6a4583dc49b173a0dccd64938941/Documentation/ONLINE-BOT.md). Dieser Link kann Repository-Zugriff erfordern. Lokale Evidence-Dateien sind keine öffentlich abrufbaren Belege.
