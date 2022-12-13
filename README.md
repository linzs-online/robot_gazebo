# robot_gazebo
Scout2 robot carrying RS16 lidar/IMU/D435 sensors，running LIO-SAM in a room!

# 1. Environment 

### Development Environment

* Ubuntu 20.04 + ROS noetic

### Download and install required function package

* GTSAM 4.1
* Eigen 3.3.7
* PCL 1.9

more detail on my blog https://blog.csdn.net/weixin_40599145/article/details/126929222

# 2. Compile

```sh
$ mkdir -P robot_ws/src
$ cd robot_ws/src
$ git clone https://github.com/linzs-online/robot_gazebo.git
$ cd ..
$ catkin_make
```

# 3. Run

before your launch the demo, you should source the workspace

if you used bash

```sh
$ source ~/robot_ws/devel/setup.bash
```

if you used zsh

```sh
$ source ~/robot_ws/devel/setup.zsh
```

###  Start the simulation environment

```sh
$ roslaunch scout_gazebo scout_gazebo.launch
```

![gazebo](/png/gazebo.png)

### Start the lio-sam

```sh
$ roslaunch lio_sam run.launch
```

![rviz](/png/rviz.png)

### Control by keyboard

```sh
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

![mapping](/png/mapping.png)
