## TWRP device tree for Realme C25Y (RE54D1)
### BIG THANKS FOR GitFASTBOOT ( Realme C21Y PBRP Recovery Maintainer )
=========================================

The Realme C25Y (codenamed _RE54D1_) is a mid-range smartphone from Realme.

It was released in 2021, September 30.

## Device specifications

Basic   | Spec Sheet
-------:|:-------------------------
CPU     | Octa-core (2x1.8 GHz Cortex-A75 & 6x1.8 GHz Cortex-A55)
Chipset | Unisoc T610 (12 nm)
GPU     | Mali-G52 MP2
Memory  | 4GB, 6GB RAM
Shipped Android Version | 11R 
Storage | 64GB,128GB eMMC 5.1
Battery | 5000 mAh, non-removable
Display | 720 x 1600 pixels, 20:9 ratio (~270 ppi density)

## Features

(COMPLETELY UNTESTED AS OF NOW THE FOLLOWING LIST IS NOT ACCURATE)

Blocking checks
- [X] Correct screen/recovery size
- [X] Working Touch, screen
- [X] Backup to internal/microSD
- [X] Restore from internal/microSD
- [X] reboot to system
- [X] ADB


Medium checks
- [X] update.zip sideload
- [X] UI colors (red/blue inversions)
- [X] Screen goes off and on
- [X] F2FS/EXT4 Support, exFAT/NTFS where supported
- [X] all important partitions listed in mount/backup lists
- [X] backup/restore to/from external (USB-OTG) storage
- [X] backup/restore to/from adb (https://gerrit.omnirom.org/#/c/15943/)
- [ ] decrypt /data
- [X] Correct date


Minor checks
- [X] MTP export
- [X] reboot to bootloader
- [X] reboot to recovery
- [X] poweroff
- [X] battery level
- [X] temperature
- [ ] encrypted backups
- [X] input devices via USB (USB-OTG) - keyboard, mouse and disks
- [ ] USB mass storage export (device does not support it)
- [X] set brightness
- [ ] vibrate
- [X] screenshot
- [X] partition SD card

## Compile

First checkout minimal twrp with aosp tree:

```
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-11
repo sync -j$(nproc --all)
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/realme/RE54D1" name="Yoshk4e/android_device_realme_RE54D1" remote="github" revision="android-11" />
```

Finally execute these:

```
source build/envsetup.sh
repopick <needed patch>
lunch twrp_RE54D1-eng
mka bootimage -j$(nproc --all)
```
