# 010 — Verpackungsfehler verdoppelte beinahe die APK-Größe

**Befund:** Fehler in 1.6.71, erst beim folgenden Build erkannt.

Die nachträgliche Verpackungsprüfung dokumentiert, dass 1.6.71 zusätzlich so-Bibliotheken als unkomprimierbar markierte. Dadurch wuchs die APK auf rund 299 MB statt der üblichen rund 135 MB. Das Dokument erklärt ausdrücklich, dass 1.6.71 kein gültiger Verpackungsreferenzstand ist; der Fehler wurde beim direkten Vergleich im Build 1.6.72 gefunden.

**Technisch:** apktool.yml legte für die nativen Bibliotheken eine falsche ZIP-Kompressionsregel fest. Die Anwendung mochte weiterhin starten, aber das Distributionsartefakt wurde mehr als doppelt so groß.

**Warum mein Fehler:** Die Abnahme prüfte Signatur, Alignment, DEX und Funktionspfade, übersah aber den Vergleich der Paketgröße und die Abweichung der Kompressionsregeln. Der Bericht nennt die Korrektur erst im Nachfolger.

**Quelle:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1.6.71_PAIRING_1.4.4_PATH.md, „Nachträglicher Verpackungsbefund“; 2026-08-24.
