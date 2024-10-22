### Patches for supporting Dell XPS 9345 13" 2024 (codename `tributo`).

As changes will be merged upstream, redundant patches will be dropped from this repo, to only maitain diff on top of latest `linux-next`.
Easiest way to install is by using Ubuntu's [X1E Dev image](https://discourse.ubuntu.com/t/ubuntu-24-10-concept-snapdragon-x-elite/48800), which now includes most/all of changes from this repo.

## Test setup
Kernel
* `linux-next`, current patchset tested on `next-20241021`
* 6.11 tree from Ubuntu's X1E dev image.

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
| ----------------------- | -------: | ------------------------------------------------------------------------------------------------------------ |
| Battery Charging        |     ✅ |                                                                                                              |
| Battery Info            |     ✅ |                                                                                                              |
| Bluetooth               |     ✅ | Requires `linux-firmware` as of 20241017 to avoid warnings.                                                  |
| Camera                  | TBD/❌ | Likely ov02c10.                                                                                              |
| Display                 |     ✅ |                                                                                                              |
| EC/Embedded Controller  | TBD/❌ | Responsible for Fan speeds, OS-controlled keyboard backlight, special keyboard keys & more.                  |
| Fingerprint Reader      | WIP/❌ | USB MP1 via PTN3222.                                                                                         |
| GPU Acceleration        |     ✅ | Requires firmware extraction from Windows.                                                                   |
| Keyboard                |     ✅ | Special keys (eg. mute MIC) not working. Backlight control works from keyboard, but not yet from Gnome.      |
| Microphone              | TBD/❌ |                                                                                                              |
| NVMe                    |     ✅ |                                                                                                              |
| Speakers                | TBD/❌ |                                                                                                              |
| Suspend                 |     ✅ | Suspends well, lid switch working. Power drop in sleep isn't best, depends on X1E generic support.           |
| Touchpad                |     ✅ |                                                                                                              |
| TPM                     |  QC/❌ | Can't be accessed from userspace directly, TZ protected.                                                     |
| USB-C 3.0               | WIP/❌ | Only in one orientation. PS8830 Retimer patchset coming soon.                                                |
| USB-C Booting           |     ✅ |                                                                                                              |
| USB-C DP Alt Mode       |     ❌ | Requires retimer patch. Depends on QCom's unreleased MSN DP driver fixes.                                    |
| Wi-Fi                   |     ✅ |                                                                                                              |
