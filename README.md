# ros_in_hand_scanner

## Description
The ROS In-hand scanner provides a 3D Scanning application based on the PCL In-hand scanner for small objects by Martin Sälzle and the PCL developers.

Original PCL Documentation can be found here:

http://pointclouds.org/documentation/tutorials/in_hand_scanner.php

The following video shows a scanning process using Intel RealSense Camera.
https://drive.google.com/file/d/0B-EoR_OK9GCgcEw3V0l1ZnNPU2s/view

## Dependencies 
This package needs PCL 1.8.0 to be installed. For further information, see the following link: http://pointclouds.org/documentation/tutorials/compiling_pcl_posix.php#experimental

## Installation

```
#Prepare Workspace
source /opt/ros/indigo/setup.bash
mkdir -p ~/rihs_ws/src
cd ~/rihs_ws/src
catkin_init_workspace
cd ~/rihs_ws/
catkin_make
source devel/setup.bash

#Get ROS In-hand scanner
cd ~/rihs_ws/src
git clone http://github.com/RodBelaFarin/ros_in_hand_scanner
cd ~/rihs_ws/

#Install
rosdep update
rosdep install ros_in_hand_scanner
catkin_make
```

## Topics
```
Subscriber Topic: camera/depth_registered/points
Message Type: sensor_msgs/PointCloud2
Description: organized point cloud
```

## Usage
Some quick infos on how to use.

Start the ROS In-hand scanner:
```
roscore
rosrun ros_in_hand_scanner ros_in_hand_scanner_node
```

Due to performance issues, a realtime registration is very slow with down to < 0.1 fps.
A workaround is to record a rosbag file during the scanprocess itself. You can use the preview window to get a view of your actual scan orientation.
Play the rosbag file afterwards with a low rate ~0.1 and start registration now.
Follow the hints in the PCL documentation for your scan process.
