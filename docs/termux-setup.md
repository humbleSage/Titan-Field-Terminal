# Termux Setup

## Current Status

Termux is installed and usable on Gargoyle / LineageOS.

The physical keyboard is usable enough to continue. The exact Termux extra-keys layout is still being tuned over time, but it is no longer blocking the project.

## Android UI Fixes

Soft keyboard hidden when physical keyboard is present:

```bash
adb shell settings put secure show_ime_with_hard_keyboard 0
adb reboot
```

Gesture navigation enabled through Android settings to remove the soft navigation bar and gain vertical screen space.

## Termux Packages

Planned base package install:

```bash
pkg update
pkg upgrade
pkg install openssh git tmux nano vim python rsync curl wget jq
```

## Installed package set

Core field-terminal packages:

```bash
pkg install openssh git tmux nano vim python rsync curl wget jq htop tree ripgrep fd unzip zip tar gzip xz-utils less man termux-tools
```

Small development/debug packages:

`pkg install clang make cmake pkg-config gdb lldb`

Network/debug packages:

`pkg install dnsutils iproute2 net-tools nmap openssl`

Optional:

`pkg install nnn gh`

Intent:

This package set is meant to make the Titan useful as a pocket field terminal: SSH, Git, notes, scripts, network checks, small C/Python experiments, and robot/system troubleshooting. Heavy GUI work, ROS 2 development, embedded firmware workflows, CAD, and full IDE workflows remain laptop tasks.


## Current Verdict

Keyboard and screen usability are good enough to proceed to SSH and field workflow testing. Customization will probably be an ongoing process.