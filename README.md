# Autonomous Indoor Navigation Robot

An autonomous mobile robot simulation built using **ROS 2 Jazzy**, **Nav2**, and **SLAM Toolbox**.
The robot generates a map of an indoor environment using LiDAR and autonomously navigates to user-defined goals while avoiding obstacles.

---

## Features

* Autonomous navigation using **ROS 2 Navigation Stack (Nav2)**
* Real-time environment mapping with **SLAM Toolbox**
* Localization using **AMCL**
* Global and local path planning
* Obstacle avoidance using LiDAR
* Goal-based navigation through **RViz**
* Full simulation using **Gazebo**

---
## video link 
video link : https://www.youtube.com/watch?v=_uocrmAddO8

## System Architecture

LiDAR → SLAM Toolbox → Map Generation
Map → AMCL → Robot Localization
Localization → Nav2 Planner → Path Planning
Planner → Controller → Robot Movement

---

## Technologies Used

* **ROS 2 Jazzy**
* **Nav2 (Navigation2 Stack)**
* **SLAM Toolbox**
* **Gazebo Simulation**
* **RViz Visualization**
* **TurtleBot3**
* **LiDAR Sensor**

---

##  Project Structure

```
navigation_robot_ws
│
└── src
    └── autonomous_nav_robot
        ├── launch
        ├── maps
        │   ├── map.yaml
        │   └── map.pgm
        ├── config
        ├── worlds
        ├── package.xml
        └── setup.py
```

---

##  Installation

### 1. Install ROS 2 Jazzy

Follow the official ROS installation guide.

### 2. Install required packages

```bash
sudo apt update

sudo apt install ros-jazzy-navigation2
sudo apt install ros-jazzy-nav2-bringup
sudo apt install ros-jazzy-slam-toolbox
sudo apt install ros-jazzy-turtlebot3*
sudo apt install ros-jazzy-gazebo-ros-pkgs
```

---

## Map Creation (SLAM)

Launch Gazebo simulation:

```bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

Run SLAM toolbox:

```bash
ros2 launch slam_toolbox online_async_launch.py use_sim_time:=true
```

Control the robot:

```bash
ros2 run turtlebot3_teleop teleop_keyboard
```

Save the generated map:

```bash
ros2 run nav2_map_server map_saver_cli -f map
```

---

##  Autonomous Navigation

Launch navigation using the saved map:

```bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```



```bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=true
```


Open RViz:

```bash
rviz2
```

Steps in RViz:

1. Set **Fixed Frame → map**
2. Click **2D Pose Estimate** to initialize robot position
3. Click **2D Goal Pose** to send a navigation goal

The robot will autonomously navigate to the goal while avoiding obstacles.

---

##  Demonstration

The robot performs:

* Environment mapping using SLAM
* Localization within the saved map
* Path planning to a goal
* Autonomous obstacle-free navigation

---

##  Future Improvements

* Custom robot URDF model
* Custom Gazebo warehouse environment
* Real LiDAR hardware integration
* Multi-goal waypoint navigation
* Vision-based obstacle detection

---

## Author

**Bachu James**

Robotics Engineer | ROS Developer | Embedded Systems Engineer

---

## 
License

This project is released under the **MIT License**.
