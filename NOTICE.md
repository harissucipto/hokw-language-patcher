# NOTICE for `android/`

This directory will hold the Android patcher app for Honor of Kings World (`com.tencent.ngr`):
working name "HoKW Language Patcher", provisional application id `id.hokw.patcher`. It is being
built in the milestones described in `docs/android.md` (Indonesian). This file records the
licensing position; the first files were copied on 25 November 2026 (milestone M4) and are listed
in the table "Files copied from hok-ace-patch" below, which every later copy must extend.

## Derived from hok-ace-patch (with permission)

Parts of this app are derived from HOK ACE Language Patcher,
https://github.com/halixm-dev/hok-ace-patch (commit `1ca536d`, 22 November 2026), by halixm-dev.
That repository carries no LICENSE file, so its own code is all rights reserved by default. Its
author granted the owner of this repository permission to reuse that code on 24 November 2026.
Every file copied under that permission is listed in the table below and keeps a header line
naming its origin.

## Apache License 2.0: ADB client ported from Shizuku

The wireless-debugging ADB client in hok-ace-patch is itself a port of Shizuku's manager ADB
client (Copyright RikkaW, Apache License 2.0; https://github.com/RikkaApps/Shizuku), following
AOSP's `adb/pairing_connection` and `adb/pairing_auth`. These files are licensed under Apache-2.0
independently of the permission above and are reused with attribution:

- `AdbClient.kt`, `AdbKey.kt`, `AdbMdns.kt`, `AdbPairing.kt`, `AdbProtocol.kt`
  (hok-ace path `android/app/src/main/java/dev/halixm/hokacepatcher/`)
- `cpp/adb_pairing.cpp` (hok-ace path `android/app/src/main/cpp/adb_pairing.cpp`; SPAKE2 for
  ADB pairing)

The Apache-2.0 text ships as `android/licenses/Apache-2.0.txt` with the first copy. These files are
included only if the Wireless debugging provider ships in the first version; the Shizuku and Root
providers do not need them.

## Other third-party components (expected; confirm license texts at M4)

| Component | License | Use |
|---|---|---|
| Shizuku API / provider 13.1.5 | MIT | Shizuku provider (user service, `newProcess`) |
| Conscrypt `org.conscrypt:conscrypt-android` 2.7.0 | Apache-2.0 | TLS 1.3 and keying-material export for ADB pairing (Wireless debugging only) |
| BoringSSL prefab `io.github.vvb2060.ndk:boringssl` | BoringSSL LICENSE (OpenSSL/SSLeay, ISC and Apache-2.0 parts) | SPAKE2, statically linked (Wireless debugging only) |
| Chaquopy 17.0.0 | MIT | Python 3.12 runtime inside the app |
| CPython 3.12 | PSF License | via Chaquopy |
| python-lz4 4.3.2 (bundles liblz4 1.9.4) | BSD-3-Clause (wrapper), BSD-2-Clause (liblz4) | `lz4.block` backend for `hokw_patch/lz4c.py` |

## Pictures from the Shizuku user manual

The "Siapkan Shizuku" screen illustrates steps 2-4 (developer options and Wireless debugging,
pairing, Start) with the pictures of Shizuku's official user manual,
https://shizuku.rikka.app/guide/setup/ (RikkaApps; files `enable_dev_options.png`,
`enter_wireless_debugging.png`, `enable_wireless_debugging.png`, `start_paring_from_shizuku.png`,
`start_pairing.png`, `enter_pairing_code.png`, `start_shizuku.png`, downloaded 25 November 2026 and
composed side by side into `res/drawable-nodpi/shizuku_step_2..4.png`, unchanged otherwise). They are
used as a short instructional excerpt with attribution in the app (caption under each picture) and
here; the manual's own licence is not stated on the site. Replace these three PNGs with your own
screenshots to drop the dependency. All other pictures in `res/drawable-nodpi/` are screenshots of
this app and of the game taken by the owner.

## Files copied from hok-ace-patch

Every copied file starts with the line `// Derived from hok-ace-patch (halixm-dev), used with
permission; see android/NOTICE.md` (hok-ace commit `1ca536d`). Package `dev.halixm.hokacepatcher`
became `id.hokw.patcher` everywhere.

