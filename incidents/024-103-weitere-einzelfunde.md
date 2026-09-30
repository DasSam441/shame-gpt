# 80 zusätzliche Einzelfunde aus CarreraMod und TimTime

Stand: 2026-09-30. Diese Liste ergänzt die 23 Fallberichte. Sie zählt **Einzelfunde und konkret gescheiterte Zustände**, nicht 80 unabhängige Root Causes. Mehrere Punkte gehören zu denselben Fehlerfamilien; solche Beziehungen sind nicht als verschiedene technische Ursachen ausgegeben. Unbelegte Vermutungen sind ausgeschlossen. Nutzernamen, Gerätekennungen und MAC-Adressen aus den Chats sind hier nicht übernommen.

## Ältere CarreraMod-Versuche

24. **1.2.67 – TimTime-Fahrzeuge nicht in Unity sichtbar.** Der Live-Test lud Freigaben und Bilder, aber die Fahrzeuge erschienen nicht in der originalen Fahrzeugliste. Quelle: CARRERAMOD_1.2.67_TIMTIME_FILTER_TEST.md.
25. **1.2.70 – Öffnen der Autos stürzte ab.** Der neu eingebaute Inline-Hook war im Gerätetest nicht startfähig. Quelle: CARRERAMOD_1.2.70_INLINE_HOOK_CRASH.md.
26. **1.2.74 – TryGetRacer-Hook crashte beim Start.** Der Kandidat wurde zurückgezogen. Quelle: CARRERAMOD_1.2.74_TRYGETRACER_CRASH.md.
27. **1.2.75 – reduzierter Hook beseitigte den Absturz nicht.** Der Folgeversuch blieb ebenfalls nicht verwendbar. Quelle: CARRERAMOD_1.2.75_REDUZIERTER_CRASH_FOLLOWUP.md.
28. **1.2.76 – SaveState.Racer-Eingriff crashte beim Start.** Die neue Fahrzeugintervention lag im betroffenen Startpfad. Quelle: CARRERAMOD_1.2.76_SAVESTATE_RACER_CRASH.md.
29. **1.2.77 – geänderter Speicherweg ließ denselben Crash bestehen.** Die erste Korrektur löste das Problem nicht. Quelle: CARRERAMOD_1.2.77_STORAGE_KORREKTUR_CRASH.md.
30. **1.2.80 – Katalog-ID im falschen Feld.** Das Schreiben nach TechnicalName statt Id führte zu einer schwarzen Fahrzeugansicht. Quelle: CARRERAMOD_1.2.80_RACERCONTROLLER_ERSTVERSUCH.md.
31. **1.2.81 – Feldkorrektur genügte nicht.** Die schwarze Ansicht blieb wegen reentranten Syncs während des UI-Aufbaus bestehen. Quelle: CARRERAMOD_1.2.81_KATALOG_ID_KORREKTUR.md.
32. **1.2.82 – originaler Anmelden-Button reagierte nicht.** Der frühe Sync vor CarCollection.OnEnable blockierte den Loginpfad. Quelle: CARRERAMOD_1.2.82_SYNC_VOR_UI_REGISTRIERUNG.md.
33. **1.2.83 – Threadwechsel löste die Loginblockade nicht.** Trotz Installation auf dem Android-Hauptthread blieb der Guest-Button blockiert. Quelle: CARRERAMOD_1.2.83_HOOKS_AUSSERHALB_NETZWERKTHREAD.md.
34. **1.2.85/1.2.86 – Verschieben in den Folgeframe brachte keine belastbare Behebung.** Der Folgestand hielt weiterhin einen Guest-Absturz fest. Quelle: CARRERAMOD_1.2.85_SYNC_NACH_BIND_FRAME.md und CARRERAMOD_1.2.86_GUEST_CRASH_FOLLOWUP.md.
35. **1.2.89 – originaler Fahrzeugabruf war keine funktionierende TimTime-Integration.** Die Dokumentation sagt ausdrücklich, dass der Funktionsnachweis fehlte. Quelle: CARRERAMOD_1.2.89_ORIGINALER_FAHRZEUGABRUF.md.
36. **1.2.90 – CarProfiles-Hook lief vor Loginabschluss.** Er konnte während Guest in Carreras RacerController schreiben. Quelle: CARRERAMOD_1.2.90_CARPROFILES_LOGINFEHLER.md.
37. **1.2.92 – vermeintlich passiver Observer war nicht nachgelagert.** OnStateEnter lieferte einen Task; die Hooks liefen weiterhin in der Login-State-Machine. Quelle: CARRERAMOD_1.2.92_PASSIVER_NACHLOGIN_WAECHTER.md.
38. **1.2.94 – Annahme über LoadCars nicht ausreichend belegt.** Der spätere Nachweis verwirft die damalige Annahme; für 1.2.94 selbst sind weder APK-Hash noch Gerätetest belegt. Quelle: CARRERAMOD_1.2.94_UNVOLLSTAENDIG_BELEGTER_ZWISCHENSTAND.md.
39. **1.2.95 – nativer Absturz beim Guest-Klick.** Der neue statische Rücksprungpfad wurde verworfen. Quelle: CARRERAMOD_1.2.95_BACKENDLOGIN_NATIVE_CRASH.md.
40. **1.2.96 – Rückzug auf eine „saubere“ Basis beseitigte Guest-Fehler nicht.** Das schloss die TimTime-API als Ursache aus, bewies aber keine funktionierende Herstellerbasis. Quelle: CARRERAMOD_1.2.96_KERNBASIS_RUECKZUG.md.
41. **1.2.97 – nativer URL-Router verursachte Sofortcrash.** Die Laufzeitänderung einer Unity-Code-Seite war ein Kandidat; der Build wurde zurückgezogen. Quelle: CARRERAMOD_1.2.97_RACERS_URL_ROUTER_CRASH.md.
42. **1.2.98 – Router-Aufruf entfernen reichte nicht.** Der Guest-Login blieb blockiert. Quelle: CARRERAMOD_1.2.98_ROUTER_AUFRUF_ENTFERNT.md.
43. **1.2.99 – ursprünglicher Launcher nicht wiederhergestellt.** Trotz entfernter Routing-Aufrufe blieb CarreraApiLogActivity statt UnityPlayerActivity als Launcher eingetragen. Quelle: CARRERAMOD_1.2.99_API_ROUTING_AUFRUFE_ENTFERNT.md.
44. **1.3.0 – CarProfiles-Brücke konnte vor fertigem Guest-/SaveState-Zustand eingreifen.** Der Ansatz wurde zurückgezogen. Quelle: CARRERAMOD_1.3.0_GUEST_LOGIN_RUECKZUG.md.

