# robot_gazebo
An scout2 robot carrying RS16 lidar/IMU/D435 sensors，running LIO-SAM in a room!

# 1. Environment 

### Development Environment

* Ubuntu 20.04 + ROS noetic

### Download and install required function package

* GTSAM 4.1
* Eigen 3.3.7
* PCL 1.9

more detail in my blog 

# 2. Run

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