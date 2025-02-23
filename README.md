### Patches for supporting Dell XPS 9345 13" 2024 (codename `tributo`).

As changes will be merged upstream, redundant patches will be dropped from this repo, to only maitain diff on top of latest `linux-next`.

## Test setup
Kernel
* `linux-next`
* current patchset tested on `next-20250223`

Initramfs
* Ubuntu's auto-built from kernel installation
* Qualcomm's debian installer example (repackaged modules)

HW configurations tested
* 1920x1200 IPS non-touch, 120Hz
* 2880x1800 OLED touch, 60hz
* 32GB RAM

## Feature Matrix

* WIP - Something I am already working on
* TBH - Something I could work on, but not started / no sufficient progress was made
* QC  - Something I cannot work on, depends on Qualcomm's upstream support


| Feature                 | Status | Notes                                                                                                        |
| ----------------------- | -----: | ------------------------------------------------------------------------------------------------------------ |
| Battery Charging        |     ✅ |                                                                                                              |
| Battery Info            |     ✅ |                                                                                                              |
| Bluetooth               |     ✅ | Requires `linux-firmware` as of 20241017 to avoid warnings.                                                  |
| Camera                  | TBD/❌ | Likely ov02c10.                                                                                              |
| Display                 |     ✅ |                                                                                                              |
| Fingerprint Reader      | WIP/❌ | USB MP1 via PTN3222.                                                                                         |
| GPU Acceleration        |     ✅ | Requires firmware extraction from Windows.                                                                   |
| Keyboard                |     ✅ |                                                                                                              |
| Microphone              | TBD/❌ |                                                                                                              |
| NVMe                    |     ✅ |                                                                                                              |
| Speakers                | TBD/❌ |                                                                                                              |
| Suspend                 |     ✅ | Suspends well, lid switch working. Power drop in sleep isn't best, depends on X1E generic support.           |
| Touchpad                |     ✅ |                                                                                                              |
| TPM                     |  QC/❌ | Can't be accessed from userspace directly, TZ protected.                                                     |
| USB-C 3.0               |     ✅ |                                                                                                              |
| USB-C Booting           |     ✅ |                                                                                                              |
| USB-C DP Alt Mode       |     ✅ |                                                                                                              |
| USB-C DP over dock      |    WIP | Beta series to enable DP per-segment link training                                                           |
| Wi-Fi                   |     ✅ |                                                                                                              |
