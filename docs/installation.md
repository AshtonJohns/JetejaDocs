# Installation Guide

This guide will help you set up the project on your system.

---

## Required Software

Ensure the following software is installed before proceeding:

- **ROS 2 Humble**
- **realsense2_camera** ROS 2 package
```bash
sudo apt install ros-humble-realsense2-camera
```
- **rplidar** ros2 package
```bash
sudo apt install ros-humble-rplidar
```
- **teleop_twist_joy** package
```bash
sudo apt install ros-humble-teleop_twist_joy
```
- **mpremote** 
```bash
pip install mpremote
```


---

## Building the Workspace

1. **Open a terminal** and navigate to your workspace directory:
```bash
cd ~/jeteja_ws
```
2. **Clone the repository** to your workspace directory:
```bash
git clone https://github.com/AshtonJohns/UCAJetson.git
```
3. **Build the project**:
```bash
colcon build
```

## Simplify Access for Future Sessions
To automatically source your workspace setup each time you open a terminal, add the following lines to your `~/.bashrc file`:
```bash 
source ~/jeteja_ws/install/setup.py
source /opt/ros/humble/install/setup.py
```