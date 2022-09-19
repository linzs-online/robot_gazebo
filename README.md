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

![gazebo](https://img-blog.csdnimg.cn/39c58cb0d9ad4754a66f2a76ddc0bb73.png)

### Start the lio-sam

```sh
$ roslaunch lio_sam run.launch
```

![rviz](https://img-blog.csdnimg.cn/d43b87db3df747b788c51d39479910bc.png)

### Control by keyboard

```sh
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

![mapping](https://img-blog.csdnimg.cn/5a4d7d38c42845fc8dfe065fbc0dc41a.png)