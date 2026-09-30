# 028 — I read the known VRC failures but did not apply them adequately

As of 2026-09-30.

## Inconsistency in my own retrospective

At the start, I wrote: “I read the old VRC history and the current Unity code.” The tool history confirms actual reads of `verlauf.md`, especially sections around S282/S283 and the later shutdown. I had already stated that a bot driving with ordinary inputs had been rejected in real acceptance despite passing tests.

Later, the user again asked me to review the documented VRC attempts. I replied that I “should have considered them before the new proposal.” During this archive work, I initially described the issue broadly as “missed VRC research.” That would be wrong if it meant the history had never been read. This complete chronology corrects that oversimplification.

## What I actually failed to do

I read the warning signs but did not turn them into sufficient acceptance criteria. The same gap between passing technical tests and producing an acceptable racing opponent recurred: first slow contact-free laps, then fast centerline driving, and still large gaps to records.

The old VRC notes report up to 3.12 m of line deviation and late steering corrections at S282. S283 improved the line but still did not consistently reach the then-current record pace. The bot was subsequently disabled. Unity also used geometric target tracking and corner-speed limiting. This establishes a related problem class, not automatically the same physical cause.

## Alternatives considered too late

I explained ML-Agents as an alternative only after the user asked, “Doesn’t Unity have anything for this?” The original request had explicitly asked for a better solution in Unity. The early advice should have compared the hand-written controller with training a driver. But the availability of Unity ML-Agents or a kart example does not prove it would meet our record target. No ML agent was implemented or trained in this chat; it remains an open approach, not a demonstrated successful replacement.

## Evidence limit

The failure was inadequate use of available knowledge and an overbroad later self-description. It does not establish deliberate deception or that useful Unity racing bots are fundamentally impossible. VRC evidence: local `C:/XAMPP/htdocs/vrc/verlauf.md`, entries dated 2026-09-19 around S282/S283/S285; that file is not mirrored publicly.

## Sources and limits

Source: user and assistant messages in chat “Check race bots,” thread `01a0ef38-8afc-7a11-8ab3-2d77d367ceb2`, read through the user’s 2026-09-30 request to document the rest of the chat. Tool records were checked selectively; not every build was independently repeated. Short excerpts are reproduced as primary evidence; the private chat is not mirrored in full.

Additional project evidence: [ONLINE-BOT.md at the documented release commit](https://github.com/DasSam441/nanoracer-unity/blob/c69d4d28596c6a4583dc49b173a0dccd64938941/Documentation/ONLINE-BOT.md). This link may require repository access. Local evidence files are not publicly accessible.