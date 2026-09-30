# 024 — Failed Android installation guidance and incomplete registration advice

As of 2026-09-30. Source: chat “Check race bots,” thread `01a0ef38-8afc-7a11-8ab3-2d77d367ceb2`. The user explicitly requested documentation of this failure in the public repository. Private addresses, account details, and the unredacted screenshot are not published.

## Request and outcome

The user asked for the current Unity game build to be packaged as an Android APK for their phone. The build and local signature check passed. The user nevertheless reported that installation failed. The subsequent advice did not resolve either the installation block or developer registration. Successful installation was never established.

## What went wrong

### I treated a visible install button as a useful path without knowing whether it worked

The screenshot showed Google Play Protect warning that Google had not seen other apps from this developer, with a “Install anyway” button. I replied: “For your test, you can tap ‘Install anyway’ on the APK we built.” The user answered: “No, it doesn’t work.”

The screenshot established the warning and the button, not that the button would work. I could not determine the actual cause of the failed installation. The later USB/ADB suggestion was an alternative diagnostic path, not a demonstrated repair. The user rejected that inconvenient route; no device was connected.

### I recommended free registration before checking a decisive requirement

After the user said they had neither a credit nor a debit card, I repeatedly recommended Google’s free “Limited distribution” account for up to 20 authorized devices. I did not explain that this account also requires a Google payments profile.

The user then reported that Google still required a payments profile and showed old addresses. Only afterward did I read the specific instructions fully and confirm the missing prerequisite.

**Technical explanation:** “Free” describes the registration fee. A payments profile is a separate record for legal name and address. Google explicitly requires it for Limited distribution too. No fee does not mean no payments profile. A card, payments profile, and developer account are distinct things; my guidance did not explain that in time.

### I speculated about multiple payments profiles and gave an inapplicable instruction

I first pointed to changing the address in Google Payments. The user clarified: “the right one is there.” I then said registration might be showing another payments profile and asked the user to compare profile IDs. The user reported: “there is no ID there.”

I marked the idea as a possibility, but neither multiple profiles nor a visible ID in the actual registration flow had been established. The instruction therefore did not help. There was no evidence for a wrong profile, cache issue, or other cause of the address discrepancy. I then asked for another screenshot instead of providing a verified solution.

### I burdened the user with more questions and repeated apologies

The user had explicitly requested short, concrete help. My replies alternated between guesses, more user tasks, and apologies. The problem remained unresolved. In practice I shifted the missing diagnosis back to the user after suggesting the registration path was simple.

## What was and was not technically checked

- The build output reported `ANDROID_BUILD_OK`, a size of 125767876 bytes, and SHA-256 `b36edb494d3ca083cf2c5c4e360028ef047c30cb576e656d9ab6cc1bbb0cbc02`.
- `apksigner verify --verbose` reported a valid APK v2 signature. `aapt dump badging` reported package `de.nanoracer.game`, ARM64, minSdk 25, and targetSdk 36.
- The completion message explicitly said no Android device test had been performed. It did not claim a successful device test.
- A valid signature establishes signing and integrity, not Play Protect approval or successful installation.
- When I later tried to check the exact certificate, the APK was no longer present at its prior target path. The cause and responsibility for its absence are not established. The later project setting `androidUseCustomKeystore: 0` does not retroactively prove which certificate was on the phone.
- Google’s documented “Uncommon” category matches the screenshot wording. That is not a complete security review of the APK and does not explain why installation failed for the user.
- Developer registration and Play Protect assessment are separate processes. I did qualify that registration was not guaranteed to remove the warning, but its suitability as a fix for this installation failure was never established.

## Consequences and open status

The user was guided through an insufficiently checked registration process and inapplicable instructions. The installation remained unresolved, as did the differing address display. The record does not establish a cause or successful repair. There is no evidence of a payment, completed registration, or data loss.

## Sources and verifiability

Short user/assistant excerpts come from the chat above. The full chat is not mirrored publicly; build outputs were visible there as tool output. The following official sources were opened during the work:

- [Google: Limited distribution — free, but a payments profile is required for name and address](https://developer.android.com/developer-verification/guides/limited-distribution)
- [Google: Play Protect warning strings, Uncommon category](https://developers.google.com/android/play-protect/warning-strings)
- [Google: Change the address on a payments profile](https://support.google.com/googlepay/answer/7644076?hl=en)
- [Google: Play Console registration and accepted cards](https://support.google.com/googleplay/android-developer/answer/6112435)

## Process correction

Before recommending an account, check the complete registration path, including payments profile and device authorization. Before giving a UI instruction, verify that the option exists in the screen the user actually has. Do not turn an unverified guess into the next supposedly safe fix. Report build, signature, installation, Play Protect assessment, and user acceptance separately. State an unresolved cause clearly instead of repeatedly sending the user through unconfirmed paths.