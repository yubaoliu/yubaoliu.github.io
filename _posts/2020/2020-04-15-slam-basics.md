---
layout: "post"
title: "SLAM Basics"
date: "2020-04-15 09:14"
categories: SLAM
tags: [SLAM]
toc: true
comments: true
---

# Introduction

本文將SLAM BOOK中的示例及博客中的示例自己復現並整理。

My source code:

```sh
git clone https://github.com/yubaoliu/SLAMLib.git
```

References:
```sh
git clone https://github.com/yubaoliu/slambook2.git
```

#  从图像到点云

## Prepare:
 - Kinect2 camera
 - Install Requirements

    ```sh
    sudo apt-get install build-essential libgtk2.0-dev libjpeg-dev libtiff4-dev libjasper-dev libopenexr-dev cmake python-dev python-numpy python-tk libtbb-dev libeigen2-dev yasm libfaac-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev libx264-dev libqt4-dev libqt4-opengl-dev sphinx-common texlive-latex-extra libv4l-dev libdc1394-22-dev libavcodec-dev libavformat-dev libswscale-dev
    ```
 - Install PCL

    ```sh
    sudo add-apt-repository ppa:v-launchpad-jochen-sprickerhof-de/pcl
    sudo apt-get update
    sudo apt-get install libpcl-all
    ```

 - pcl_viewer

    ```sh
    sudo apt-get install libpcl-dev pcl-tools
    ```
## Practice
### Create point cloud use depth and rgb image
- Inpub image

![rgb](http://qiniu.yubaoliu.cn/markdown-img-paste-20200415155846883.png)

![depth](http://qiniu.yubaoliu.cn/markdown-img-paste-20200415155923159.png)

```sh
./generate_pointcloud rgb.png depth.png
```

- View Point Cloud

    ```sh
    pcl_viewer pointcloud.pcd
    ```
![pcd](http://qiniu.yubaoliu.cn/markdown-img-paste-20200415155533141.png)

### Start Kinect2

    ```sh
    roslaunch kinect2_bridge kinect2_bridge.launch
    ```

- View image
    ```sh
    rosrun image_view image_view image:=/kinect2/qhd/image_color
    ```

    ![](http://qiniu.yubaoliu.cn/markdown-img-paste-20200415101312426.png)



# Turtlebot

```sh
roslaunch turtlebot_bringup minimal.launch (启动底座)
turtlebot_teleop keyboard_teleop.launch (启动遥控)
```
