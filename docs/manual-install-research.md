# Manual Install Research

## Goal
Determine whether the Unihertz Titan Ubuntu Touch community port can be installed manually now that UBports Installer does not include the device.

## Known Starting Point
- Device: Unihertz Titan original
- Android base: 10
- Build: Titan_20221121
- Bootloader: unlocked
- ADB/fastboot: working
- UBports Installer 0.11.2 result: device not supported

## Research Questions
- Are prebuilt artifacts available?
- What partitions are flashed?
- Is Magisk/root required?
- Is vbmeta patching required?
- Is TWRP/recovery required?
- Is userdata overwritten?
- How is stock Android restored?
- Are there eMMC/UFS differences?
- What hardware works after boot?

## Sources
- UBports GitLab community port for `unihertz-titan`
- XDA/Reddit community install reports
- Unihertz Titan firmware/recovery resources