| Destination in `android/` | Origin in hok-ace-patch | Basis | Changes |
|---|---|---|---|
| `app/src/main/java/id/hokw/patcher/ShellProvider.kt` | `android/app/src/main/java/dev/halixm/hokacepatcher/ShellProvider.kt` | permission of halixm-dev, 24 November 2026 | package `id.hokw.patcher`; Wireless provider, labels and `available` flag removed (constants `SHIZUKU`, `ROOT` only); `WorkerAccess` replaced by `WorkerUid` (2000/0), without the refusal of a Shizuku server running as root |
| `app/src/main/java/id/hokw/patcher/ShellServiceStarter.kt` | `android/app/src/main/java/dev/halixm/hokacepatcher/ShellServiceStarter.kt` | permission of halixm-dev, 24 November 2026 | package; `WorkerUid`; process and thread names `hokw-*`; otherwise verbatim (hand-off through `IActivityManager.getContentProviderExternal` and `IContentProvider.call`) |
| `app/src/main/java/id/hokw/patcher/ShizukuWorkerStarter.kt` | `android/app/src/main/java/dev/halixm/hokacepatcher/ShizukuWorkerStarter.kt` | permission of halixm-dev, 24 November 2026 | package; uid-0 refusal dropped (ADR 0007 not adopted, `docs/android.md` section 3); `DiagnosticTrace` replaced by `android.util.Log`; `isPreV11` check and messages naming this app; Shizuku package constant from `ShizukuLauncher` |
| `app/src/main/java/id/hokw/patcher/RootWorkerStarter.kt` | `android/app/src/main/java/dev/halixm/hokacepatcher/RootWorkerStarter.kt` and `shellLine` from `android/app/src/main/java/dev/halixm/hokacepatcher/WirelessDebugging.kt` | permission of halixm-dev, 24 November 2026 | package; `shellLine` moved in (WirelessDebugging.kt itself is not copied); `Log`; refusal messages name this app |
| `app/src/main/java/id/hokw/patcher/WorkerBinderProvider.kt` | `android/app/src/main/java/dev/halixm/hokacepatcher/WorkerBinderProvider.kt` | permission of halixm-dev, 24 November 2026 | package; caller check through `WorkerUid.accepted` |
| `app/src/main/java/id/hokw/patcher/WorkerDeviceConnection.kt` | `android/app/src/main/java/dev/halixm/hokacepatcher/WorkerDeviceConnection.kt` | permission of halixm-dev, 24 November 2026 | `WorkerLink`/`WorkerStarter`, first-binder attach, death watch, patience/stall fallback, own-starter command and timeout kept; public API restructured to `connect(provider, onReady, onError)` / `disconnect()` / `service` / `provider` (android/DESIGN.md contract), each attempt on its own thread; `Log`; `destroy()` asked of the worker on close |
| `app/src/main/java/id/hokw/patcher/ShizukuLauncher.kt` | `android/app/src/main/java/dev/halixm/hokacepatcher/ShizukuLauncher.kt` | permission of halixm-dev, 24 November 2026 | package; `open` kept as `openShizuku`; `isRunning`, `hasPermission`, `requestPermission`, `deniedPermanently`, `serverUid` added over the Shizuku API |
| `app/src/main/java/id/hokw/patcher/AppUpdateChecker.kt` | `android/app/src/main/java/dev/halixm/hokacepatcher/AppUpdateChecker.kt` (the prompt in `AppUpdatePrompt.kt` was not copied; our screen code is in `MainActivity.kt`) | permission of halixm-dev, 24 November 2026 | package; repository from `BuildConfig.RELEASE_REPO` (Gradle property `hokw.releaseRepo`) and an injectable connection factory per URL; result is a sealed `Outcome` (UpToDate, Newer, Older, NoRelease, RateLimited, Offline, Timeout, Invalid) instead of English messages; tag `android-v<five numbers>` via `PatchVersion.parse` (no legacy four-part versions); asset `HoKW-Language-Patcher-<version>.apk` under `releases/download/<tag>/`; `html_url` accepted only under the repository's releases, release body trimmed to 600 characters; HTTP hardening (10 s timeouts, 1 MiB cap, no redirects/caches, Accept, `X-GitHub-Api-Version`, product User-Agent) kept |
| `app/src/main/java/id/hokw/patcher/PrivilegedDeviceService.kt` | `android/app/src/main/java/dev/halixm/hokacepatcher/PrivilegedDeviceService.kt` (pattern only) | permission of halixm-dev, 24 November 2026 | not a copy: the constructor pair (no-arg and `(Context)`), `destroy()` ending the process and the stdout/stderr draining pattern follow hok-ace; the allow-listed shell (`identity`, `exec`, `execStream`, `streamStatus`, `push` with `CommandPolicy`) is this repository's work |

Other files from the plan in `docs/android.md` section 3 (`EngineAssets.kt`, `UiText.kt`,
`RunNotification.kt`, `DiagnosticTrace.kt`, the Gradle and manifest skeletons)
are added to this table by the step that copies them; a file under `android/` that is not listed
here was written for this repository. `WirelessDebugging.kt` and the Apache-2.0 ADB client are not
part of the first version (no Wireless debugging provider).

## Not derived

The patch engine (`hokw_patch/`), the translation data (`translations/`), the privileged device
service (an allow-listed shell; only its constructor/destroy/draining pattern follows hok-ace, see
the table), the patch worker, the Python bridge, the data packaging and the Mac-side adb harness
are this repository's own work. hok-ace-patch's game engine (`wxq_patch`), its game re-signing
key, the access-APK flow, the recovery/first-setup/re-download code, the texture codecs, the
Windows app and the CI workflows are not used.

## Account risk

Modifying game data violates Tencent's terms of service and accounts can be sanctioned. The
patcher does not touch the anti-cheat, the game process or the game binary, and it does not forge
CRCs or hashes, but the modification remains detectable. Nothing in this repository claims
otherwise.
