fetch\_moveit\_kinetic
======================
The purpose of this package is to use `fetch_gazebo` with `MoveIt!` in ROS kinetic.

## Install
cd ~
mkdir -p fetch\_moveit\_ws/src
cd fetch\_moveit\_ws/src  # same directory as .rosinstall
git clone https://github.com/708yamaguchi/fetch\_moveit\_kinetic.git
cp fetch\_moveit\_kinetic/.rosinstall .rosinstall # you can use symbolic link
wstool update -t .
rosdep install --from-paths . --ignore-src -y -r
source /opt/ros/kinetic/setup.bash
cd ../
catkin build
source ~/fetch\_moveit\_ws/devel/setup.bash

## gazebo with MoveIt!
```
source /opt/ros/kinetic/setup.bash
source ~/fetch_moveit_ws/devel/setup.bash
roslaunch fetch_gazebo playground.launch
roslaunch fetch_moveit_config move_group.launch info:=true # launch only MoveIt!
# roslaunch fetch_gazebo_demo demo.launch # launch navigation, perception and Moveit!
```

#### .rosinstall
```
- git:
    local-name: fetchrobotics/fetch_gazebo
    uri: https://github.com/fetchrobotics/fetch_gazebo.git
    version: gazebo7  # for kinetic
- git:
    local-name: fetchrobotics/fetch_ros
    uri: https://github.com/fetchrobotics/fetch_ros.git
    version: indigo-devel  # for kinetic
```
