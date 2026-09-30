# 030 — Several bot-test setups and internal driving-planning attempts were wrong

As of 2026-09-30.

## Scope

These failures were found and corrected during the work. They do not prove that these exact intermediate states were released live or that the final test counts were fabricated.

| Finding | Technical cause | Effect and correction |
|---|---|---|
| First stationary obstacle was beside the route | It was placed along the prior heading through a curve, not on the actual path | Passing it did not prove the intended stop. The fixture was moved onto the route. |
| High-speed braking fixture never reached 180 km/h | Coarsely sampled polygonal curve generated artificial curvature spikes | Not a valid braking test. A densely sampled analytic curve was used. |
| New line touched Canada/Peak barriers | Global normal rays hit a neighboring hairpin | Route points became discontinuous. Matched left/right boundary segments and continuity checks were added. |
| Overtake of moving opponent did not happen | The lane-change start was recalculated from the current position on each planning pass | The transition kept moving backward. A fixed spatial start was introduced. |
| Claimed side-by-side test had the wrong setup | `Physics.SyncTransforms` applied an earlier Transform change and overrode the intended Rigidbody position | The opponent was ahead, not alongside. Earlier results are invalid; starting position and gap were then checked explicitly. |
| Late obstacle in a tight curve caused contact | Distance in the reference track model did not adequately represent the physical car body | Full body sweeps and larger lateral clearance were added, and the strict contact test was repeated. |

## Why this matters

A green test can exercise the wrong setup. The side-by-side check needed a precondition on the actual relative start position. A lap without barrier contact can still cut a corner, which is why vehicle-outline checks were added.

## Limits of final checks

The outline check ran at 10 Hz and only after the first lap. Zero measured boundary crossings is not a complete guarantee for every physics step and initial condition. Traffic tests checked overlaps every physics step. Even 54 track cases and 15 traffic cases are not an exhaustive analysis of all traffic situations.

The final local checks passed after correction. There was expressly no live gameplay test. That followed the user’s instruction and is not itself a violation. File/hash checks and an active server process do not prove synchronization quality on an end device.

Evidence files: `Evidence/bot-racing-line/matrix-curvature.log`, `traffic-extended.log`, `network-final.log`, `matrix-final.log`, `traffic-body-clearance.log`, `network-body-clearance.log`, and the documented failure sections in `ONLINE-BOT.md`. The earlier invalid side-by-side results are not used as final acceptance.

## Sources and limits

Source: user and assistant messages in chat “Check race bots,” thread `01a0ef38-8afc-7a11-8ab3-2d77d367ceb2`, read through the user’s 2026-09-30 request to document the rest of the chat. Tool records were checked selectively; not every build was independently repeated. Short excerpts are reproduced as primary evidence; the private chat is not mirrored in full.

Additional project evidence: [ONLINE-BOT.md at the documented release commit](https://github.com/DasSam441/nanoracer-unity/blob/c69d4d28596c6a4583dc49b173a0dccd64938941/Documentation/ONLINE-BOT.md). This link may require repository access. Local evidence files are not publicly accessible.