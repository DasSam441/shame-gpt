# 023 — Three more independently documented crashes (1.6.74–1.6.76)

As of 2026-09-30. These are concrete runtime/package failures in the CarreraMod release history, not merely static risks.

## 1.6.74: logger hit SIGILL on Android 17

**Finding:** The full tombstone from the affected ARM64 Pixel ties the crash on the first 20-Hz tick to the global Dobby trampoline for Bionic `fputc('\n', stream)`. The app died before the pairing HTTP request.

**Technical failure:** The logger changed a global libc call path. On the documented Android 17 runtime, the trampoline call caused an illegal instruction.

**Correction:** Version 1.6.74 removed the two global libc hooks and replaced them with local PLT-slot forwarding inside the Carrera library. The report documents the cause and code change; device acceptance of the fix remained explicitly open.

**Source:** private project note `docs/CARRERAMOD_1.6.74_ANDROID17_LOGGER_BUILD.md`.

## 1.6.75: collection crash from truncated ARM64 GCHandles

**Finding:** `collectioncrash.log` records SIGSEGV on UnityMain while reopening/updating the vehicle collection, in `hooked_load_cars` and `remember_car_collection`. The import had processed four vehicles immediately beforehand.

**Technical failure:** On ARM64, IL2CPP GCHandles are pointer-width (64-bit). The bridge stored return values, arguments, and handle fields as `uint32_t`, truncating the upper 32 bits. The tombstone showed the shortened handle and invalid memory access.

**Correction:** Version 1.6.75 changed the affected types to `uintptr_t` and separately checked that the 32-bit path stayed unchanged. A fix report alone does not prove later user acceptance.

**Source:** private project note `docs/CARRERAMOD_1.6.75_COLLECTION_GCHANDLE_FIX.md`.

## 1.6.76: a Multidex gap caused an immediate app crash

**Finding:** The internal predecessor contained `classes20.dex` but no `classes19.dex`. Android ART stopped searching for later DEX files at the gap; `HornPhysicsDebugControl`, needed at Activity startup, could not be loaded and the app crashed immediately.

**Impact:** The candidate was blocked, not imported into staging, and removed from the TimTime intake. The following 1.6.77 version filled the sequence through `classes19.dex`.

**Limit:** This is a documented error in a built internal candidate, not a confirmed distribution failure.

**Source:** private project note `docs/CARRERAMOD_1.6.77_HORN_PHYSICS_DEX_FIX_BUILD.md`.

## Evidence limit

These are three concrete failures with different evidence: two device-stack-confirmed crashes and one internal packaging/startup error. Other candidates in the project history are not counted here without checking for duplicates, actual distribution, and device evidence.