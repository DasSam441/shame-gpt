# Review scope: chat “Check race bots”

As of 2026-09-30. I read all user and assistant messages returned by the thread tool through the request to document the rest of the chat. I selectively checked tool actions against the chat logs and local project documentation; I did not independently repeat every test. No live gameplay tests, new game builds, or game changes were performed for this archive.

| Conversation phase | Archive record / assessment |
|---|---|
| Original Unity bot proposal and VRC history | Report 028: prior attempts were read, but the lessons were not turned into adequate acceptance criteria. |
| Narrowing to online bot, six first names, and switching rules | Recorded as approved scope; no independently established error in the names or 0/1/2 rule. Single-player was explicitly deferred. |
| First implementation and publication | Report 025: pace was much too cautious; report 030: internal test setups were wrong. |
| Old cones and tires | Report 029; part of the earlier implementation came from another chat and was corrected here. |
| Faster centerline version | Report 026; increased speed did not establish a racing line. |
| Racing line and overtaking | Report 030: specific internal failures and corrected tests. |
| Percentage statements and three-second target | Report 027: absolute comparison came too late; target was not reached. |
| Renewed VRC reference and question about Unity tools | Report 028; ML-Agents was not trained and success was not established. The licensing answer is not a demonstrated factual error by itself. |
| Approval for a sync test | Explicitly authorized publication; process/files were checked, but live synchronization quality was not established. |
| APK build and failed installation | Reports 024 and 031; build and signature passed, no device test was claimed, installation remained unresolved. |
| Registration without a card, payments profile, and old address | Report 024: missing prerequisite, inapplicable profile-ID instruction, cause unresolved. |
| Communication criticism and archive request | Report 031: first report was too narrow and was later expanded. |

## Not presented as established errors

There is no evidence here that final test numbers were fabricated, that human vehicle physics were changed without authorization, that live gameplay tests were performed against the instruction, that the APK was deliberately deleted, or that an APK was built without a request. Approval questions for material concept changes followed an explicit user agreement; their existence alone is not proof of a mistake. Whether their communication was optimal is separate from whether they were authorized.

Publication for the sync test was not acceptance of racing performance. The three-second target was stated explicitly only after the second bot revision; it is not represented as a promise from the start. Different local test states, releases, and user acceptance remain separate.

## Evidence available

The primary source is thread `01a0ef38-8afc-7a11-8ab3-2d77d367ceb2`. Relevant excerpts appear in the reports. I also read `ONLINE-BOT.md`, `acceptance-summary.json`, `protected-source-report.json`, `data-integrity.json`, and `release-sync.log`. The tool history records VRC reads in the first turn. Private chats, local evidence files, and private addresses are not reproduced wholesale. Readers can verify the quoted excerpts and reasoning here, but will not necessarily have access to every original artifact.