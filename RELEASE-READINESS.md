# Android 0.12.0 — implementation and remaining release configuration

This is a development candidate, not a production approval or a published update.
The existing on-device yt-dlp/Python/FFmpeg engine and GPL source obligations remain.
The user's English/Vietnamese language review is complete.

## Implemented

- Stream download completion changes to processing/saving; only a published local
  file is marked complete. Stream speed/ETA is hidden while merging or saving.
- Pro uses Google Play Billing 8.3, actual localized product pricing, pending-purchase
  handling, restore and backend RSA-signed entitlements. No local boolean unlock.
- Pro batch queue (up to 50 HTTPS links), scheduled downloads and Video/Audio/Files
  organization use the existing engine and persistent WorkManager records. Direct
  file jobs reject HTML. Schedule time is best effort under Android power/network
  policy. Cancellation applies to the batch group. Wi-Fi preference is enforced
  with transport checks, not merely an unmetered-network constraint.
- Verified Pro suppresses ads. Free ads retain UMP consent and the existing interval;
  a missing/failed ad does not prevent the download. Owner ad IDs are configured in project properties; SDK fallbacks remain test IDs.
- Release builds use Google Play flexible in-app updates and omit the APK-install
  permission. Development sideload builds keep the verified APK update channel.
- Release upload-key configuration reads passwords from environment variables.
  Without that key the generated AAB is unsigned and cannot be uploaded.

## Native 16 KB support

`scripts/prepare-native.py` verifies the original FFmpeg Maven AAR against
`engine-checksums.json`, verifies libwebp v1.6.0 source archive SHA-256, builds the
five WebP DSOs using NDK 28.2.13676358 and 16 KB linker alignment, and replaces only
those DSOs in a local AAR. It audits every nested FFmpeg ELF PT_LOAD alignment.
The source URL and hash are pinned in the script; `build/engine/native-support.json`
records hashes of generated libraries. The engine/extractor is retained.

Install CMake, Ninja and NDK 28.2.13676358, set `ANDROID_HOME`, run
`python3 scripts/prepare-engine.py` followed by `python3 scripts/prepare-native.py`
before Gradle. Optional `CMAKE`, `NINJA`, `ANDROID_NDK_HOME` select tool paths.
The WebP BSD license is copied to `build/engine/libwebp-LICENSE`; source is available
from the pinned upstream URL in the build script. Original dependency notices apply.
ELF alignment checks alone do not replace running the engine on 16 KB Android.

## Still requires deployment/account/device work

- AdMob App ID `ca-app-pub-1108509845492545~4416654397` is configured.
  Banner `ca-app-pub-1108509845492545/4944615505` and interstitial
  `ca-app-pub-1108509845492545/1305908340` are also configured. The owner
  confirmed the Play one-time product ID `omniget_pro_lifetime`; it is pinned in
  project properties and matches the verifier default. Live billing, consent and
  ad-delivery verification remain outstanding.
- Deploy the verification server (`pro-server/README.md`), provision its credentials
  in the hosting secret store, supply its HTTPS endpoint and public signing key.
- Production upload signing key, Play App Signing enrollment and final package
  ownership confirmation. Preserve the installed app's signer for sideload updates;
  a Play-signed app may require a separate installation/migration.
- Review the current Play target API requirement before submission (candidate
  compile/target SDK 36), native 16 KB checks, permissions, data safety, content
  rights, GPL/third-party obligations and AdMob eligibility. A downloader's Play
  acceptance is not guaranteed by a successful build.
- Public privacy-policy URL and support/contact details. Fill in actual controller,
  hosting, retention and advertising disclosures before publishing the listing.
- Real-device regression: background/cancel/reboot/network changes, batch/schedule,
  media merge, direct files, sharing, 16 KB devices and low storage.
- Play internal-track tests: successful/pending/cancelled purchases, restore/refund,
  entitlement expiration/outage, ad consent/no-ads and in-app store updates.

## Public build properties

`ADMOB_APP_ID`, `ADMOB_BANNER_ID`, `ADMOB_INTERSTITIAL_ID`, `PRO_PRODUCT_ID`,
`PRO_VERIFY_URL`, `PRO_PUBLIC_KEY` may be set as Gradle project properties.
`RELEASE_STORE_FILE` and `RELEASE_KEY_ALIAS` point to a securely supplied upload key;
`OMNIGET_STORE_PASSWORD` and `OMNIGET_KEY_PASSWORD` are environment secrets.
Never send the key/password/service account/purchase tokens through chat or publish
those values with source artifacts. Do not enable real checkout before backend and
internal-track verification pass.

## Follow-up fixes

Single-item cancellation is now distinct from cancelling an entire unfinished batch.
Persistent cancellation markers prevent progress/status callbacks from resurrecting
a cancelled item; the worker skips cancelled siblings and stops the active engine.
Transient verification/network/server errors keep jobs queued with WorkManager
backoff; only an explicit verifier rejection or missing setup requires user action.
Native downloads share the existing engine lock; the foreground service enters
foreground before waiting instead of discarding a request when the worker is active.
The organization subtitle now describes the implemented folders rather than promising
filename rules. Host regression includes HTTP failure classification and SQLite
cancellation selectors. Android concurrency/lifecycle still needs device testing.

## Play rejection correction — code 14

Play Console explicitly required target API 36 for code 13. Candidate 0.11.1
(code 14) raises compile/target SDK to 36 and AGP to 8.10.1, retaining the original
private upload key. Verify the actual signed bundle manifest before delivery.
The owner must add internal tester accounts in Play Console. Only that warning
was readable in the supplied screenshot; the other collapsed warnings require
review inside Play Console. Android 16 runtime/device regression remains pending.

## Package change — MLCSoft

The current application/package/namespace is `com.mlcsoft.omniget`, code 15,
version 0.12.0, target API 36. Reuse the existing upload key; preserve historical
certificates. A new Play app, product setup and verifier permissions are required.
Old-app purchases/storage are not automatically migrated. The AdMob association
must be reviewed for the new Play listing. No backend deployment is performed
by this package change. Pro remains disabled without production verification.
