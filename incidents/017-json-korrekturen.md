# 017 — Als vollständig bezeichnete JSON-Korrektur hatte weiter unwirksame Schalter

**Befund:** Folgefehler nach dem Audit von 1.6.49.

1.6.50 wurde als „vollständiger TimTime-JSON-Vertrag“ beschrieben. Der Nachtrag korrigierte das: Für simulation_plus.speed_steering_min_throttle_percent fehlte weiterhin ein nativer Endpunkt. Ein zweiter Nachtrag stellte fest, dass der Root-Schalter enabled:false fälschlich als globale Sperre über die einzelnen Mod-Schalter gelegt war.

1.6.52 entfernte diese globale Verzweigung. In 1.6.50 konnten daher Werte trotz erfolgreicher statischer DEX-, JSON- und Signaturprüfungen wirkungslos bleiben.

**Technische Erklärung:** Ein Feldpfad kann in Java/DEX vorhanden sein und trotzdem am nativen JNI-Endpunkt enden, der nicht exportiert wird. Außerdem änderte die globale Sperrlogik das Profilsemantik: Ein Root-Wert überschattete moduleigene available/enabled-Werte.

**Warum mein Fehler:** Ich nannte den Vertrag vollständig, obwohl nicht jedes Feld bis zum nativen Verbraucher belegt war, und die statischen Gesamtprüfungen fanden die fehlende Bindung nicht. Die nächste Korrektur führte eine eigene, neue Profilregression ein.

**Quellen:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1.6.50_JSON_VERTRAG_BUILD.md und docs/CARRERAMOD_1.6.52_OPTIONAL_MODS_PROFILE_ROUTING.md.
