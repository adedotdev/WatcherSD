# WatcherSD

A simulation to test autonomous navigation capabilities using turtlebot for a Smart Wheelchair


## Prerequisites
- ROS2
- RViz
- Gazebo

## Installation and Build
1. Clone the repository
   `git clone`
   
3. Create a ROS2 workspace

   `mkdir ros2_ws`
   
5. Create a new package in ROS2

   `ros2 pkg create --build-type ament_cmake --license Apache-2.0 <package_name>`
   
7. Build and verify success

   `colcon build --packages-select <package_name>`

## Launch
