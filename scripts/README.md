# Titan Field Terminal

Repurposing an original Unihertz Titan into a pocket field terminal for robotics, systems work, SSH, runbooks, remote checks, and experimental mobile Linux exploration.

This repository is a public lab notebook, not a polished install guide. It documents the process of trying to turn an old physical-keyboard Android phone into a practical pocket terminal.

## Project Goal

Determine whether an old Unihertz Titan can become a useful pocket field terminal for robot operations, systems work, and mobile Linux experiments.

## Target Uses

- SSH into robot systems
- Read and edit robot runbooks
- Open camera stream URLs
- Check network/device status
- Take field notes
- Run small scripts
- Serve as a pocket companion to larger robotics projects

## Current Device

- Model: Unihertz Titan, original
- Android before modification: 10
- Build before modification: Titan_20221121
- Hardware: MT6771
- Storage type: UFS
- Bootloader: unlocked
- A/B slots: none

## Current Status

Ubuntu Touch successfully booted on the device using the manual UFS install path from the community port artifacts.

However, the physical keyboard behavior currently makes Ubuntu Touch impractical for this project. The keyboard appears to expose Unihertz-specific behavior that was configurable under stock Android but is not currently manageable in Ubuntu Touch through normal settings. Switching keyboard/input layouts did not resolve the issue.

So the project has reached **first breath**, but not yet **field-terminal viability**.

## Attempt Order

1. Ubuntu Touch / UBports community port
   - Status: boots successfully
   - Verdict: not currently practical due to physical keyboard behavior
2. Android-based fallback such as LineageOS/Gargoyle
   - Status: next likely investigation path
3. Termux-based field-terminal fallback
   - Status: practical fallback if Android-based workflow is the best fit

## First Breath Definition

For this project, “first breath” means the Titan successfully boots into a viable non-stock operating environment, or the recovery/failure notes become useful enough to publish.

That threshold has been met: Ubuntu Touch booted successfully, even though it is not yet usable as the intended field terminal.

## Notes

This project is experimental. It may include failed paths, awkward workarounds, recovery notes, and abandoned attempts. That is intentional.

The goal is not only to produce a working device, but to document what works, what breaks, and what is worth trying next.