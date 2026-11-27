# NostalPre – Pre-Renewal Android build

This is the Pre-Renewal-only source package prepared from the supplied nostalRE source.
The experimental AUTO Attack edits were intentionally left out.

## Build status
- The server source enables `PRERE` in `server/src/config/renewal.hpp`.
- `scripts/build-server.sh` compiles the server with `-DPRERE`.
- The Android app label is `NostalPre`; version is `0.3.1-prere`.
- This package is source code, **not an installable APK**.
- The APK has not yet been compiled or tested on a phone.
- A GitHub Actions workflow is included to attempt an ARM64 Android build.

## Build with GitHub Actions
1. Create a GitHub repository and upload the complete contents of this folder to its root.
2. Open the repository's **Actions** tab.
3. Run **Build NostalPre Android APK**.
4. If the workflow succeeds, download the artifact named `NostalPre-Android-APK`.

The workflow can still fail if upstream source dependencies, toolchain versions, or build scripts need adjustment.
Keep the existing nostalRE APK and its game data backed up until the new APK is successfully installed and tested.