## Einzelne fehlerhafte JSON-Pfade in 1.6.49

45. **POWERBAND-Startwert blieb veraltet.** Eine spätere Änderung von enabled aktualisierte einen bereits lokal gespeicherten Zustand nicht. Quelle: CARRERAMOD_1.6.49_JSON_WIRKUNGS_AUDIT.md.
46. **MODULE enabled fehlte im JSON-Import.** Der Mod konnte serverseitig nicht gestartet werden. Dieselbe Quelle.
47. **MODULE ignore_modules fehlte im JSON-Import.** Der Wert existierte nur im lokalen Dialog. Dieselbe Quelle.
48. **MODULE check_position_valid fehlte im JSON-Import.** Der Wert wurde nicht aus TimTime übernommen. Dieselbe Quelle.
49. **MODULE next_modules_zero fehlte im JSON-Import.** Auch dieser Schalter blieb lokal statt servergesteuert. Dieselbe Quelle.
50. **BANDEN TEST enabled wurde nur initial gelesen.** Spätere Serveränderungen aktualisierten die aktive Native-Konfiguration nicht verlässlich. Dieselbe Quelle.
51. **OFFTRACK available wurde ignoriert.** available:false konnte den Knopf und vorhandenen lokalen Zustand nicht sicher stilllegen. Dieselbe Quelle.
52. **SIM+-Schwellenwert hatte keinen belegten JNI-Endpunkt.** Der Java-Aufruf nativeSetSpeedReductionThrottlePercent fand keinen passenden exportierten Namen in der APK. Dieselbe Quelle.
53. **SIM+-Wert gas_step_percent fehlte.** Der Gas-Sprung-Dialog las ihn nicht aus JSON. Dieselbe Quelle.
54. **SIM+-Wert gas_step_window_ms fehlte.** Der Zeitfensterwert war nicht servergesteuert. Dieselbe Quelle.
55. **SIM+-Wert gas_step_ignore_steering_ms fehlte.** Die JSON-Vorgabe wurde nicht eingelesen. Dieselbe Quelle.
56. **SIM+-Wert gas_step_cooldown_ms fehlte.** Der Cooldown blieb außerhalb des JSON-Vertrags. Dieselbe Quelle.
57. **SIM+-Flag available fehlte.** Der Knopf wurde ungeachtet der TimTime-Verfügbarkeit installiert. Dieselbe Quelle.
58. **SIM+-Flag enabled fehlte.** Das Serverprofil konnte den Startzustand nicht setzen. Dieselbe Quelle.
59. **start_min besaß keinen Parser-/Setterpfad.** Der JSON-Block hatte in der APK keine Wirkung. Dieselbe Quelle.
60. **tx_byte_10 besaß keinen Parser-/Setterpfad.** Auch dieser angebotene JSON-Block blieb wirkungslos. Dieselbe Quelle.
61. **automatic_logging.on_start_min wurde fest auf false gesetzt.** Die sichtbare Konfigurationsoption wurde nicht angewendet. Dieselbe Quelle.
62. **api.racers wurde wie eine eigenständige Route behandelt, war aber nur ein Alias.** Der Router las dafür keine separate Route. Dieselbe Quelle.

