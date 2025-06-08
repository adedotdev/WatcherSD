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


## Setup & Launch (multiple terminals required)
1. Launch default simulation world (first terminal)
```
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```
- To load a different simulation environment (optional)
```
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo turtlebot3_house.launch.py
```

2. Run SLAM node to build the map (second terminal)
```
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True
```

3. Run teleoperation node and view in RViz (third terminal)
```
export TURTLEBOT3_MODEL=burger
ros2 run turtlebot3_teleop teleop_keyboard
```
- Use given keys to move around. You should see output similar to:
```
Control Your TurtleBot3!
 ---------------------------
 Moving around:
        w
   a    s    d
        x

 w/x : increase/decrease linear velocity
 a/d : increase/decrease angular velocity
 space key, s : force stop

 CTRL-C to quit
```

4. Save SLAM map (fourth terminal)
```
ros2 run nav2_map_server map_saver_cli -f ~/map
```

5. Ensure map is saved by checking downloads or root directory (~/map.pgm)
6. Clear or close all terminals


## Usage (multiple terminals required)
1. Launch default simulation world (first terminal)
```
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```
- To load a different simulation environment (optional)
```
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo turtlebot3_house.launch.py
```

2. Run Navigation node (second terminal)
```
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True map:=$HOME/map.yaml
```

3. Estimate initial pose by clicking `2D Pose Estimate` button in RViz, then click-hold on map where robot is located, and finally drag green arrow toward the direction where the robot is facing. Repeat until the LDS sensor data is overlayed on the saved map

4. Run teleoperation node to precisely locate the robot on the map
```
ros2 run turtlebot3_teleop teleop_keyboard
```

5. Move robot back and forth to collect surrounding environment information and estimate location of Turtlebot on the map.

6. Terminate teleoperation node with `Ctrl + C`

7. Click `Navigation Goal` button in RViz, then click on the map to set the destination of the robot and drag the green arrow towards the direction the robot will be facing.


## License
Released under Apache-2.0
