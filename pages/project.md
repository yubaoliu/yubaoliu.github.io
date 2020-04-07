---
layout: page
title: Project
comments: yes
permalink: /project/
---

# Pattern Recogination
## PSPNET_ROS

This project aims to do semantic segmentation in real-time using ROS action or service.

There are two modules: client and Server. The client will send the source image to request the semantic label from Server. Client-side does not need to deploy GPU. The server is designed to conduct semantic segmentation using GPU.

客户端: 定閱圖像topic,向服務器端實時發送語義分割請求;

服務端: 對圖像進行segmantic segmentating並返回分割結果;

客戶端與服務器可以運行在不同的主機上，本程序使用ROS進行通信;這樣客戶端並不需要配置GPU.

- https://aisl-serv6.aisl.cs.tut.ac.jp:20443/liu/pspnet_ros.git (Public to Github later)
-

## SegNet_ROS

## Semantic_map
