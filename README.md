# OmniGet Android — signed Play upload candidate

Package: `com.openselena.omniget.prototype`  
Version: 0.11.0 (versionCode 13)  
Minimum SDK: 29; compile/target SDK: 35; architecture: ARM64.

The AAB is signed with a dedicated RSA upload key, not the development APK key.
Select Google-managed app signing when enrolling this first release in Play App
Signing. Play delivery signatures will differ from the existing debug sideload.
Do not use this bundle with the debug APK updater. Install via a Play testing track.

This is a submission candidate: Play Console policy/target API checks, privacy
policy/data safety, account/ad approval and physical-device tests remain necessary.
The AdMob App, Banner and Interstitial IDs are configured. Pro checkout remains
unavailable until the production verifier is configured. No production purchase
or Play acceptance is claimed. See source RELEASE-READINESS.md for open checks.

The source ZIP accompanies this GPL app. Original dependency licenses and the
pinned libwebp source build recipe are included. No private signing material or
passwords are included in this public distribution.
