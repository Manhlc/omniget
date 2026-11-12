Android development preview for Android 10+ ARM64 devices. This is a debug-signed prerelease, not a production or Google Play release.

## What's New
- Floating bottom navigation for Downloads, Pro and Settings, retaining OmniGet's dark/orange palette.
- Google AdMob test banner with UMP consent handling and privacy options. No live monetization or Pro billing.
- On-device yt-dlp 2026.10.26, Python and FFmpeg; one engine task at a time, up to 1080p when supported, with MediaStore export to Downloads/OmniGet.
- Direct HTTPS downloads, history, retry, file sharing and Wi-Fi preference.

## Fixes
- Android 10 inset compatibility and keyboard/navigation clearance.
- Preserves the existing development signing certificate for updates.

## Validation and limitations
- APK build/signature, engine payload checksums and Android Lint verified (0 errors, 22 warnings).
- The bundled yt-dlp payload passed a host-only HTTPS extraction/download smoke test; policy/parser fixtures passed 21 checks.
- Installation, floating navigation, ad rendering and engine execution have NOT been validated on a physical Android device. The software emulator did not boot reliably enough for app verification.
- No guarantee of support for every website; authenticated content, DRM, gallery-dl and complete desktop feature parity are not implemented.

APK, Android app source/build instructions and SHA-256 checksums are included. Source is under the repository's GPL-3.0 license; third-party components retain their respective licenses. See ENGINE.md and ADMOB.md in the source archive for dependency origins and release limitations.
