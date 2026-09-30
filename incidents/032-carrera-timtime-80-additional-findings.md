# 80 additional CarreraMod and TimTime findings

Updated: 2026-09-30. This report adds 80 individually numbered findings to the archive. They are **specific defects, failed states, unsupported claims, or failed attempts**, not 80 independent root causes. Some expand failure families already summarized in earlier reports. Unverified hypotheses are excluded. Personal names, device identifiers, and MAC addresses from chats are omitted.

## Earlier CarreraMod attempts

CT-024. **1.2.67 — TimTime cars did not appear in Unity.** The live test loaded permissions and images, but the cars did not appear in Carrera’s vehicle list. Source: CARRERAMOD_1.2.67_TIMTIME_FILTER_TEST.md.

CT-025. **1.2.70 — opening the car list crashed.** The new inline hook was not usable in the device test. Source: CARRERAMOD_1.2.70_INLINE_HOOK_CRASH.md.

CT-026. **1.2.74 — TryGetRacer hook crashed at startup.** The candidate was withdrawn. Source: CARRERAMOD_1.2.74_TRYGETRACER_CRASH.md.

CT-027. **1.2.75 — reducing the hook did not remove the crash.** The follow-up remained unusable. Source: CARRERAMOD_1.2.75_REDUZIERTER_CRASH_FOLLOWUP.md.

CT-028. **1.2.76 — SaveState.Racer intervention crashed at startup.** The new vehicle intervention was in the affected startup path. Source: CARRERAMOD_1.2.76_SAVESTATE_RACER_CRASH.md.

CT-029. **1.2.77 — changing the storage path did not fix the same crash.** The first correction did not solve the problem. Source: CARRERAMOD_1.2.77_STORAGE_KORREKTUR_CRASH.md.

CT-030. **1.2.80 — catalog ID was written to the wrong field.** Writing it to TechnicalName instead of Id produced a black vehicle view. Source: CARRERAMOD_1.2.80_RACERCONTROLLER_ERSTVERSUCH.md.

CT-031. **1.2.81 — correcting the field was not enough.** The black view remained because synchronization re-entered while the UI was being built. Source: CARRERAMOD_1.2.81_KATALOG_ID_KORREKTUR.md.

CT-032. **1.2.82 — Carrera’s sign-in button did not respond.** Sync before CarCollection.OnEnable blocked the login path. Source: CARRERAMOD_1.2.82_SYNC_VOR_UI_REGISTRIERUNG.md.

CT-033. **1.2.83 — moving the hook to the main thread did not remove the login block.** The Guest button remained blocked. Source: CARRERAMOD_1.2.83_HOOKS_AUSSERHALB_NETZWERKTHREAD.md.

CT-034. **1.2.85/1.2.86 — moving sync to the next frame did not establish a reliable fix.** The follow-up still recorded a Guest crash. Sources: CARRERAMOD_1.2.85_SYNC_NACH_BIND_FRAME.md and CARRERAMOD_1.2.86_GUEST_CRASH_FOLLOWUP.md.

CT-035. **1.2.89 — the original vehicle fetch was not a working TimTime integration.** The documentation explicitly says there was no functional proof. Source: CARRERAMOD_1.2.89_ORIGINALER_FAHRZEUGABRUF.md.

CT-036. **1.2.90 — CarProfiles hook ran before login completed.** It could write to Carrera’s RacerController during Guest login. Source: CARRERAMOD_1.2.90_CARPROFILES_LOGINFEHLER.md.

CT-037. **1.2.92 — the supposedly passive observer still ran too early.** OnStateEnter returned a Task; hooks were still installed during the login state machine. Source: CARRERAMOD_1.2.92_PASSIVER_NACHLOGIN_WAECHTER.md.

CT-038. **1.2.94 — the LoadCars assumption was not adequately supported.** A later audit found the assumption insufficient. No APK hash or device test is documented for 1.2.94 itself. Source: CARRERAMOD_1.2.94_UNVOLLSTAENDIG_BELEGTER_ZWISCHENSTAND.md.

CT-039. **1.2.95 — native crash on Guest click.** The new static return path was discarded. Source: CARRERAMOD_1.2.95_BACKENDLOGIN_NATIVE_CRASH.md.

CT-040. **1.2.96 — retreating to a “clean” base did not fix Guest login.** This ruled out the TimTime API as the cause, but did not establish a working manufacturer baseline. Source: CARRERAMOD_1.2.96_KERNBASIS_RUECKZUG.md.

CT-041. **1.2.97 — native URL router caused an immediate crash.** Runtime modification of a Unity code page was a candidate cause; the build was withdrawn. Source: CARRERAMOD_1.2.97_RACERS_URL_ROUTER_CRASH.md.

CT-042. **1.2.98 — removing the router call was not enough.** Guest login remained blocked. Source: CARRERAMOD_1.2.98_ROUTER_AUFRUF_ENTFERNT.md.

CT-043. **1.2.99 — the original launcher was not restored.** Even after routing calls were removed, CarreraApiLogActivity remained the launcher instead of UnityPlayerActivity. Source: CARRERAMOD_1.2.99_API_ROUTING_AUFRUFE_ENTFERNT.md.

