# Installation Guide

This guide will help you set up the project on your system.

---

## My Setup
### Powerful computer
- 5950X CPU 
- RTX 3080 GPU
- Ubuntu 22.04
### NVidia Jetson
- Jetson Orin Nano Developer Kit with JetPack 6.1
- Ubuntu 22.04

---

## Powerful Computer for Machine Learning

### ROS 2 Humble
https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debs.html

And make sure that you have the common extensions by: 
```bash
sudo apt install python3-colcon-common-extensions
```

### librealsense2
Follow the documentation at: 

https://github.com/IntelRealSense/librealsense/blob/master/doc/installation.md

### realsense2_camera ROS 2 package
```bash
sudo apt install ros-humble-realsense2-camera
```
### rplidar ROS 2 package
```bash
sudo apt install ros-humble-rplidar
```
### teleop_twist_joy package
```bash
sudo apt install ros-humble-teleop_twist_joy
```

### requirements.txt
These are selective things to install that are required, but you might already have. You may pick any of the items and run a
```bash
pip install <module>
```

### Install CUDA Toolkit
Install using the official documentation: 

https://developer.nvidia.com/cuda-downloads

These were my options: 
* Operating System: Linux

* Architecture: x86_64

* Distribution: Ubuntu 20.04

* Version: Latest (e.g., CUDA 12.0)

### Add CUDA paths
```bash
echo 'export PATH=/usr/local/cuda/bin:$PATH' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
```

### Verify installation
```bash
nvcc --version
```

### Install cuDNN
https://developer.nvidia.com/cudnn

Verify your options.

### Installing Tensorflow

The highest JetPack 6.1 will allow is tensorflow 2.18. It's recommended to keep the same version on both computers. The `requirements.txt` file found within the root of the workspace includes tensorflow and other needed installs. 

#### Install python virtual environment
```bash
sudo apt install -y python3-venv
```

#### Create the virtual environment
```bash
mkdir ~/tf_env
cd ~/tf_env
python3 -m venv tf-gpu
```

#### Sourcing Tensorflow with virtual environment
If you have a virtual environment creates, then either add 
```bash
source ~/tf_env/tf-gpu/bin/activate
```
to your `~/.bashrc` file or source it when spawning a new terminal.

#### Verify TensorFlow and GPU support
```bash
python -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
```

---

## NVidia Jetson

### FLASHING JETPACK
TODO

### ROS2 and librealsense2 Setup
This should follow the same procedure for the powerful computer above.

### Building the Workspace
This should follow the same procedure for the powerful computer above.

### Installing Tensorflow
[https://docs.nvidia.com/deeplearning/frameworks/install-tf-jetson-platform/index.html](https://docs.nvidia.com/deeplearning/frameworks/install-tf-jetson-platform/index.html)

#### Tensorflow 2.18
This is the most up to date version for Jetpack 6.1.
```bash
sudo pip3 install --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v61 tensorflow==2.16.1+nv24.08
```

You might need to downgrade your numpy. 
#### Test Tensorflow 
To test, run the following for GPU support: 
```bash
python3 -c "import tensorflow as tf; print(tf.config.list_physical_devices())"
```
---

## Sourcing the workspace
To automatically source your workspace setup each time you open a terminal, add the following lines to your `~/.bashrc` file:
```bash 
source ~/jeteja_ws/install/setup.bash
```
and if you did not when installing ros2 humble, source it by 
```bash
source /opt/ros/humble/install/setup.bash
```
---