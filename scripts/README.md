# Titan Field Terminal

Repurposing an original Unihertz Titan into a pocket Linux/mobile terminal for robotics field work, SSH, runbooks, remote checks, and experimental mobile Linux exploration.

This repository is currently a local lab notebook. It will be published after the device successfully boots into its first viable non-stock operating environment.

## Project Goal

Determine whether an old physical-keyboard Android phone can become a practical pocket terminal for robot operations.

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
- Android: 10
- Build: Titan_20221121
- Hardware: MT6771
- Bootloader: locked
- A/B slots: none

## Attempt Order

1. Ubuntu Touch / UBports community port
2. Android-based fallback such as LineageOS/Gargoyle
3. Termux-based RobotOps terminal fallback

## Publishing Rule

This repository becomes public after first breath: the device boots into a viable non-stock operating environment, or the recovery/failure notes become useful enough to publish.