# Synthetic mobile audio feasibility

2026-11-27. Independent synthetic probes only; no product code.

| Environment | Result | Evidence |
|---|---|---|
| macOS ARM64 iOS Simulator | PASS | Run 45969208861, job 140405204613; 523 Hz power 12269687.357649343, 576000 samples at 48000 Hz |
| macOS ARM64 Android | FAIL | Run 45969330435; observed HV_UNSUPPORTED during emulator initialization; run cancelled |
| macOS Intel Android first attempt | FAIL | Run 45971433973; 100 boot polls with 3-second sleeps; cleanup responded to emulator kill |
| macOS Intel Android second attempt | PASS | Run 45973135552, job 140418204835; commit 81025e30a9b0fb58d3f1703042fe09231c50e295; boot completed at elapsed 446 seconds; 523 Hz power 33767375.92218591; 583680 samples at configured 48000 Hz |

Android second attempt explicitly used two virtual cores and extended boot polling to 200 iterations. Both changed, so their individual effect is not isolated. SDK installation, APK build, AVD creation, boot/capture and diagnostic upload passed. Artifact 15186372390, 16045 bytes, runner-reported ZIP SHA256 7255d90e607dcecf790c5052127b279af984c6171275dea169223bda3ab5280e; independent extraction/hash not performed for this artifact.

Both platform probes use a synthetic 523 Hz stimulus routed via BlackHole and a disposable native recording app. The tone power threshold is a limited feasibility check, not calibrated audio quality or a production test. Results do not establish reliability or optimal host. Future experiments should repeat cold/warm boot and resource benchmarks and evaluate parallel independent jobs with aggregate results.

Evidence: https://github.com/xenixcom/test/actions/runs/45969208861/job/140405204613 ; https://github.com/xenixcom/test/actions/runs/45971433973 ; https://github.com/xenixcom/test/actions/runs/45973135552/job/140418204835
