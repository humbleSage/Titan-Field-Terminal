# Gargoyle / LineageOS Attempt

## Why this attempt exists

Ubuntu Touch booted successfully on the original Unihertz Titan, but the physical keyboard behavior made it impractical as a field terminal.

This attempt tests whether an Android-based custom ROM with Titan keyboard configuration can provide a more usable base for Titan Field Terminal.

## Starting State

- Device: Unihertz Titan original
- Storage: UFS
- Bootloader: unlocked
- Previous OS attempt: Ubuntu Touch
- Current goal: Flash Gargoyle / LineageOS 20 system image from current state

## Hypothesis

Gargoyle / LineageOS 20 may preserve or restore enough Titan keyboard behavior to make the device usable with Termux.

## Image / Artifact Used

Downloaded Gargoyle / LineageOS 20 image:

- File: `gargoyle_bvN.img`
- Local path: `~/Dev/titan-linux/downloads/gargoyle/`
- Variant: `bvN` / vanilla
- Notes:
  - Chosen because this is the original Titan, not Titan Pocket or Titan Slim.
  - Avoided `g66...` and `g55...` assets because they appeared to target other Unihertz devices.

## Flashing Notes

Initial attempt to flash the raw Gargoyle image from macOS failed:

```bash
fastboot flash system ./gargoyle_bvN.img
```

Error:

`fastboot: error: Failed reading from system`

This matched the earlier macOS fastboot issue encountered while flashing raw Ubuntu Touch userdata images.

## Sparse Image / Alternate Flashing Path

The raw system image could not be flashed directly from macOS fastboot.

Resolution:
- Used sparse conversion / alternate Linux tooling to flash the Gargoyle system image successfully.
- Converted the raw Gargoyle system image to Android sparse format before flashing:

```bash
img2simg gargoyle_bvN.img gargoyle_bvN.sparse.img
fastboot flash system ./gargoyle_bvN.sparse.img
```

Result:
- `system` partition flashed with Gargoyle.
- Device did not boot immediately after system flash.

## Boot Image Problem

After flashing Gargoyle system, the Titan did not boot.

Likely cause:
- The `system` partition contained Gargoyle / LineageOS.
- The `boot` partition still contained the Ubuntu Touch / Halium boot image from the previous experiment.

Interpretation:
Gargoyle requires an Android-compatible / Magisk-patched boot image. Flashing only the system image was not enough.

## Recovery Detour

The device reached Android Recovery with the “No command” dead robot screen.

Recovery menu access:

`Hold Power, then tap Volume Up once, then release.`

This opened the Android Recovery menu and allowed returning to Fastboot.

Notes:
- This was an important recovery step.
- The device was not bricked.
- Fastboot remained accessible after using the recovery menu.


## Boot Image Resolution

Gargoyle eventually booted after flashing a compatible Android / Magisk-patched boot image.

Command used:

```bash
fastboot flash boot ./magisk_patched-24000_Xkyu1_vbmeta.img
fastboot reboot
```

Notes:
- Gargoyle release notes state that rooting / Magisk-patched boot is not optional for a fully working system.
- The Gargoyle release assets did not include obvious boot images.
- Avoided boot images for g66... and g55... device families because this Titan reports as g61v71c2k_dfl_tee_u.
- The exact source/location for magisk_patched-24000_Xkyu1_vbmeta.img should be documented more clearly later.

## Gargoyle Keyboard Status

The on-screen keyboard issue was partially fixed by disabling the virtual keyboard when a physical keyboard is present:

```bash
adb shell settings put secure show_ime_with_hard_keyboard 0
adb reboot
```

This prevents the large software keyboard from covering the screen whenever text input is focused.

However, this may reduce access to special characters and terminal-oriented keys that were previously handled by the stock/Kika keyboard setup. For terminal use, the next likely workaround is Termux’s extra keys row rather than relying on the Android software keyboard.

Next test:
- Install/configure Termux.
- Test physical keyboard symbol access.
- Test terminal-critical keys: `/`, `-`, `_`, `~`, `|`, `\`, `:`, `@`, `Ctrl`, `Esc`, `Tab`.
- Configure Termux extra keys row.
- Decide whether this is good enough for field-terminal workflows.

## Current Result

Gargoyle / LineageOS boots.

Current status:
- OS boots: yes
- ADB works: yes
- Physical keyboard: partially usable
- Giant on-screen keyboard: mostly fixed with ADB settings hack
- Field-terminal viability: not proven yet

Current blocker:
- Hiding the virtual keyboard improves screen usability, but may remove convenient access to special characters needed for terminal use.

## Current Verdict

Gargoyle is more promising than Ubuntu Touch for this project because it boots and the keyboard behavior is at least partially manageable.

It is still far from polished. The next decision point is whether Termux plus physical keyboard plus extra keys row can make the Titan practical as a pocket field terminal.