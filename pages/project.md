---
layout: page
title: Project
comments: yes
permalink: /project/
---

# Pattern Recogination
## PSPNET_ROS

This project aims to do semantic segmentation in real-time using ROS action or service.

There are two modules: client and Server. 
The client will send the source image to request the semantic label from Server. 
Client-side does not need to deploy GPU. 
The server is designed to conduct semantic segmentation using GPU.

客户端: 定閱圖像topic,向服務器端實時發送語義分割請求;

服務端: 對圖像進行segmantic segmentating並返回分割結果;

客戶端與服務器可以運行在不同的主機上，本程序使用ROS進行通信;這樣客戶端並不需要配置GPU.

- https://aisl-serv6.aisl.cs.tut.ac.jp:20443/liu/pspnet_ros.git (Public to Github later)
-

## SegNet_ROS

# Semantic_mapping
## DEMO: mapping using ground truth

1.  Prepare

    -   PSPNet_ROS
    -   TUM dataset: e.g. `rgbd_dataset_freiburg1_room.bag`

2.  Config map type in yaml.  Open `params/tum_gt.yaml`:

    -   map_type: 0: point clound with color of RGB image
    -   map_type: 1: point clound with color semantic label

3.  Lauch these sequencially

    ```sh
    # mapping node
     roslaunch semantic_mapping tum_gt.launch

    # PSPNet segmentation server
    roslaunch pspnet_ros action_server_ade20k.launch

    # PSPNet client
    roslaunch pspnet_ros action_client.launch

    ```

4.  play bag file:

    ```sh
    rosbag play --clock rgbd_dataset_freiburg1_room.bag --hz 30
   
