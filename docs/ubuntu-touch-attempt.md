# Ubuntu Touch Attempt

## Device
- Model: Unihertz Titan original
- Android base before attempt: 10
- Build before attempt: Titan_20221121
- Hardware: MT6771
- Bootloader unlocked: yes
- A/B slots: none

## Goal
Attempt Ubuntu Touch as the first full mobile Linux target for Titan Field Terminal.

## Preflight
- ADB works: Y
- Fastboot works: Y
- Battery level: 98%
- UBports Installer version: 0.11.2
- Install method: ??
- Notes:

## Installer Detection

UBports Installer version: 0.11.2

Result:
- Device detected as: Titan
- Installer message: Device not supported
- Manual install option offered: yes

Notes:
The installer did not auto-recognize the Titan as a supported device even though a community port exists.

## Attempt 001 - UBports Installer

### Date
2026-05-11

### Host
macOS, UBports Installer 0.11.2

### Device State
- Device: Unihertz Titan original
- Android: 10
- Build: Titan_20221121
- Bootloader: unlocked
- ADB: working
- Fastboot: working

### Result
UBports Installer detected the device as `Titan`, but reported:

> Device not supported
> Sorry, there is no port for this device yet.

Manual device selection was checked, but the installer did not include a port for this device.

### Decision
Stopped before attempting to install using an incorrect device profile.

### Interpretation
The graphical UBports Installer path is not currently viable for this Titan. Next step is to investigate manual/community-port installation using the existing `unihertz-titan` Ubuntu Touch community port materials.

### Status
Blocked at installer database/device-profile stage. Device remains bootable and controllable.

## Result
- Boots:
- Wi-Fi:
- Keyboard:
- Terminal:
- Charging:
- Sleep/wake:
- Notes:

## Verdict