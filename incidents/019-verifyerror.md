# 019 — Driver-Debug-Setter machte die Activity-Klasse ungültig

**Befund:** CarreraMod 1.6.0 wurde wegen VerifyError gesperrt.

Die neue Methode setTimTimeDriverDebugAllowed(boolean) verwendete zu wenige Register und überschieb dadurch die Activity-Referenz mit einem String. Beim Zugriff auf debugApprovedMac hatte Android deshalb einen Empfänger mit falschem Typ; die Klasse wurde mit VerifyError verworfen.

1.6.1 fügte ein echtes lokales Register hinzu und hielt p0 als Activity fest. Damit war dieser VerifyError laut Versionsdokument behoben; der getrennte ARMv7-Crash blieb offen.

**Warum mein Fehler:** Die Smali-Register-/Typprüfung vor dem Build fing nicht ab, dass ein Methodenparameter und der Activity-Empfänger dieselbe Registerposition nutzten. Ein Buildartefakt ohne DEX-Verifikation war nicht releasefähig.

**Quelle:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1.6.0_DRIVER_DEBUG_VERIFYERROR.md und docs/CARRERAMOD_1.6.1_DRIVER_DEBUG_REGISTERFIX.md.
