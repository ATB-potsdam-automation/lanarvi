# lanarvi

## About
Main workspace for running the point cloud mapping in ROS2 on the CEOL.
The main launch file is included in the ceol_bringup package (measurement.launch.py).
In the current version, only the ceol_node and the SICK driver is launched,Point Cloud processing needs to be launched seperately.

<details open="open">
<summary>Table of Contents</summary>

- [About](#about)
- [Requirements](#requirements)
- [Installation](#installation)
- [Running the Measurment](#running-the-measurement)
- [Running single Nodes](#running-single-nodes)
</details>

-------------------------------------------------------------------------------------
## Requirements
Setup with ROS2 Humble installation

-------------------------------------------------------------------------------------

## INSTALLATION

### installation as a new catkin workspace 

source ROS. Probably the command will look like this:
```sh
source /opt/ros/humble/install/setup.bash
```
clone the workspace

```sh
cd $(your_workspace_root_folder)
git clone https://github.com/ATB-potsdam-automation/lanarvi.git ./lanarvi_ws/
```
cd into the workspace
```sh
cd /lanarvi_ws
```
build the msgpack11 package for the sick-driver
```sh
colcon build --symlink-install --packages-select msgpack11
```
source the workspace
```sh
source install/setup.bash
```
build the rest of the workspace
```sh
colcon build --symlink-install
```
source the workspace again
```sh
source install/setup.bash
```

## RUNNING THE MEASUREMENT

### Running without pointcloud pipeline
```sh
ros2 launch ceol_bringup measurement.launch.py
```

### Running with pointcloud pipeline
```sh
ros2 launch TODO TODO
```

### launch the data playback of existing rosbags
```sh
ros2 launch TODO TODO
```

## RUNNING TSINGLE NODES 

run CCAN-communication with CEOL. This starts two nodes: socket_can_receiver and ceol_node
```sh
ros2 launch ros2_socketcan socket_can_receiver.launch.py && ros2 run ceol_base ceol_node
```

