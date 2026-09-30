# 020 — ARMv7-Firmware-Guard gab Carreras ursprüngliches Ergebnis nicht zurück

**Befund:** CarreraMod 1.6.6 war für ARMv7 funktional ungültig und wurde gesperrt.

Der Guard an UpdateFirmware.Run prüfte den ARMv7-memset-GOT-Slot, gab aber das ursprüngliche Task<bool> nicht an Carrera zurück. Damit änderte die Schutzroutine den Vertrag der Herstellerfunktion; die Änderung durfte nicht als gültig gelten.

**Technische Erklärung:** Ein Hook um eine asynchrone Methode muss die erwartete Task<bool>-Rückgabe erhalten. Eine Prüfung des GOT-Slots allein reicht nicht, wenn der Wrapper das Ergebnis der Originalfunktion verschluckt.

**Warum mein Fehler:** Ich konzentrierte mich auf den Speicher-/Hook-Schutz und prüfte nicht, dass der vollständige asynchrone Rückgabevertrag erhalten blieb.

**Quelle:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1.6.6_ARMV7_FIRMWARE_GUARD_GESPERRT.md.
