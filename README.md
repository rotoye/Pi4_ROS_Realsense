# Pi4_ROS_Realsense
A repository to share an image with Raspberry Pi 4 with realsense drivers and MAVROS related files

Since there are no apt-get package yet for the ROS Melodic on raspberry pi 4. We will be compiling from source

## Compiling a ROS related package from source. MAVROS here as an example
Commands based on:
https://github.com/mavlink/mavros/blob/master/mavros/README.md#installation

Will add all required mavros-related packages to mavros.install without deleting other repos

```
rosinstall_generator --rosdistro melodic mavlink mavros mavros_extras --deps | tee -a mavros.rosinstall
wstool merge -t src /tmp/mavros.rosinstall
wstool update -t src -j4
sudo ./src/catkin/bin/catkin_make_isolated --install -DCMAKE_BUILD_TYPE=Release --install-space /opt/ros/melodic -j2
```
