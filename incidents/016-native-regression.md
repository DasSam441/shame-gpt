# 016 — Native Bibliotheksersetzung brach vorhandene Funktionen; Folgefix stürzte beim Start ab

**Befund:** Regression in 1.6.42 und Startblocker in 1.6.43.

1.6.42 ersetzte für OFFTRACK BRK die gemeinsame carreraapilog-Bibliothek durch eine ältere Variante. Dieselbe Bibliothek lieferte auch den Zustand für 20-Hz-Logging und BANDEN TEST. Auf dem Gerät startete der Logger nicht; der Hook meldete nicht bereit, und Werte fielen auf Standardwerte zurück.

1.6.43 sollte OFFTRACK in eine getrennte Brücke verschieben. Der Build stürzte aber sofort beim Start ab. Die dokumentierte Ursache war ein JNI-Namensfehler: Java deklarierte getState/setValues/isEnabled/setEnabled, die Bibliothek exportierte nur die Varianten mit vorangestelltem native. Der erste Aufruf löste UnsatisfiedLinkError aus.

**Warum mein Fehler:** Die Reparatur behandelte einen benötigten nativen Export durch Austausch einer ganzen Bibliothek und übersah deren andere Verbraucher. Beim folgenden Build waren kompilierte JNI-Symbole nicht mit den Java-Deklarationen abgeglichen.

**Technische Grenze:** Die Dokumente belegen beide konkreten Mechanismen. Sie beweisen nicht, dass jede weitere Funktion der jeweiligen APK betroffen war.

**Quellen:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1.6.42_FUNKTIONS_DEBUG_JSON_AUDIT.md und docs/CARRERAMOD_1.6.43_NATIVE_BOUNDARY_REPAIR.md.
