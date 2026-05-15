# RobotOps Vision

The Titan Field Terminal is not intended to run full ROS 2 workloads locally.

Its practical role is to act as a pocket RobotOps console:

- SSH into robot systems
- Launch known ROS 2 bring-up scripts remotely
- Start/stop robot services
- Tail logs
- Open camera feeds
- Monitor basic robot status
- Trigger field scripts
- Store runbooks and field notes

## Architecture

Titan:
- Termux
- SSH
- Git
- browser bookmarks
- lightweight scripts or apps

Robot / robo-dev machine:
- ROS 2
- launch files
- camera streams
- hardware interfaces
- logs
- builds

## Future experiments

- Pair game controller to Titan
- Forward controller commands from Titan to robot
- Build a small Titan-side robot status dashboard
- Use Titan as a field display while another machine handles teleop