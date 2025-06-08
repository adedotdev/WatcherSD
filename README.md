# WatcherSD

A simulation to test autonomous navigation capabilities for a Smart Wheelchair using turtlebotsim


## Prerequisites
- ROS2
- RViz
- Gazebo

## Installation & Build
1. Create a ROS2 workspace
```
   mkdir ~/ros2_ws
   cd ros2_ws
```

2. Clone the repository
```
   cd ~/turtlebot3_ws/src/
   git clone -b humble https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
   cd ~/turtlebot3_ws && colcon build --symlink-install
```
   
3. To create and build a new package in ROS2 (optional)
```
   ros2 pkg create --build-type ament_cmake --license Apache-2.0 <package_name>
   colcon build --packages-select <package_name>
```

## Setup & Launch
1. Launch default simulation world
```
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```
To load a different simulation environment (optional)
```
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo turtlebot3_house.launch.py
```

2. 

## License
Released under Apache-2.0
