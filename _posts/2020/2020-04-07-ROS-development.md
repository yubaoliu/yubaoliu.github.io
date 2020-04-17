---
layout: "post"
title: "ROS Development"
date: "2020-04-07 16:09"
categories: ROS
tags: [ROS]
toc: true
comments: true
---

# TF

```sh
rosrun tf view_frames
```
Example:
[tum1_freiburg1_room pdf](/assets/pdf/tum1_freiburg1_room_tf.pdf)

# Parames

```sh
<rosparam command="load" file="FILENAME" />

<param name="params_a" type="yaml" command="cat &quot;$(find roslaunch)/test/params.yaml&quot;" />
```

get parameters:

```cpp
 nh.param<std::string>("default_param", default_param, "default_value");

 int i;
 nh.param("my_num", i, 42);
```

 # comment

 ```sh
 <!-- Parameters for dynamic elements -->

 <launch>
 	<?ignore
 	<node name="mapper" type="dynamic_mapper" pkg="ethzasl_icp_mapper" output="screen">
 		<param name="eps_a" value="0.004"/><!--1 deg = 0.017rad-->
 	</node>
 	?>

 	<node pkg="tf" type="static_transform_publisher" name="correction_tf" args="0 0 0 0 0.2 0 /pointcloud /boat_level 100"/>
 </launch>
 ```
