---
layout: "post"
title: "Realsense"
date: "2020-04-23 15:27"
categories: articles
tags: [realsense]
toc: true
comments: true
---

# Resources
-   [Get started](https://realsense.intel.com/get-started/)
-   [IntelRealSense/librealsense-Github](https://github.com/IntelRealSense/librealsense)
-   [Intel® RealSense™ SDK 2.0 Github User Guide](https://www.intel.com/content/dam/support/us/en/documents/emerging-technologies/intel-realsense-technology/Intel-RealSense-SDK2-Github-Guide.pdf)
-   Intel® RealSense™ SDK 2.0 (build 2.19.0)
    [Download](https://github.com/IntelRealSense/librealsense/releases/tag/v2.19.0)
-   Intel® RealSense™ Depth Cameras D435i
-   ROS Wrapper 2.0 for Intel® RealSense™ Devices (build 2.2.1)
    [Download](https://github.com/intel-ros/realsense/releases)
- SLAM with D435i: [wiki](https://github.com/intel-ros/realsense/wiki/SLAM-with-D435i)

# Building librealsense2 SDK
## Preparation
- RealSense Camere: my device is D435i
- Ubuntu >= 16.04
```sh
Ubuntu 16.04/18.04 LTS (Linux Kernels 4.4, 4.8 ,4.10, 4.13, 4.15 and
4.16)
```

Refer [Linux Ubuntu Installation](https://github.com/IntelRealSense/librealsense/blob/master/doc/installation.md)

- Build librealsenseSDK on Ubuntu 18

```sh
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install git libssl-dev libusb-1.0-0-dev pkg-config libgtk-3-dev
sudo apt-get install libglfw3-dev libgl1-mesa-dev libglu1-mesa-dev
git clone https://github.com/IntelRealSense/librealsense.git
cd librealsense
./scripts/setup_udev_rules.sh
./scripts/patch-realsense-ubuntu-lts.sh
```
- Build and install

```sh
mkdir build && cd build
cmake ../ -DCMAKE_BUILD_TYPE=Release -DBUILD_EXAMPLES=true
make -j3
make install or sudo make install
```

- Recompile and install librealsense binaries

`sudo make uninstall && make clean && make && sudo make install`

- Remove all RealSense™ SDK-related packages with:

`dpkg -l | grep "realsense" | cut -d " " -f 3 | xargs sudo dpkg --purge`

- realsense-viewer

Reconnect the Intel RealSense depth camera and run:

## Tools
- **realsense-viewer**

To verify the installation.

If not working, reboot your PC and try again.

![](https://i.loli.net/2019/02/24/5c728a981f7a7.png)


- `./SimpleViewer`

![](https://i.loli.net/2019/02/26/5c752f5f1be70.png) ./NiViewer

![](https://i.loli.net/2019/02/26/5c753184142b0.png)


# ROS Wrapper
- Install

 ```sh
 sudo apt-get install ros-kinetic-realsense2-camera
 ```
- ROS: RGBD Poind Cloud

 ```sh
roslaunch realsense2_camera rs_camera.launch filters:=pointcloud
```

- ROS: Start the camera node
 ```sh
roslaunch realsense2_camera rs_camera.launch
```

![](https://i.loli.net/2019/03/08/5c82255d93cdc.png)


# sugestion

Important notes: - Don't use the pre-build packages, try to build
with source code. I don't know why - Make sure the SDK's version is
compatible with ROS Wrapper's version

- Error when execute ./scripts/patch-realsense-ubuntu-lts.sh

Error Description:

```sh
make: Leaving directory '/home/yubao/GitProject/librealsense-2.19.0/ubuntu-xenial-hwe'
Patched kernels modules were created successfully

Replacing videodev :
    Module videodev  is used by videobuf2_core
    Unloading dependency videobuf2_core
    modprobe: FATAL: Module videobuf2_core is in use.
Failed to unload module videobuf2_core. error type 1 . Operation is aborted
yubao@yubao-Z370M-S01:~/GitProject/librealsense-2.19.0$
```

Solution:

```sh
yubao@yubao-Z370M-S01:~/catkin_ws$ lsmod | grep videobuf2_core
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
videodev              180224  3 videobuf2_core,videobuf2_v4l2,uvcvideo
yubao@yubao-Z370M-S01:~/catkin_ws$ sudo modprobe -r uvcvideo
yubao@yubao-Z370M-S01:~/catkin_ws$ lsmod | grep videobuf2_core
```
