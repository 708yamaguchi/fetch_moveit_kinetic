fetch\_moveit\_kinetic
======================
The purpose of this package is to use `fetch_gazebo` with `MoveIt!` in ROS kinetic.

## Install
```bash
cd ~
mkdir -p fetch_moveit_ws/src
cd fetch_moveit_ws/src  # same directory as .rosinstall
git clone https://github.com/708yamaguchi/fetch_moveit_kinetic.git
cp fetch_moveit_kinetic/.rosinstall .rosinstall # you can use symbolic link
wstool update -t .
rosdep install --from-paths . --ignore-src -y -r
source /opt/ros/kinetic/setup.bash
cd ../
catkin build
source ~/fetch_moveit_ws/devel/setup.bash
```

## Use fetch\_gazebo with MoveIt!
```bash
source /opt/ros/kinetic/setup.bash
source ~/fetch_moveit_ws/devel/setup.bash
# Terminal 1
roslaunch fetch_gazebo playground.launch
# Terminal 2
roslaunch fetch_moveit_config move_group.launch info:=true # launch only MoveIt!
# roslaunch fetch_gazebo_demo demo.launch # launch navigation, perception and Moveit!
# Terminal 3
cd ~/fetch_moveit_ws/src
rviz -d fetch_moveit_kinetic/fetch_moveit_kinetic.rviz
```
