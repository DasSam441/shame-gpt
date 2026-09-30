# 029 — Old cones and tire stacks remained visible despite the removal request

As of 2026-09-30.

## User finding and my statement

Along with the slow bot, the user objected that old cones and tire stacks were still present despite an earlier removal instruction. I confirmed: “Only the editor buttons disappeared. The published track pool still contains 312 old cones and 71 tire stacks.”

## Technical finding

Removing UI buttons does not remove stored object instances or the code that recreates them from track data. The visible state therefore did not reach the requested “remove everywhere” state. In the first shared bot release, I even mentioned “the three enlarged cones” as part of parallel changes.

## Responsibility and evidence limits

The original removal/button change came from parallel project work. This chat establishes the remaining problem, my release communication, and the subsequent correction. It does not contain the full original request and implementation. I therefore do not assign authorship of the earlier partial removal wholesale to this chat. The precise timing of the enlargement and removal instructions is also not fully established here.

## Correction

After explicit approval, the old `cone` and `tires` types were removed from active track/editor data and prevented from being read or published again. New package objects were retained. The local record `Evidence/bot-pace-cleanup/data-integrity.json` reports `remainingLegacyObjects: 0`, preserved other placements, and preserved track/ghost keys. The error was corrected for the checked data; it is not represented as still present today.

## Sources and limits

Source: user and assistant messages in chat “Check race bots,” thread `01a0ef38-8afc-7a11-8ab3-2d77d367ceb2`, read through the user’s 2026-09-30 request to document the rest of the chat. Tool records were checked selectively; not every build was independently repeated. Short excerpts are reproduced as primary evidence; the private chat is not mirrored in full.

Additional project evidence: [ONLINE-BOT.md at the documented release commit](https://github.com/DasSam441/nanoracer-unity/blob/c69d4d28596c6a4583dc49b173a0dccd64938941/Documentation/ONLINE-BOT.md). This link may require repository access. Local evidence files are not publicly accessible.