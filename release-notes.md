# OmniGet Android v0.9.0 development preview

Compact composer with inline Paste; equal-width history filters; compact media/direct-file rows and overflow actions instead of three large buttons; readable titles with separately stored actual filenames; opaque compact Pro proposal sheet. The reserved ad/navigation footer is shorter and remains separate from download controls.

Settings → Check for updates uses a fixed public GitHub channel. APK download checks bounded size, SHA-256, package, strictly newer version, OS compatibility and the installed app signing certificate. A scoped FileProvider opens the Android system installer after user consent/unknown-source permission. No silent install; this is not Play Store In-App Updates. Install this bootstrap version manually once to enable future in-app checks.

Validation: ARM64 build/signature, Android Lint with zero errors, 65 host checks and local HTTPS engine regression tests. Actual SQLite migration SQL preserves old title/URI rows. Device UI and native installer/permission flow remain unverified. Pro is not on sale and ads still use Google test IDs; source login/anti-bot restrictions remain.

Android 10+ ARM64 debug-signed development build. Android source/build instructions, GPL-3.0 license and third-party notices are included. Preserve the existing signing key for subsequent updates; UPDATES.md documents the channel publication procedure.