CT-044. **1.3.0 — CarProfiles bridge could run before Guest/SaveState was ready.** The approach was withdrawn. Source: CARRERAMOD_1.3.0_GUEST_LOGIN_RUECKZUG.md.

## Individual broken JSON paths in 1.6.49

CT-045. **POWERBAND start state became stale.** A later change to enabled did not update a state already stored locally. Source: CARRERAMOD_1.6.49_JSON_WIRKUNGS_AUDIT.md.

CT-046. **MODULE enabled was missing from JSON import.** The server could not start the module. Same source.

CT-047. **MODULE ignore_modules was missing from JSON import.** The value existed only in the local dialog. Same source.

CT-048. **MODULE check_position_valid was missing from JSON import.** TimTime’s value was not imported. Same source.

CT-049. **MODULE next_modules_zero was missing from JSON import.** This setting also remained local rather than server-controlled. Same source.

CT-050. **BANDEN TEST enabled was read only initially.** Later server changes did not reliably update the active native configuration. Same source.

CT-051. **OFFTRACK available was ignored.** available:false could not safely hide the button and disable a stored local state. Same source.

CT-052. **SIM+ throttle threshold had no proven JNI endpoint.** Java called nativeSetSpeedReductionThrottlePercent, but the APK had no matching exported symbol. Same source.

CT-053. **SIM+ gas_step_percent was missing.** The gas-step dialog did not read it from JSON. Same source.

CT-054. **SIM+ gas_step_window_ms was missing.** The timing window was not server-controlled. Same source.

CT-055. **SIM+ gas_step_ignore_steering_ms was missing.** The JSON value was not imported. Same source.

CT-056. **SIM+ gas_step_cooldown_ms was missing.** The cooldown remained outside the JSON contract. Same source.

CT-057. **SIM+ available was missing.** The button was installed regardless of TimTime availability. Same source.

CT-058. **SIM+ enabled was missing.** The server profile could not set the initial state. Same source.

CT-059. **start_min had no parser or setter path.** The JSON block had no effect in the APK. Same source.

CT-060. **tx_byte_10 had no parser or setter path.** This advertised JSON block also had no effect. Same source.

CT-061. **automatic_logging.on_start_min was forced to false.** The visible configuration option was not applied. Same source.

CT-062. **api.racers was treated as a separate route even though it was only an alias.** The router did not read it as an independent route. Same source.

## Other contract and packaging failures

CT-063. **1.6.42 replaced the native library with an incompatible historical build.** The expected OFFTRACK native side was not ready. Source: CARRERAMOD_1.6.42_FUNKTIONS_DEBUG_JSON_AUDIT.md.

CT-064. **1.6.42 could not start the 20-Hz logger.** startLogging() returned false because the observer-ready flag was not set. Same source.

CT-065. **1.6.42 exposed fallback values as if they were live configuration.** 80/50/80 did not prove that TimTime values had loaded. Same source.

CT-066. **1.6.42 still contained POWERBAND despite its documented retirement.** The button and handoff path remained. Source: CARRERAMOD_POWERBAND_STILLLEGUNG.md.

CT-067. **1.6.42 still contained MODULE despite its documented retirement.** The dialog and JSON processing remained. Source: CARRERAMOD_MODULE_HANDLING_STILLLEGUNG.md.

CT-068. **1.6.42 still contained BANDEN TEST despite its documented retirement.** The button, dialog, and native handoff remained. Source: CARRERAMOD_BANDEN_TEST_STILLLEGUNG.md.

CT-069. **1.6.50 was prematurely called a “complete JSON contract.”** The native endpoint for simulation_plus.speed_steering_min_throttle_percent was still missing. Source: CARRERAMOD_1.6.50_JSON_VERTRAG_BUILD.md.

CT-070. **1.6.50 incorrectly let root enabled:false override module switches.** A global setting overrode each module’s available/enabled pair. Source: CARRERAMOD_1.6.52_OPTIONAL_MODS_PROFILE_ROUTING.md.

CT-071. **1.6.52 omitted SIM+ gas-step from the shared UI refresh.** If the manifest arrived after the overlay was created, the button did not appear. Same source.

CT-072. **1.6.43 failed because Java and native JNI names did not match.** Java declared getState/setValues and similar methods, while the library exported different names; the first configuration call raised UnsatisfiedLinkError. Source: CARRERAMOD_1.6.43_NATIVE_BOUNDARY_REPAIR.md.

CT-073. **The first 1.6.65 APK candidate still had the old version number.** Apktool reused a cached manifest block. The candidate was caught and not released, but the build pipeline was faulty. Source: CARRERAMOD_1.6.65_BUILD.md.

CT-074. **1.6.20 lost classes5.dex during repackaging.** The candidate consequently lacked the pairing/manifest client. Source: CARRERAMOD_1_6_GESAMTAUDIT_2026-08-16.md.

CT-075. **1.6.27 overwrote classes5.dex.** The debug DEX caused TimTimeVehicleClient to disappear from the APK. Same source.

