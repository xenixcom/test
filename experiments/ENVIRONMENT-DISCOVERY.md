# Environment discovery — 2026-11-27

Public sandbox only. Synthetic test data; no private project data.

## Verified
- Git text CRUD, UTF-8 readback, branch, draft PR and issue lifecycle.
- Git blob/tree/commit/ref; atomic multi-file commit; stale expected SHA rejected (generic GraphQL error), matching SHA accepted.
- Binary Base64 round trip 8 bytes and 256 KiB; 1 MiB generated binary committed and verified byte-for-byte in Actions checkout (SHA256 4463d07e89027c670087b1197f2a2bc3c5ff3c27517a6e4bdabb10289e532835), then artifact downloaded. Direct contents read returned empty; direct blob read failed UTF-8 decoding. Arbitrary local-file upload and maximum transfer size not established.
- Standard Linux x86_64, Windows AMD64, macOS arm64 and macOS Intel runners; parallel matrix, push trigger, status/steps/logs, artifacts, successful retry after intentional failure. Retry while run active rejected with 403.
- Cross-run temporary marker absent in subsequent run; do not rely on runner persistence.
- Linux KVM initially EACCES; per-run ACL adjustment yielded API version 12. API33 x86_64 Android emulator boot and ADB verified after explicit AVD directory correction.
- macOS iOS simulator boot, launchctl, screenshot; ARM CoreAudio query and afplay.
- BlackHole 2ch 0.7.1 installed; initially not visible, audio service reload made visible. FFmpeg preflight failed (not installed); native Swift/AVAudioEngine probe succeeded: ROUTES_VERIFIED, FORMAT 48000.0 2, CAPTURE_SAMPLES 244800 (first channel), LOOPBACK_POWER 0.014899032718806791, TONE_RATIO 14899032718.806791, AUDIO_LOOPBACK_PASS, ROUTE_RESTORED. Ratio uses a denominator floor; not a calibrated SNR measurement.

## Boundaries
- No direct workflow dispatch or cancellation action exposed in inspected connector. Push trigger and retry available.
- Direct binary read has limits; checkout/artifact route verified only at tested sizes. No claim of arbitrary sandbox-to-repo file transfer.
- Host audio loopback is not simulator/emulator audio loopback; not a substitute for physical host testing.
- Runner versions and capacities are observed snapshots, not guarantees. Artifacts in probes retained one day; logs and artifacts subject to service retention.
- No private repository changes, no production workflow design, no ongoing service. Main sandbox head observed 6081ac857fd9947b1f475d67fdbe1e50fd7fb519.

## Evidence
- [Audio loopback capability / 45968605202](https://github.com/xenixcom/test/actions/runs/45968605202): completed/success, commit 0affb0d4cddb4b1e27ca795b901a8a97272ca234
- [Audio loopback capability / 45968457193](https://github.com/xenixcom/test/actions/runs/45968457193): completed/failure, commit b29bf8cf49c751663e770b42813bbb9683f88b98
- [Audio loopback capability / 45968305597](https://github.com/xenixcom/test/actions/runs/45968305597): completed/success, commit 99a375b7567986b4bb370c7b580a7e3b35b01cd8
- [macOS audio and Intel probe / 45968178036](https://github.com/xenixcom/test/actions/runs/45968178036): completed/success, commit fd43dc3e014adb8e5a97d222d25252139990317f
- [Android and runner lifecycle probe / 45968156391](https://github.com/xenixcom/test/actions/runs/45968156391): completed/success, commit cb4e9a3c75af738d58d10c75c9a961a580eff153
- [Binary integrity and lifecycle / 45968011452](https://github.com/xenixcom/test/actions/runs/45968011452): completed/success, commit cd39e2f71b7c9f5963fb402fcca2ec258d25e87f
- [Android and runner lifecycle probe / 45967915386](https://github.com/xenixcom/test/actions/runs/45967915386): completed/failure, commit 9cfc37fa8689a1fad5882bfb44a3e22bdfd9d114
- [Native runtime boundaries / 45967528959](https://github.com/xenixcom/test/actions/runs/45967528959): completed/success, commit 90b722b9602726c3a693737f9a7eb146e42cd501
- [Functional runner probe / 45967378644](https://github.com/xenixcom/test/actions/runs/45967378644): completed/success, commit a77f6a97e47a16a0b984050b5781d9665a9b1a15
- [Runner capability probe / 45967178355](https://github.com/xenixcom/test/actions/runs/45967178355): completed/success, commit e813ee983eedd0aaab73eb9f2d1643c9e469800b
- [Environment discovery matrix / 45966780116](https://github.com/xenixcom/test/actions/runs/45966780116): completed/success, commit f389e200789e6017ee5675f52ee3753a21719ce4
- [Sandbox smoke test / 45966423978](https://github.com/xenixcom/test/actions/runs/45966423978): completed/success, commit 6081ac857fd9947b1f475d67fdbe1e50fd7fb519
