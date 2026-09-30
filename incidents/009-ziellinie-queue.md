# 009 — Ziellinienereignisse gingen verloren oder liefen in eine alte Session

**Befund:** 1.6.68 bestand den statischen Vertrag, scheiterte aber im Gerätetest.

Der dokumentierte 1.6.68-Gerätetest zeigte, dass die aktuelle Überfahrt nicht ankam. Zugleich wurden rund 200 alte Queue-Ereignisse erfolgreich an eine vier Tage alte Session übertragen, die noch als aktiv markiert war. Später wurde festgestellt, dass der Client die aktuelle MAC verwarf, wenn das Java-Fahrzeugmapping noch fehlte; die verwaiste normale Session blockierte außerdem den virtuellen Fallback.

**Technisch:** Persistente Wiederholung war an sich vorgesehen, aber Sessionstatus und Fahrzeugzuordnung passten nicht mehr zum aktuellen Ereignis. Ein erfolgreicher HTTP-Versand alter Queue-Daten bedeutete nicht, dass das neue Event korrekt angekommen oder der Sessionstatus frisch war.

**Warum mein Fehler:** Ich behandelte Deduplizierung und persistente Queue als ausreichenden Zustellschutz und stellte 1.6.68 als fertige virtuelle Zeitnahme dar, obwohl der vollständige reale Ablauf noch nicht bewiesen war.

**Quelle:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1.6.68_VIRTUAL_TARGET_PREP.md und docs/CARRERAMOD_CURRENT_STATE.md; Gerätetest 2026-08-23, Korrektur in 1.6.69.
