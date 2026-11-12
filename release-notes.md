# OmniGet Android v0.5.1 development fix

The main Download action now routes social media URLs and HLS/DASH to yt-dlp. Generic HTML pages, including pages mislabeled as binary files, also route to the engine instead of being offered as direct downloads. Engine HTML output is rejected before publishing to Downloads. Retry uses the corrected routing. Redacted engine errors are shown as selectable text.

The original yt-dlp release already contains EJS 0.8.0; both solver hashes were verified against upstream expectations. No replacement solver or runtime download is used.

Validation: ARM64 APK build/signature, Android Lint, 41 policy/parser/routing checks, HTTPS HTML/mislabeled-HTML/MP4 classification, and a host-only actual engine download matching the source bytes. Live YouTube testing is blocked by Cloud egress policy; on-device YouTube/social extraction has not been verified. Login/anti-bot challenges and DRM are not bypassed. Google AdMob still uses test IDs. Debug-signed Android 10+ ARM64 development build.

Corresponding Android source and build instructions are included under GPL-3.0 with third-party components retaining their licenses.
