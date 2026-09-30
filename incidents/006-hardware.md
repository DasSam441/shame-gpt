# 006 — Unity-Buildfähigkeit mit Gerätefunktion vermischt

**Befund:** unbelegt und zu pauschal.

In frühen Antworten plante ich Unity-Ausgaben für Web, Windows, macOS, Android und iOS mit Bluetooth-, NFC- und USB-Adaptern, bevor konkrete Gerätepfade geprüft waren. Der Nutzer musste betonen, dass diese Verbindungen Kernfunktionen sind und wirklich funktionieren müssen.

Die vorhandenen TimTime-Unterlagen belegen Webfunktionen und Browsergrenzen, aber keinen erfolgreichen Unity-Gerätezugriff auf allen Plattformen. Für reale Gerätekombinationen, besonders WebGL/iOS und USB auf Mobilgeräten, standen Tests noch aus.

**Technisch:** Einen Unity-Build für ein Zielsystem erzeugen zu können beweist nicht, dass dessen APIs, Berechtigungen und Hardwarezugriff die benötigten Abläufe tragen.

**Warum mein Fehler:** Ich vermischte allgemeine Plattformfähigkeit mit projektspezifischem Funktionsnachweis und gab dem Plan mehr Sicherheit, als die Belege hergaben.

**Quelle:** zugänglicher Chat „TimTime auf Unity umstellen“, September 2026; öffentliches DasSam441/TimTime, Stand 2026-09-30. Dieser Fall behauptet nicht, dass Unity solche Clients grundsätzlich nicht bauen kann.
