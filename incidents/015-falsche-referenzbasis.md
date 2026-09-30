# 015 — Als „saubere“ beziehungsweise bekannte Basis ausgegebene APKs blockierten weiter den Login

**Befund:** zwei fehlgeschlagene Rebuilds mit unterschiedlichen Integritätsproblemen.

1.3.2 wurde ohne TimTime-Klassen und Hooks aus einer Hersteller-Appstore-Basis gebaut. Guest-Login funktionierte trotzdem nicht. Die vorhandene Herstellerdatei war nur ein Base-Split; der passende Original-ABI-Split fehlte. Die Ursache des Loginfehlers wurde mit diesem Stand nicht abschließend geklärt.

1.3.3 sollte den bekannten funktionierenden CarreraMod-Kern 1.2.49 reproduzieren. Der Guest-Login blieb blockiert. Der spätere DEX-Vergleich zeigte, dass classes2.dex mit CarreraApiLogActivity durch Apktool neu erzeugt und nicht bytegleich zur Referenz war; nur der Vergleich der nativen Bibliotheken hatte zuvor bestanden.

**Technische Erklärung:** Eine Basis, die nur aus einem App-Bundle-Base-Split stammt, ist kein vollständiges installierbares Originalpaket. Und bytegleiche Native-Bibliotheken beweisen keinen bytegleichen Java-/DEX-Startpfad. Der Launcher und seine DEX-Datei waren Teil des geschützten Loginpfads.

**Warum mein Fehler:** Ich stellte „saubere“ beziehungsweise „known-good“ Builds als Wiederherstellung des Originalverhaltens hin, bevor alle erforderlichen ABI-Splits und alle DEX-Dateien identisch geprüft waren.

**Quellen:** privates DasSam441/Carrera-Mod-App, docs/CARRERAMOD_1.3.2_SAUBERE_BASIS_RUECKZUG.md und docs/CARRERAMOD_1.3.3_KNOWN_GOOD_CORE_RUECKZUG.md.
