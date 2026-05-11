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

## First Breath

### Result
Ubuntu Touch booted successfully on the original Unihertz Titan.

### Notes
- Device reached Ubuntu Touch setup.
- Setup screens appear scaled for a more conventional phone display.
- Some setup UI elements do not adapt cleanly to the Titan screen dimensions.
- Some keyboard input is inconsistent or not accepted in parts of setup.
- The Titan was already an unusual Android phone, so some ergonomic weirdness is expected.

### Verdict
First breath achieved. Ubuntu Touch manual install path is viable enough to continue testing.

## Keyboard Quirks

- Test English layout vs Unihertz layout
- Identify which keys work
- Identify broken modifiers/symbols
- Determine whether keyboard-as-navigation/touchpad exists in Ubuntu Touch
- If needed, inspect `/dev/input` events and keymaps

## Keyboard Blocker

Ubuntu Touch booted, but the physical keyboard behavior makes the device impractical as a field terminal.

Observed:
- Keyboard behavior is inconsistent/quirky.
- The issue appears deeper than a language/layout setting.
- Switching keyboard/input layout did not resolve it.
- The old Android build had a Unihertz-specific keyboard/navigation feature that could be disabled.
- Ubuntu Touch does not appear to expose an equivalent control during initial testing.

Interpretation:
The device likely exposes vendor-specific physical keyboard / touch-navigation behavior that Ubuntu Touch does not handle cleanly. The port boots, but the Titan is not currently usable as a practical field terminal under Ubuntu Touch.

Verdict:
Ubuntu Touch is technically viable enough to boot, but not functionally viable for this project without deeper input-driver/keymap work.