# Session Log

## Session 001 - Recon

### Goal
Identify the Unihertz Titan, confirm Mac tooling, and prepare for a future Ubuntu Touch attempt.

### Confirmed
- ADB works on Mac.
- Fastboot works on Mac.
- Device is original Unihertz Titan.
- Android version is 10.
- Build is Titan_20221121.
- Hardware platform is MT6771.
- Bootloader is currently locked.
- Device has no A/B slots.

### Current status
Read-only recon complete. No destructive changes made.

### Next
- Charge device to 70-80%+.
- Confirm OEM unlocking is enabled in Developer Options.
- Capture sanitized recon logs.
- Prepare recovery notes before bootloader unlock.

## Session 002 - Bootloader Unlock

### Goal
Unlock the Titan bootloader and confirm control still works afterward.

### Result
- Bootloader unlock command: `fastboot flashing unlock`
- Device wiped: yes
- Android booted after wipe: yes
- ADB works after wipe: yes
- Fastboot works after wipe: yes
- `fastboot getvar unlocked`: yes
- `secure`: no
- Warranty flag changed from yes to no

### Notes
Unlock flow completed successfully from macOS using Android Platform Tools.
After-unlock fastboot log captured locally at:

`recon/fastboot-getvar-all-after-unlock.raw.txt`

### Next
Prepare for Ubuntu Touch / UBports install attempt.

## Session 003 - Ubuntu Touch First Breath

### Goal
Flash the manual Ubuntu Touch community-port images and determine whether the Titan can boot.

### Result
Success. The Titan booted into Ubuntu Touch setup.

### Quirks Observed
- Setup UI is not well adapted to Titan screen dimensions.
- Some keyboard input does not work consistently during setup.
- UI appears scaled for a conventional phone.

### Status
First breath achieved.