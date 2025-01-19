# A1-QP-MPC-Controller配置教程

### 安装系统依赖

1. 安装ros-noetic

2. 安装系统依赖

   ```
   # 基础开发工具和库
   sudo apt-get update && sudo apt-get install -y \
     vim \
     libatlas-base-dev \
     libeigen3-dev \
     libgoogle-glog-dev \
     libsuitesparse-dev \
     python3-catkin-tools python3-osrf-pycommon \
     python3-matplotlib \
     gfortran \
     autoconf \
     git \
     coinor-libipopt-dev \
     curl \
     libopenmpi-dev \
     build-essential \
     libssl-dev
   ```
   
3. 安装ros相关包

   ```
   sudo apt-get install -y \
     ros-noetic-ros-control \
     ros-noetic-gazebo-ros \
     ros-noetic-joy \
     ros-noetic-ros-controllers \
     ros-noetic-robot-state-publisher
   ```
   
   
   
4. 安装OSQP

   ```
   # 安装OSQP
   cd /tmp
   git clone --recursive git@github.com:osqp/osqp.git
   cd osqp
   git checkout v0.6.0
   mkdir build && cd build
   cmake ..
   sudo make
   sudo make install
   ```

5. 安装osqp-eigen

   ```
   cd /tmp
   git clone https://github.com/robotology/osqp-eigen.git
   cd osqp-eigen
   git checkout v0.6.3
   mkdir build && cd build
   cmake ../
   sudo make
   sudo make install
   ```

   

### 运行

```
mkdir -p ws/src
cd ws
git clone git@github.com:unitreerobotics/unitree_legged_sdk.git

cd src
git clone git@github.com:LianzhaoZhang/a1_cpp.git
git clone --recursive git@github.com:ShuoYangRobotics/unitree_ros.git
```
删掉ws/src/unitree/ros/unitree_legged_real文件夹

```
catkin build -j
source ./devel/setup.bash
roslaunch unitree_gazebo normal.launch
roslaunch a1_cpp a1_ctrl.launch
```

