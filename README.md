# open3d_slam_private

This project provides tools for robot **LiDAR-based mapping and localization**.

This is an advanced and fine-tuned version of open3d_slam that is private to RSL for internal projects and development.

## Build
For now to build this repository, you need to:
1. make sure CMake version is correct
2. install dependencies from `open3d_catkin` 
3. install dependencies for `open3d_slam`

Clone the repository to:
``` bash
mkdir -p catkin_ws/src
cd catkin_ws/src
git clone git@github.com:leggedrobotics/open3d_slam_private.git
```

1. Make sure your CMake > 3.18
```bash
cmake --version
```
**If NOT** install the cmake from https://cmake.org/download download tar.
Unpack tar and
``` bash
cd cmake-<version>
./configure
make -j<num_of_processes>
sudo make install
```

2. Install the necessary dependencies from `open3d_catkin`:
```bash
cd open_3d_slam_rsl/open3d_catkin/
./install_deps.sh
```

3. Install libraries required from `open3d-slam`
```bash
sudo apt install libgoogle-glog-dev libglfw3 libglfw3-dev liblua5.2-dev
``` 

4. Install `libnabo` from Anybotics by cloning it to `catkin_ws/src`

```bash
cd catkin_ws/src
git clone git@github.com:ANYbotics/libnabo.git
```

And finally:

```bash
cd catkin_ws
catkin init
catkin config -DCMAKE_BUILD_TYPE=Release
catkin build open3d_slam_ros
```

## Use

First make sure you have correct topics for LiDAR point cloud and pose prior external odometry.

```bash
source devel/setup.sh
```
To perform **mapping and localization**, call:
```bash
roslaunch open3d_slam_ros development.launch
```

While playing the rosbag file:

```bash
rosbag play --clock --pause -s 0 -r 1.0 <your_great_bag>.bag
```

## License

The external repositories used in this work are under their respective licenses.
```
https://github.com/ANYbotics/libpointmatcher , https://github.com/ANYbotics/pointmatcher-ros and https://github.com/ANYbotics/libnabo
```
