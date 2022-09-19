
## fdilink的imu驱动包
Deta-10-ros-v0.0.1
### 依赖：
```bash
sudo apt install ros-melodic-serial
```

### 使用：    
ahrs_driver.launch
```
<launch>
  <node pkg="fdilink_ahrs" name="ahrs_driver" type="ahrs_driver" output="screen" >
    <!-- 是否输出debug信息 -->
    <param name="debug"  value="false"/>
    
    <!-- 串口设备，可通过rules.d配置固定 -->
    <param name="port"  value="/dev/ttyUSB0"/>
    <!-- <param name="port"  value="/dev/ttyTHS1"/> -->

    <!-- 波特率 -->
    <param name="baud"  value="921600"/>

    <!-- 发布的imu话题名 -->
    <param name="imu_topic"  value="/imu"/>
    
    <!-- 发布的imu话题中的frame_id -->
    <param name="imu_frame"  value="imu"/>

    <!-- 地磁北的yaw角 --> # 二维指北的朝向，北为0，逆时针增加，0~2π的取值范围。
    <param name="mag_pose_2d_topic"  value="/mag_pose_2d"/>

    <!-- 发布的数据基于不同设备有不同的坐标系   -->
    <param name="device_type"  value="1"/> <!-- 0: origin_data, 1: for single imu or ucar in ROS, 2:for Xiao in ROS -->
  </node>
</launch> 
```
  其中`device_type`：
  
  0. Deta-10的原始坐标系模式
  1. 单独imu的坐标系模式

调用的ahrs_driver节点会发布`sensor_msgs/Imu`格式的imu topic。
```
std_msgs/Header header
  uint32 seq
  time stamp
  string frame_id
geometry_msgs/Quaternion orientation
  float64 x
  float64 y
  float64 z
  float64 w
float64[9] orientation_covariance
geometry_msgs/Vector3 angular_velocity
  float64 x
  float64 y
  float64 z
float64[9] angular_velocity_covariance
geometry_msgs/Vector3 linear_acceleration
  float64 x
  float64 y
  float64 z
float64[9] linear_acceleration_covariance
```
也会发布`geometry_msgs/Pose2D`格式的二维指北角话题，话题名默认为`/mag_pose_2d`。
```
float64 x
float64 y
float64 theta  # 指北角
```

### 2020-1-15
  维护了文件注释。

### 2020-10-20
  添加了`device_type`参数，可以在`ahrs_driver.launch`文件中指定设备类型，根据不同设备类型以不同的坐标系发布ROS的imu数据。
  其中：

  0. Deta-10的原始坐标系模式
  1. 单独imu的坐标系模式
