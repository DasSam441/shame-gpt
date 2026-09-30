# 014 — TimTime-Eingriffe blockierten wiederholt Carreras Guest-Login

**Befund:** wiederholte fehlgeschlagene Login-/Startansätze, deren Ursachen nicht alle gleich waren.

Die Versionsdokumente halten unter anderem fest:

- 1.2.86: Guest-Crash blieb nach einer Änderung der Racer-Referenz bestehen.
- 1.2.90: ein Hook auf RacerService.get_CarProfiles konnte vor abgeschlossenem Login in den RacerController schreiben.
- 1.2.91: bis zu 40 native Hooks wurden vor dem Guest-Klick installiert und blockierten den Login.
- 1.2.96: die als saubere Basis gedachte Version blockierte Guest weiterhin; der Fehler lag damit nicht an TimTime-API oder Manifest.
- 1.2.98: Guest blieb blockiert, obwohl der URL-Router-Aufruf entfernt wurde.
- 1.2.99: API-Routing-Aufrufe waren entfernt, aber der Launcher war weiterhin CarreraApiLogActivity statt des Original-Unity-Launchers.
- 1.3.0: die RacerService.CarProfiles-Brücke konnte vor dem fertigen Guest-/SaveState-Zustand eingreifen und wurde zurückgezogen.

**Technische Erklärung:** Mehrere Varianten griffen in unterschiedliche Punkte eines empfindlichen Ablaufs ein: Activity-Start, Hookinstallation, Login und Aufbau des Racer-Zustands. Ein Hook, der vor dem abgeschlossenen Login läuft, kann Carreras eigenen Zustand verändern oder den Guest-Pfad blockieren. Nicht jeder historische Absturz ist mit derselben Root Cause belegt.

**Warum mein Fehler:** Die Folge von Varianten zeigt, dass ich den geschützten Loginpfad zu früh und an zu vielen Stellen als Ansatz für den Import benutzte. Der spätere Projektbefund verlangte, Manifestdaten beim Start nur zu speichern und erst nach belegtem Abschluss des originalen Login-/SaveState-Pfads zu importieren.

**Zählgrenze:** Die sieben aufgelisteten Versionen sind einzeln dokumentierte schlechte Zustände, aber keine sieben unabhängig bewiesenen Ursachen. Zusätzlich gibt es in der Serie weitere nicht-freigegebene Zwischenstände.

**Quellen:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1.2.86_GUEST_CRASH_FOLLOWUP.md, 1.2.90_CARPROFILES_LOGINFEHLER.md, 1.2.91_START_HOOK_BLOCKIERT_GUEST.md, 1.2.96_KERNBASIS_RUECKZUG.md, 1.2.98_ROUTER_AUFRUF_ENTFERNT.md, 1.2.99_API_ROUTING_AUFRUFE_ENTFERNT.md und 1.3.0_GUEST_LOGIN_RUECKZUG.md.