## Weitere Vertrags- und Buildfehler

63. **1.6.42 ersetzte die Native-Bibliothek durch einen inkompatiblen historischen Stand.** Dadurch war die erwartete OFFTRACK-Gegenstelle nicht bereit. Quelle: CARRERAMOD_1.6.42_FUNKTIONS_DEBUG_JSON_AUDIT.md.
64. **1.6.42 konnte den 20-Hz-Logger nicht starten.** startLogging() gab wegen des fehlenden Observer-Bereitschaftsstatus false zurück. Dieselbe Quelle.
65. **1.6.42 zeigte Fallbackwerte als scheinbare Konfiguration.** 80/50/80 belegte nicht, dass die TimTime-Werte geladen waren. Dieselbe Quelle.
66. **1.6.42 enthielt POWERBAND trotz dokumentierter Stilllegung.** Der Knopf und Übergabepfad waren noch vorhanden. Quelle: CARRERAMOD_POWERBAND_STILLLEGUNG.md.
67. **1.6.42 enthielt MODULE trotz dokumentierter Stilllegung.** Dialog und JSON-Verarbeitung waren noch vorhanden. Quelle: CARRERAMOD_MODULE_HANDLING_STILLLEGUNG.md.
68. **1.6.42 enthielt BANDEN TEST trotz dokumentierter Stilllegung.** Knopf, Dialog und Native-Übergabe waren noch vorhanden. Quelle: CARRERAMOD_BANDEN_TEST_STILLLEGUNG.md.
69. **1.6.50 wurde zu früh „vollständiger JSON-Vertrag“ genannt.** Für simulation_plus.speed_steering_min_throttle_percent fehlte weiterhin der native Endpunkt. Quelle: CARRERAMOD_1.6.50_JSON_VERTRAG_BUILD.md.
70. **1.6.50 legte Root-enabled:false fälschlich über Mod-Schalter.** Ein globaler Wert überschattete die eigenen available/enabled-Paare. Quelle: CARRERAMOD_1.6.52_OPTIONAL_MODS_PROFILE_ROUTING.md.
71. **1.6.52 ließ SIM+-Gas-Sprung beim gemeinsamen UI-Refresh aus.** Kam das Manifest nach Erzeugung des Overlays, erschien der Knopf nicht. Dieselbe Quelle.
72. **1.6.43 scheiterte an JNI-Namensabweichungen.** Java deklarierte getState/setValues usw., die Native-Bibliothek exportierte anders benannte Symbole; der erste Konfigurationsaufruf löste UnsatisfiedLinkError aus. Quelle: CARRERAMOD_1.6.43_NATIVE_BOUNDARY_REPAIR.md.
73. **1.6.65 erster APK-Kandidat trug weiter die alte Versionsnummer.** Apktool verwendete einen gecachten Manifestblock; der Kandidat wurde zwar abgefangen und nicht ausgeliefert, der Buildprozess war aber fehleranfällig. Quelle: CARRERAMOD_1.6.65_BUILD.md.
74. **1.6.20 verlor beim Repack classes5.dex.** Der Kandidat enthielt dadurch den Pairing-/Manifest-Client nicht. Quelle: CARRERAMOD_1_6_GESAMTAUDIT_2026-08-16.md.
75. **1.6.27 überschrieb classes5.dex.** Der neue Debug-DEX ließ den TimTimeVehicleClient aus dem APK-Paket verschwinden. Dieselbe Quelle.

