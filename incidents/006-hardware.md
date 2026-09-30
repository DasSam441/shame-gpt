# 006 — Unity build support was confused with working device access

**Finding:** unsupported and too broad.

In early responses, I planned Unity targets for Web, Windows, macOS, Android, and iOS with Bluetooth, NFC, and USB adapters before checking concrete device paths. The user had to stress that these connections are core functions and must actually work.

The available TimTime material established web functions and browser limits, but did not establish successful Unity device access across all platforms. Tests for real device combinations, especially WebGL/iOS and USB on mobile, were still open.

**Technical explanation:** Being able to produce a Unity build for a target does not prove that its APIs, permissions, and hardware access support the required workflows.

**Why this was my mistake:** I confused general platform capability with project-specific evidence and gave the plan more certainty than the record supported.

**Source:** accessible chat “Move TimTime to Unity,” September 2026; public `DasSam441/TimTime`, as of 2026-09-30. This report does not claim Unity cannot build such clients in general.