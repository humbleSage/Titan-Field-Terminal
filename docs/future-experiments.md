# Future Experiments

These are intentionally not part of the core Titan Field Terminal path.

## Go

Status: approved curiosity / useful learning tool.

Goal:
Use the Titan for small Go CLI programs and learning exercises.

## proot-distro

Status: installed as curiosity shelf.

Goal:
Explore Debian or Ubuntu userland inside Termux without changing the phone OS again.

Not core because:
- PRoot is slower than native Termux.
- It does not turn the Titan into a normal Linux machine.
- It may increase storage and maintenance friction.

## X11 / GUI apps

Status: future side quest.

Goal:
Test Termux:X11 and lightweight GUI apps.

Not core because:
- Screen is small.
- Input is awkward.
- GUI work belongs on the laptop unless proven otherwise.

## ROS 2 local feasibility

Status: future moonshot.

Goal:
Investigate whether any tiny ROS 2 or ROS-adjacent workflow can run locally on the Titan.

Preferred practical alternative:
Use the Titan to SSH into a real ROS 2 machine and run ROS tools remotely.

Core rule:
The Titan should control/check ROS systems, not replace the robo-dev laptop.