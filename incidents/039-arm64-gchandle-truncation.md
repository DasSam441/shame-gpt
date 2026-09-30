# 039 — The 1.6.75 vehicle-collection hook truncated ARM64 GCHandles

**Finding:** device-confirmed SIGSEGV while reopening/updating the vehicle collection.

`collectioncrash.log` records the crash on UnityMain in `hooked_load_cars` and `remember_car_collection`. The import had processed four vehicles immediately before the fault.

**Technical explanation:** IL2CPP GCHandles on ARM64 are pointer-width values (64 bits). The bridge stored return values, arguments, and handle fields as `uint32_t`, truncating the upper half. The tombstone showed the shortened handle followed by an invalid memory access.

**Why this was my mistake:** I used 32-bit storage for values crossing the native/IL2CPP boundary in an ARM64 path. The correction changed the affected types to `uintptr_t` and checked the 32-bit path separately. That code correction is documented; later user acceptance is not established by the fix note alone.

**Limit:** The failure and pointer truncation are documented for this collection path. This report does not claim every ARM64 GCHandle in the application was affected.

**Source:** private `DasSam441/Carrera-Mod-App`, `docs/CARRERAMOD_1.6.75_COLLECTION_GCHANDLE_FIX.md`.