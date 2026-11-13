# OmniGet — MLCSoft package

Application ID and namespace: `com.mlcsoft.omniget`  
Version: `0.12.0` (code `15`)  
Compile/target SDK: 36; minimum SDK: 29; ARM64.

The former `com.openselena.omniget.prototype` listing cannot accept this package.
Create a new app in Play Console, enroll it in Play App Signing, and upload
`OmniGet-MLCSoft-v0.12.0-play-signed.aab` to its internal testing track. This bundle
retains the dedicated upload certificate (public certificate included); private
signing material is not distributed. Existing old-package APKs remain separate.

Recreate the one-time product `omniget_pro_lifetime` on the new listing and grant
the verifier service account access to the new app when deploying verification.
Review AdMob association for the new package/listing. The owner-supplied ad IDs
are retained; they have not been silently replaced. Pro checkout stays disabled
without a production verifier endpoint and public key. Old app data/history and
purchases are not automatically migrated to the new package.

Java source paths, activity/service names, FileProvider authority and verifier
package defaults now match the new identity. Engine and GPL/third-party notices
remain. Play builds use Play updates. The new standalone APK update namespace is
`android-mlcsoft-updates`; it is separate and has not been published.

Matching source and manifest are included. Build/signature/static checks do not
establish device behavior, ad delivery, purchase verification or Play acceptance.
Cloudflare deployment is deferred; no backend is deployed by this change.
