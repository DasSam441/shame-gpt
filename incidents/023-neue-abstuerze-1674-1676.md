# 023 — Android failures in CarreraMod 1.6.74–1.6.76

This page replaces a grouped report with separate evidence-backed case files. Each incident has its own report: [1.6.74 logger SIGILL on Android 17](038-android17-logger-sigill.md), [1.6.75 ARM64 GCHandle truncation](039-arm64-gchandle-truncation.md), and [the internal 1.6.76 Multidex gap](040-android-multidex-gap-1-6-76.md).

The cases have different evidence: two device-stack-confirmed runtime crashes and one internal package/startup failure that was blocked before staging. They are not treated as one failure or three independent root causes of the same issue.