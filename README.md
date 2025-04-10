### Patches for supporting Dell XPS 9345 13" 2024 (codename `tributo`).

As changes will be merged upstream, redundant patches will be dropped from this repo, to only maitain diff on top of latest `linux-next`.

## Test setup
Kernel
* `linux-next`
* current patchset tested on `next-20250327`

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
| Camera                  |     QC | ov02c10. Initial support in Linaro's tree                                                                    |
| Display                 |     ✅ |                                                                                                              |
| Fingerprint Reader      |     ✅ |                                                                                                              |
| GPU Acceleration        |     ✅ | Requires firmware extraction from Windows.                                                                   |
| Keyboard                |     ✅ |                                                                                                              |
| Microphone              |     ✅ |                                                                                                              |
| NVMe                    |     ✅ |                                                                                                              |
| Speakers                |     ✅ | Minor issues such as bad sound quality, L R are swapped.                                                     |
| Suspend                 |     ✅ | Suspends well, lid switch working. Power drop in sleep isn't best, depends on X1E generic support.           |
| Touchpad                |     ✅ |                                                                                                              |
| TPM                     |  QC/❌ | Can't be accessed from userspace directly, TZ protected.                                                     |
| USB-C 3.0               |     ✅ |                                                                                                              |
| USB-C Booting           |     ✅ |                                                                                                              |
| USB-C DP Alt Mode       |     ✅ |                                                                                                              |
| USB-C DP over dock      |     ✅ | Series on the lists, not yet merged                                                                          |
| Wi-Fi                   |     ✅ |                                                                                                              |
| EC                      |  QC/❌ | Proprietary controller

## Audio configuration  

Besides device tree changes in kernel, two things are required to get audio working: alsa configuration and toplogy firmware.

### Audioreach-topology
* Download latest sources with Dell XPS 9345 support from https://github.com/alexVinarskis/audioreach-topology/tree/dell-xps-9345
* Build via
```bash
cmake .
cmake --build .
```
* Install compiled binary to firmware path via
```bash
sudo cp qcom/x1e80100/dell/xps13-9345/X1E80100-Dell-XPS-13-9345-tplg.bin /lib/firmware/updates/qcom/x1e80100/X1E80100-Dell-XPS-13-9345-tplg.bin
```

### Alsa configuration
* Download lastet configuration with Dell XPS 9345 support from https://github.com/alexVinarskis/alsa-ucm-conf/tree/dell-xps-9345
* Follow instructions in `README.md` to unpack

Reboot to apply changes. You should now have:
* Working x2 speakers
* Working x2 microphones
* Working audio jack with microphone

Audio over HDMI and USB Type-C DP alt mode is not yet supported.
