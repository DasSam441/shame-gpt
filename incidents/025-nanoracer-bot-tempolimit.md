# 025 — Racing bot shipped with a blanket 79.2 km/h cap

As of 2026-09-30.

## Claim and counter-evidence

The first completion emphasized “54 driving tests, 162 laps, no barrier contacts.” The user then objected to how slow the bot was. I confirmed: “I capped the bot at 79.2 km/h.”

## Technical failure

The first bot had a fixed cap of 22 m/s (79.2 km/h), a cornering budget of 7 m/s², and a braking budget of 5 m/s². The uniformly cautious driving plan was not adequately checked against the actual performance of the three vehicle classes. Contact-free slow laps could pass the tests without producing a useful racing opponent.

The problem was inadequate acceptance, not a demonstrated fabrication of the 162 laps. The completion mentioned that subjective feel remained open, but did not foreground the low cap or the lack of a meaningful pace comparison.

## Consequences and correction

The user had to report the inadequate speed after delivery. Only then were class-specific maximum speeds, braking power, and higher cornering limits considered. The correction reached 207 contact-free laps locally and about 212 km/h. That still did not fix the missing racing line; see report 026.

Evidence: `Evidence/online-bot/driving.json`, `Evidence/bot-pace-cleanup/pace-comparison.json`, and the “first version” and “pace correction” sections in `ONLINE-BOT.md`. The later target of three seconds behind records had not yet been explicitly set at the start and is not retroactively treated as a promised number.

## Sources and limits

Source: user and assistant messages in chat “Check race bots,” thread `01a0ef38-8afc-7a11-8ab3-2d77d367ceb2`, read through the user’s 2026-09-30 request to document the rest of the chat. Tool records were checked selectively; not every build was independently repeated. Short excerpts are reproduced as primary evidence; the private chat is not mirrored in full.

Additional project evidence: [ONLINE-BOT.md at the documented release commit](https://github.com/DasSam441/nanoracer-unity/blob/c69d4d28596c6a4583dc49b173a0dccd64938941/Documentation/ONLINE-BOT.md). This link may require repository access. Local evidence files are not publicly accessible.