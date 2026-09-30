# 022 — Dalvik-Registerfehler ließ Debug-APKs schon beim Laden scheitern

**Befund:** zwei getrennte VerifyError-Builds.

CarreraMod 1.5.6 verwendete in createOverlayTools zu wenige Dalvik-Register. Ein Graph-Button konnte dadurch die Activity-Referenz überschreiben; Android brach mit VerifyError ab.

CarreraMod 1.6.0 hatte denselben Fehlertyp an einer anderen Stelle: setTimTimeDriverDebugAllowed(boolean) überschieb die Activity-Referenz mit einem String, und Android verwarf die Klasse beim Zugriff auf debugApprovedMac. Der Fix 1.6.1 gab dem Setter ein eigenes lokales Register.

**Technische Erklärung:** Dalvik-Register sind typisierte Speicherplätze für Parameter und lokale Werte. Werden Register falsch gezählt oder Activity-Referenz und String verwechselt, kann die VM die Methode beziehungsweise ganze Klasse beim Laden als ungültig ablehnen.

**Warum mein Fehler:** Register- und Typbeziehungen wurden vor dem Build nicht ausreichend geprüft. Die Probleme waren vor jeder Gerätefunktion ein Startblocker.

**Quellen:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1.5.6_GRAPH_REGISTERFEHLER.md, docs/CARRERAMOD_1.6.0_DRIVER_DEBUG_VERIFYERROR.md und docs/CARRERAMOD_1.6.1_DRIVER_DEBUG_REGISTERFIX.md.
