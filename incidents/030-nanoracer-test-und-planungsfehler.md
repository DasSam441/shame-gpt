# 030: Mehrere fehlerhafte Bot-Testaufbauten und interne Fahrplanungsversuche

Stand: 2026-09-30.

## Einordnung

Diese Befunde wurden während der Arbeit entdeckt und korrigiert. Sie sind konkrete fehlgeschlagene Versuche, aber kein Beleg dafür, dass genau diese Zwischenstände live ausgeliefert wurden oder die finalen Testzahlen erfunden waren.

| Befund | Technische Ursache | Auswirkung und Korrektur |
|---|---|---|
| Erstes stehendes Hindernis neben der Spur | In einer Kurve entlang der bisherigen Fahrtrichtung statt auf der tatsächlichen Route platziert | Vorbeifahrt war kein Nachweis des beabsichtigten Anhaltens. Fixture auf Route korrigiert. |
| Hochgeschwindigkeits-Bremsfixture erreichte keine 180 km/h | Grob polygonal abgetastete Kurve erzeugte künstliche Krümmungsspitzen | Kein gültiger Bremsnachweis. Dicht abgetastete analytische Kurve verwendet. |
| Neue Linie berührte Kanada-/Peak-Banden | Globale Normalenstrahlen trafen eine benachbarte Haarnadelstrecke | Unstetige Routenpunkte. Zusammengehörige linke/rechte Randabschnitte und Kontinuitätsprüfung ergänzt. |
| Überholen bewegter Gegner blieb aus | Spurwechselbeginn wurde bei jeder Planung erneut auf die aktuelle Position gelegt | Übergang wurde immer nach hinten verschoben; fester räumlicher Beginn eingeführt. |
| Angeblicher Nebeneinander-Test war falsch aufgestellt | `Physics.SyncTransforms` übernahm einen zuvor geänderten Transform und hob die gewünschte Rigidbody-Position auf | Gegner stand voraus, nicht daneben. Frühere Testeinträge sind ungültig; Startposition und Anfangsabstand wurden danach ausdrücklich geprüft. |
| Spätes Hindernis in enger Kurve führte zu Kontakt | Abstand im Referenzstreckenmodell allein erfasste reale Fahrzeugkörper nicht ausreichend | Vollständige Körpersweeps und größere seitliche Reserve eingeführt; derselbe strenge Kontakttest wiederholt. |

## Warum das relevant ist

Ein grüner Test kann den falschen Aufbau prüfen. Die Nebeneinander-Prüfung benötigte eine Vorbedingung für die tatsächliche relative Startposition. Eine Strecke ohne Bandenkontakt kann außerdem immer noch über eine Kurvenecke abkürzen; deshalb kamen Fahrzeugumrissprüfungen hinzu.

## Verbleibende Grenzen der finalen Prüfungen

Die Umrissprüfung erfolgte mit 10 Hz und erst nach der ersten Runde. Null gemessene Überschreitungen ist damit keine lückenlose Garantie für jeden Physikschritt und jede Anfangssituation. Verkehrsprüfungen kontrollierten dagegen Überlappungen pro Physikschritt. Auch 54 Streckenfälle und 15 Verkehrsfälle sind keine vollständige Untersuchung aller möglichen Verkehrssituationen.

Die endgültigen lokalen Prüfungen bestanden nach den Korrekturen. Es gab ausdrücklich keine Live-Spielprüfung. Das entsprach der Nutzeranweisung und ist nicht selbst als Regelverstoß zu werten. Datei-/Hashprüfung und aktiver Serverprozess beweisen keine Synchronisationsqualität auf dem Endgerät.

Belegdateien: `Evidence/bot-racing-line/matrix-curvature.log`, `traffic-extended.log`, `network-final.log`, `matrix-final.log`, `traffic-body-clearance.log`, `network-body-clearance.log`; sowie die dokumentierten Fehlerabschnitte in ONLINE-BOT.md. Frühere falsche Nebeneinander-Ergebnisse werden nicht als Endabnahme verwendet.

## Quellen und Grenzen

Quelle: vollständig durchblätterte Nutzer- und Assistentennachrichten im Chat „Bots für Rennen prüfen“, Thread `01a0ef38-8afc-7a11-8ab3-2d77d367ceb2`, bis zum Auftrag vom 30.09.2026, auch den übrigen Chat zu dokumentieren. Werkzeugprotokolle wurden gezielt geprüft, nicht jeder Build unabhängig wiederholt. Kurze Chatauszüge werden hier als Primärbelege wiedergegeben; der vollständige private Chat wird nicht gespiegelt.

Zusätzlicher Projektbeleg: [ONLINE-BOT.md am dokumentierten Release-Commit](https://github.com/DasSam441/nanoracer-unity/blob/c69d4d28596c6a4583dc49b173a0dccd64938941/Documentation/ONLINE-BOT.md). Dieser Link kann Repository-Zugriff erfordern. Lokale Evidence-Dateien sind keine öffentlich abrufbaren Belege.
