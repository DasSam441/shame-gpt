# 024: NanoRacer – gescheiterte Android-Installationshilfe und unvollständige Registrierungsberatung

Stand: 2026-09-30. Quelle: Chat „Bots für Rennen prüfen“, Thread `01a0ef38-8afc-7a11-8ab3-2d77d367ceb2`. Der Nutzer beauftragte ausdrücklich die Dokumentation dieses Fehlschlags im öffentlichen Repository. Private Adressen, Kontodaten und das ungeschwärzte Bildschirmfoto werden nicht veröffentlicht.

## Auftrag und tatsächliches Ergebnis

Der Nutzer ließ den aktuellen Unity-Spielstand als Android-APK bauen und wollte ihn auf seinem Handy nutzen. Der Build und die lokale Signaturprüfung bestanden. Die Installation scheiterte nach Nutzerangabe dennoch. Die anschließende Beratung löste weder die Installationssperre noch die Probleme bei der Entwicklerregistrierung. Eine erfolgreiche Installation wurde nicht nachgewiesen.

## Belegte Abfolge und Fehler

### 1. Ein sichtbarer Installationsknopf wurde als brauchbarer Weg empfohlen, ohne das Ergebnis zu kennen

Der Screenshot zeigte Google Play Protect mit dem Hinweis, dass Google von diesem Entwickler noch keine anderen Apps kenne, sowie „Trotzdem installieren“. Meine Antwort lautete: „Für deinen Test kannst du bei der von uns gebauten APK auf ‚Trotzdem installieren‘ tippen.“ Der Nutzer antwortete: „nein geht nicht“.

Der Screenshot belegt die Warnung und den Knopf, nicht dessen erfolgreiche Funktion. Ich konnte anschließend keine konkrete Ursache für die gescheiterte Installation feststellen. Die später vorgeschlagene USB-/ADB-Installation war ein alternativer Diagnoseweg, keine nachgewiesene Reparatur dieser Sperre. Der Nutzer lehnte diesen umständlichen Weg ab; ein Gerät war nicht verbunden.

### 2. Kostenlose Registrierung empfohlen, entscheidende Voraussetzung erst nach Nutzerwiderspruch recherchiert

Nachdem der Nutzer erklärt hatte, weder Kredit- noch Debitkarte zu besitzen, empfahl ich wiederholt das kostenlose Konto „Limited distribution“ für bis zu 20 autorisierte Geräte. Ich erklärte dabei nicht, dass auch dieses Konto ein Google-Zahlungsprofil verlangt.

Der Nutzer meldete daraufhin, dass Google trotzdem ein Zahlungsprofil anfordere und alte Adressen anzeige. Erst danach las ich die spezielle Anleitung vollständig und bestätigte die fehlende Voraussetzung.

**Technische Erklärung:** „Kostenlos“ beschreibt die Registrierungsgebühr. Ein Zahlungsprofil ist ein eigener Datensatz für rechtlichen Namen und Anschrift. Google verlangt dessen Verknüpfung ausdrücklich auch für Limited distribution. Gebührenfreiheit bedeutet deshalb nicht, dass kein Zahlungsprofil erforderlich ist. Eine Zahlungskarte, ein Zahlungsprofil und ein Entwicklerkonto sind unterschiedliche Dinge; meine Hilfestellung hatte diese Unterschiede nicht rechtzeitig erklärt.

### 3. Unbelegte Vermutung über mehrere Zahlungsprofile und unpassende Bedienanweisung

Ich verwies zunächst auf die Adressänderung im Zahlungscenter. Der Nutzer stellte klar: „da ist die richtige“. Darauf antwortete ich: „Dann zeigt die Registrierung möglicherweise ein anderes Zahlungsprofil“ und verlangte einen Vergleich der Zahlungsprofil-IDs. Der Nutzer meldete: „da steht keine ID“.

Die Vermutung war sprachlich als Möglichkeit markiert, aber weder mehrere Profile noch eine sichtbare ID in der tatsächlich geöffneten Registrierung waren belegt. Die Anleitung half deshalb nicht. Es gab keinen belegten Nachweis für ein falsches Profil, einen Cachefehler oder eine andere Ursache der abweichenden Adressanzeige. Danach verlangte ich erneut einen Screenshot, statt bereits einen verifizierten Lösungsweg liefern zu können.

