# 003 — JSON-Einstellungen ohne Wirkung

**Befund:** fehlerhaft. CarreraMod 1.6.49 / Code 195.

Das spätere Wirkungs-Audit verfolgte JSON-Felder bis zum DEX/Java-Code und nativen Setter. Es fand unter anderem:
- Root enabled schaltete Mods nicht sicher aus.
- module_handling-Fachwerte wurden nicht aus JSON gelesen.
- offtrack_brake.available wurde ignoriert.
- simulation_plus-Gas-Sprungwerte waren nicht an JSON gebunden.
- start_min und tx_byte_10 hatten keinen Parser-/Setterpfad.
- automatic_logging.on_start_min wurde immer auf false gesetzt.

**Technisch:** Vorhandene Dialoge und JSON-Schlüssel genügen nicht. Der Wert muss vom Parser bis zum wirksamen nativen Aufruf durchgereicht sein; ein fehlender JNI-Pfad oder überschreibender lokaler Wert macht ihn wirkungslos.

**Warum mein Fehler:** Die ausgelieferte Oberfläche suggerierte Einstellbarkeit, die das Programm nicht vollständig umsetzte. Erst die feldweise Wirkungsprüfung machte die Lücken sichtbar.

**Quelle:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1.6.49_JSON_WIRKUNGS_AUDIT.md; Stand 2026-08-20.