## Frühere Hook- und Formelversuche

76. **Direkte Dashboard-/UI-Gang-Hooks lieferten keine verwertbaren Werte oder crashten.** Die Anzeigeebene war kein stabiler Gang-Datenpfad. Quelle: docs/chat-history/README.md, „RPM und Gang“.
77. **Gear-Store-Hooks crashten oder beschädigten die Schaltlogik.** Quelle: dieselbe Chat-Chronik.
78. **Direkte Sprünge in originale Up-/Downshift-Blöcke crashten.** Der Upshift-Block erwartete internen Kontext, den der Hook nicht bereitstellte. Quelle: dieselbe Chat-Chronik, „Manuelles Schalten“.
79. **Direktes Schreiben in Gearbox.gear war instabil.** Die Chat-Chronik markiert diesen Ansatz als nicht funktionierend. Quelle: dieselbe Chat-Chronik.
80. **Engine.CalculateTorque auf null zu setzen begrenzte die echte Fahrleistung nicht wie beabsichtigt.** Quelle: dieselbe Chat-Chronik, „5800-RPM-Begrenzung“.
81. **InputController.get_Throttle war der falsche Stellpunkt.** Der Ansatz wurde verworfen. Quelle: dieselbe Chat-Chronik.
82. **RacerDriveData.Kph einzufrieren führte zu unplausiblem Fahrverhalten.** Quelle: dieselbe Chat-Chronik.
83. **Die alte TX-Byte-10-Tabelle war nicht belastbar.** Spätere Logs zeigten Bytewerte, die nicht zum gleichzeitig protokollierten steering_assist = 0 passten. Quelle: docs/chat-history/README.md, „TX-Byte 10“.
84. **RawX-Overlaylabels waren nicht sauber der Bytequelle zugeordnet.** 0x21/0x22/0x23 wurden zeitweise als w23/w24/w25 angezeigt; die Zuordnung musste neu geprüft werden. Quelle: dieselbe Chat-Chronik, „Gyro / RawX“.
85. **Car.acceleration wurde als Stellgröße missverstanden.** Die Chronik korrigiert: Es ist ein Messwert; Car.AddForce betrifft Beschleunigungskraft. Quelle: dieselbe Chat-Chronik.
86. **Lenkungsformeln erzeugten unnatürliches oder asymmetrisches Verhalten.** Die getesteten starken Eingriffe wurden nicht als brauchbare Fahrfunktion übernommen. Quelle: dieselbe Chat-Chronik, „Lenkungs- und Byte8-Experimente“.

## Direkte Korrekturen aus späteren Chats