## Earlier hook and formula experiments

CT-076. **Direct dashboard/UI gear hooks returned unusable values or crashed.** The display layer was not a stable gear-data path. Source: docs/chat-history/README.md, “RPM and gear.”

CT-077. **Gear-store hooks crashed or damaged shift behavior.** Same chat history.

CT-078. **Direct jumps into original up/downshift blocks crashed.** The upshift block required internal context the hook did not provide. Source: same chat history, “Manual shifting.”

CT-079. **Direct writes to Gearbox.gear were unstable.** The chat history marks this approach as unsuccessful. Same source.

CT-080. **Setting Engine.CalculateTorque to zero did not limit real driving power as intended.** Source: same chat history, “5800 RPM limit.”

CT-081. **InputController.get_Throttle was the wrong control point.** The approach was discarded. Same source.

CT-082. **Freezing RacerDriveData.Kph caused implausible driving behavior.** Same source.

CT-083. **The old TX byte 10 table was unreliable.** Later logs showed byte values inconsistent with the simultaneously logged steering_assist = 0. Source: docs/chat-history/README.md, “TX byte 10.”

CT-084. **RawX overlay labels were not reliably tied to byte sources.** 0x21/0x22/0x23 were temporarily displayed as w23/w24/w25; the mapping needed revalidation. Source: same chat history, “Gyro / RawX.”

CT-085. **Car.acceleration was mistaken for a control value.** The history clarifies it is a measurement; Car.AddForce affects acceleration force. Same source.

CT-086. **Steering formulas produced unnatural or asymmetric behavior.** The strong interventions tested were not retained as usable driving features. Source: same chat history, “Steering and Byte 8 experiments.”

## Direct corrections from later chats

CT-087. **Wrong TimTime vehicle count.** I first reported 9 vehicles and inferred an import problem; the later check found 36 fleet entries and 32 hybrid cars. Chat: “Fix missing TT cars.”

CT-088. **A local reconstruction was presented as a server result.** I initially called the set of 9 an actual TimTime manifest defect, then corrected that it came from my local reconstruction. Same chat.

CT-089. **I delegated diagnosis to the user while more evidence could be checked.** I requested phone photos/USB evidence; the user said that was not possible and the app import had already been tested repeatedly. Same chat.

CT-090. **I initially treated the audio request as an app request.** Asked whether all audio settings had been checked, I answered about the app; the user clarified: “in TimTime, not in the app.” Chat: “Fix audio settings persistence.”

CT-091. **I inferred durable persistence from a function call.** I saw saveState() and claimed settings were saved without waiting for server confirmation. The later server finding was HTTP 409. Chat: “Evening races / saved rounds.”

CT-092. **I declared the audio fix complete after syntax/UI checks.** The user then reported that not even the language setting was being saved. Chat: “Fix audio settings persistence.”

CT-093. **I treated club tracks as integrated when they were absent from race-control track selection.** The missing import path was identified later. Chat: “Evening races / saved rounds.”

CT-094. **I gave the wrong session explanation for a finish-line driver.** I said the driver had not joined the new session; timestamps showed that they had. Chat: “Evening races / saved rounds.”

CT-095. **I claimed a previous session ID without evidence.** I later withdrew the claim that the devices had sent an old ID. Same chat.

CT-096. **I incorrectly treated an MRC/NFC identifier as a Live-Target requirement.** The user pointed out that finish-line detection does not require an MRC chip; the server and browser filters had been mixed. Same chat.

CT-097. **I described the first LapCompleted event as missing.** The user had repeatedly mentioned the event; the later finding showed a TimTime processing error. Same chat.

CT-098. **I conflated Live-Target and MRC timing.** I initially explained the dashboard/lap failure using the wrong timing source. Same chat.

CT-099. **I gave the wrong reason for a missing observer timing-source switch.** I said only Hybrid Racing Lab was active. A virtual finish-line source existed but was not connected to the observer feed. Chat: “Fix timing-source switching.”

CT-100. **I speculated about pairing-code generation without enough evidence.** When asked whether a code might not be generated, I shifted the likely cause to app redirection without proving the code-generation path. Chat: “Check pairing-code generation.”

CT-101. **I said pairing was “fixed” after the user had only asked a question.** The reply claimed a code/QR flow without citing a concrete code or app test in that answer. Same chat.

CT-102. **I built signed APK 1.2.69 despite the project rule against unrequested app builds.** I built an Android candidate during Live-Target work; the user then clarified that they did not want an app built. Chat: “Plan Live-Target transmission.” This is a second documented build-scope failure, separate from report 004.

CT-103. **I used the wrong time contract in the Live-Target payload.** The first Android path sent lapTimeMs; the user corrected that only the original crossing timestamp should be sent. TimTime derives lap time from consecutive timestamps. Same chat.

## How to read these 80 entries

Some are failed follow-up versions from the same root cause, such as login hooks or vehicle import. Others are separate JSON values, false factual claims, or scope failures. This list asserts **80 documented findings**, not 80 independent root causes. Each entry names the relevant version note or accessible chat. Project code, APKs, usernames, and MAC addresses are not mirrored.
