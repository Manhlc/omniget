# OmniGet Android 0.11.1 — API 36 correction

Package: `com.openselena.omniget.prototype`  
Version name: `0.11.1`  
Version code: `14`  
Compile/target API: **36**; minimum API: 29; ARM64.

## Fix

Google Play rejected version code 13 because it targeted API 35. This bundle
compiles/targets API 36 using Android Gradle Plugin 8.10.1 and retains the same
upload certificate, package, engine and configured AdMob IDs. No new signing key
has been created for this correction. Pro checkout remains unconfigured/disabled.

## Upload

Replace the old bundle in the internal-testing release with
`OmniGet-v0.11.1-api36-play-signed.aab`. Keep Google Play App Signing enabled.
Add tester accounts or a tester group under the internal track's Testers section,
save changes, and share Play's opt-in link with those accounts after rollout.

The supplied screenshot showed three warnings, but only the no-testers warning
was expanded. Review the other warnings in Play Console. This artifact's build,
signature and manifest checks do not establish Play policy acceptance or runtime
behavior on Android 16. Physical-device tests and release-readiness checks remain.

Source accompanies this GPL app. Private signing material and passwords are not
included. The upload certificate is public; the private key remains in the
separate signing directory. This download branch does not change main or the
installed debug APK update channel.