### 4. Unnötige Belastung durch weitere Rückfragen und wiederholte Entschuldigungen

Der Nutzer hatte ausdrücklich kurze, konkrete Hilfe verlangt. Meine Antworten wechselten zwischen Vermutungen, zusätzlichen Bedienaufgaben und Entschuldigungen. Das Problem blieb ungelöst. Die Verantwortung für die fehlende Diagnose wurde dadurch praktisch wieder auf den Nutzer verlagert, obwohl ich zuvor einen einfachen Registrierungsweg nahegelegt hatte.

## Was tatsächlich technisch geprüft wurde – und was nicht

- Der damalige Build meldete `ANDROID_BUILD_OK`, Dateigröße 125767876 Bytes und SHA-256 `b36edb494d3ca083cf2c5c4e360028ef047c30cb576e656d9ab6cc1bbb0cbc02`.
- `apksigner verify --verbose` meldete eine gültige APK-v2-Signatur. `aapt dump badging` zeigte Paket `de.nanoracer.game`, ARM64, minSdk 25 und targetSdk 36.
- Der Abschluss sagte ausdrücklich, dass kein Android-Gerätetest erfolgt war. Es wurde also kein bestandener Gerätetest behauptet.
- Eine gültige Signatur belegt Integrität und Signierung, keine Play-Protect-Freigabe und keine erfolgreiche Installation.
- Beim späteren Versuch, das konkrete Zertifikat nachzuprüfen, war die APK am bisherigen Zielpfad nicht mehr vorhanden. Ursache und Verantwortlichkeit für ihr Fehlen sind nicht belegt. Die später gelesene Projekteinstellung `androidUseCustomKeystore: 0` beweist nicht rückwirkend das Zertifikat der Datei auf dem Handy.
- Googles dokumentierte Kategorie „Uncommon“ passt zum Wortlaut des Screenshots. Das ist keine vollständige Sicherheitsprüfung der APK und keine Erklärung dafür, warum die angebotene Installation beim Nutzer nicht funktionierte.
- Entwicklerregistrierung und Play-Protect-Bewertung sind getrennte Vorgänge. Ich hatte zwar eingeschränkt, dass eine Registrierung die Warnung nicht garantiert beseitigt; eine konkrete Eignung zur Behebung dieses Installationsfalls war aber überhaupt nicht nachgewiesen.

## Folgen und offener Stand

Der Nutzer wurde durch einen nicht ausreichend geprüften Registrierungsablauf und unpassende Anweisungen geführt. Die Installation blieb ungeklärt; ebenso die abweichenden Adressanzeigen. Weder eine Ursache noch eine erfolgreiche Reparatur darf aus diesem Verlauf behauptet werden. Es gibt keinen Beleg für eine Zahlung, eine abgeschlossene Registrierung oder einen Datenverlust.

## Quellen und Nachprüfbarkeit

Die kurzen Antwort- und Nutzerauszüge stammen aus dem genannten Chat. Der vollständige Chat wird hier nicht öffentlich gespiegelt; die Buildausgaben waren dort als Werkzeugausgaben sichtbar. Die folgenden offiziellen Quellen wurden im Verlauf tatsächlich geöffnet:

- [Google: Limited distribution – kostenlos, aber Zahlungsprofil für Namen und Adresse erforderlich](https://developer.android.com/developer-verification/guides/limited-distribution)
- [Google: Play-Protect-Warntexte, Kategorie Uncommon](https://developers.google.com/android/play-protect/warning-strings)
- [Google: Anschrift im Zahlungsprofil ändern](https://support.google.com/googlepay/answer/7644076?hl=de)
- [Google: Play-Console-Registrierung und akzeptierte Karten](https://support.google.com/googleplay/android-developer/answer/6112435)

## Erforderliche Korrektur der Arbeitsweise

Vor einer Kontoempfehlung den vollständigen Registrierungsablauf einschließlich Zahlungsprofil und Gerätefreigabe prüfen. Vor einer Bedienanweisung die tatsächlich vorhandenen Optionen berücksichtigen. Vermutungen nicht als nächsten sicheren Reparaturschritt behandeln. Build, Signatur, Installation, Play-Protect-Bewertung und Nutzerabnahme getrennt ausweisen. Eine ungelöste Ursache klar benennen, ohne den Nutzer wiederholt durch unbestätigte Wege zu schicken.
