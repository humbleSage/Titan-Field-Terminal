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

## README Interpretation

The UBports Installer path does not support this Titan, but the community port README provides manual installation paths.

The project can be built manually, but prebuilt GitLab artifacts are available via the `devel-flashable` job. The install path depends on whether this Titan is eMMC or UFS.

Next blocker: identify storage type before flashing anything.

## Storage Type Check

Commands used:

```bash
adb shell getprop ro.boot.boot_devices
adb shell ls -l /dev/block/by-name | head -50
adb shell ls /sys/block
```

Observed:

- ro.boot.boot_devices: bootdevice,11230000.mmc
- /dev/block/by-name partitions point to /dev/block/sdc*
- /sys/block includes sda, sdb, and sdc
- No mmcblk0 block device was present

Conclusion:

This Titan should be treated as a UFS model for the Ubuntu Touch manual install path.

## Artifact Link Correction

The README artifact link was stale. The current default branch is `main`, and the UFS flashable job is named `devel-flashable-ufs`.

Corrected UFS artifact URL:
`https://gitlab.com/ubports/porting/community-ports/android10/unihertz-titan/unihertz-titan/-/jobs/artifacts/main/download?job=devel-flashable-ufs`

## UFS userdata image creation

Created `userdata.img` successfully on macOS using `mke2fs` from Android Platform Tools.

Artifact contents:

- `out/boot.img`
- `out/ubuntu.img`

Staging:

```bash
rm -rf userdata
mkdir userdata
cp out/ubuntu.img userdata/ubuntu.img
```

Image creation:

```bash
mke2fs -t ext4 -O '^metadata_csum' -d userdata userdata.img 7000000
```

Result:

- userdata.img: 6.7G
- file userdata.img: Linux rev 1.0 ext4 filesystem data

## Fastboot raw userdata flash failure on macOS

Attempted to flash raw ext4 `userdata.img` from macOS using Android Platform Tools fastboot.

Results:

```bash
fastboot flash userdata userdata.img
fastboot flash userdata ./userdata.img
```

Both failed with:

`fastboot: error: Failed reading from userdata`

Rebuilt a smaller ext4 image:

`mke2fs -t ext4 -b 4096 -O '^metadata_csum' -m 0 -d userdata userdata.img 1000000`

Resulting image:

- userdata.img: 3.8G
- ext4 filesystem detected by file

Flashing still failed with the same fastboot read error.

Next step: use Linux laptop and img2simg from android-sdk-libsparse-utils to convert userdata.img to Android sparse format, then flash userdata.sparse.img.