87. **Falsche TimTime-Fahrzeugzahl.** Ich meldete zunächst 9 Fahrzeuge und leitete daraus einen Importfehler ab; der nachträgliche Abgleich zeigte 36 Fuhrparkeinträge und 32 Hybrid-Fahrzeuge. Chat „Behebe fehlende TT-Autos“.
88. **Falsche lokale Nachbildung als Serverbefund ausgegeben.** Ich bezeichnete die 9er-Menge zunächst als tatsächlichen TimTime-Manifestfehler und korrigierte später: Sie stammte aus meiner lokalen Nachbildung. Derselbe Chat.
89. **Diagnose an den Nutzer delegiert, obwohl vorhandene Befunde weiter geprüft werden konnten.** Ich forderte Handyfotos/USB-Nachweise an; der Nutzer sagte, das gehe nicht und die App sei wiederholt mit Fahrzeugimport getestet worden. Derselbe Chat.
90. **Audio-Auftrag zunächst auf die falsche Anwendung bezogen.** Auf „alle Audio-Einstellungen geprüft?“ antwortete ich zunächst für die App; der Nutzer stellte klar: „in TimTime, nicht in der App“. Chat „Audioeinstellungen speichern beheben“.
91. **Dauerhaftes Speichern aus einem Funktionsaufruf abgeleitet.** Ich sah saveState() und behauptete Persistenz, ohne die bestätigte Serverantwort abzuwarten. Späterer Serverbefund: HTTP 409. Chat „Hallo Tim … Runden …“.
92. **Audio-Fix nach bloßer Syntax-/Oberflächenprüfung als abgeschlossen gemeldet.** Der Nutzer meldete danach, dass nicht einmal Spracheinstellungen gespeichert wurden. Chat „Audioeinstellungen speichern beheben“.
93. **Clubstrecken als übernommen behandelt, obwohl sie in der Rennleitungs-Auswahl fehlten.** Das wurde erst später als separater Importpfad erkannt. Chat „Hallo Tim … Runden …“.
94. **Sessionzuordnung bei einem Ziellinienfahrer falsch erklärt.** Ich behauptete zeitweise, er sei der neuen Session nicht beigetreten; die gespeicherten Zeitstempel zeigten den Beitritt. Chat „Hallo Tim … Runden …“.
95. **Vorherige Session-ID als Ursache behauptet, ohne Beleg.** Ich musste zurücknehmen, dass die Geräte eine alte ID gesendet hätten. Derselbe Chat.
96. **MRC-/NFC-Kennung fälschlich als Voraussetzung für Live-Target behandelt.** Der Nutzer wies darauf hin, dass eine Ziellinienerkennung keinen MRC-Chip benötigt; Server- und Browserfilter waren tatsächlich vermischt. Derselbe Chat.
97. **Erstes LapCompleted fälschlich als fehlendes Ereignis beschrieben.** Der Nutzer hatte das vollständige Ereignis wiederholt erwähnt; der spätere Befund zeigte einen TimTime-Auswertungsfehler. Derselbe Chat.
98. **Live-Target- und MRC-Zeitnahme vermischt.** Ich erklärte den Dashboard-/Rundenausfall zunächst mit der falschen Zeitnahmeart. Derselbe Chat.
99. **Falsche Erklärung für fehlenden Beobachter-Umschalter.** Ich sagte, es gebe nur eine aktive Quelle; tatsächlich existierte die virtuelle Ziellinienzeitnahme, war aber nicht an den Beobachter-Livekanal angeschlossen. Chat „Behebe Zeitnahme-Umschaltung“.
100. **Pairing-Code-Erzeugung ohne ausreichende Daten als unwahrscheinlich dargestellt.** Auf eine ausdrücklich als Frage markierte Nachfrage schob ich die Ursache zur App-Weiterleitung, ohne den Code-Erzeugungspfad belegt zu haben. Chat „Pairing-Code-Erzeugung prüfen“.
101. **Pairing als „gefixt“ gemeldet, obwohl die vorherige Nutzernachricht nur eine Frage war.** Die Antwort behauptete einen Code-/QR-Ablauf, ohne in dieser Antwort einen konkreten Code- oder App-Test zu nennen. Derselbe Chat.
102. **APK 1.2.69 trotz Projektregel ohne Build-Auftrag erstellt.** Ich baute und signierte einen Android-Kandidaten während der Live-Target-Arbeit; der Nutzer stellte klar, dass keine App gebaut werden sollte. Chat „Plan Live-Target-Übertragung“. Das ist ein zweiter dokumentierter Build-Auftragsfehler, getrennt von Bericht 004.
103. **Falschen Zeitvertrag in den Live-Target-Payload übernommen.** Der erste Android-Pfad sendete lapTimeMs; der Nutzer korrigierte, dass nur der Zeitstempel der Überfahrt gesendet werden sollte. Die Rundenzeit wird aus zwei Zeitstempeln gebildet. Derselbe Chat.

## Einordnung der 80 Punkte

Einige Einträge sind gescheiterte Folgestände derselben Ursache (zum Beispiel Login-Hooks oder Fahrzeugimport); andere sind getrennte JSON-Werte, falsche Tatsachenbehauptungen oder Auftragsfehler. Die Liste behauptet deshalb **80 dokumentierte Einzelfunde**, nicht 80 voneinander unabhängige Grundursachen. Für jeden Punkt wird die konkrete Versionsnotiz oder der zugängliche Chat genannt. Projektcode, APKs, Nutzernamen und MAC-Adressen werden nicht gespiegelt.
