# Android Field Terminal Plan

## Why this branch exists

Ubuntu Touch booted successfully on the original Unihertz Titan, but the physical keyboard behavior makes it impractical as a field terminal.

The project goal is not OS purity. The goal is a useful pocket field terminal for robotics, systems work, SSH, runbooks, and mobile Linux experiments.

## New Hypothesis

An Android-based ROM, paired with Termux, may preserve enough Titan hardware/keyboard behavior to make the device useful while still providing a Linux-like terminal environment.

## Candidate Stack

- Gargoyle / LineageOS 20
- Termux
- OpenSSH
- Git
- tmux
- nano or vim
- Python
- rsync/scp
- Browser bookmarks for robot tools and camera URLs

## Success Criteria

The Titan is viable if it can:

- Type normally without keyboard/touchpad interference
- Connect to Wi-Fi reliably
- Run Termux
- SSH into another machine
- Read/edit runbooks
- Open robot camera/status URLs
- Sleep/wake without becoming annoying

## Current Status

- Ubuntu Touch first breath: achieved
- Ubuntu Touch field-terminal viability: blocked by keyboard behavior
- Next investigation: Gargoyle / LineageOS 20 as Android-based fallback