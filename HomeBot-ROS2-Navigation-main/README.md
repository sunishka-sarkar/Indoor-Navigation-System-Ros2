```markdown
# Indoor Navigation System using ROS2

An autonomous indoor navigation system built on **ROS 2 Humble** that enables a mobile robot to map unknown environments, localize itself, and navigate to target positions while dynamically avoiding obstacles.

##  Overview
Traditional GPS fails in indoor settings due to signal interference. This project implements a robust alternative using **SLAM**, **AMCL**, and **Nav2** to provide essential capabilities for service robots, warehouse automation, and assistive robotics.

### Key Features
* **SLAM (Simultaneous Localization and Mapping):** Uses LiDAR and Odometry fusion to build 2D occupancy grid maps in real-time.
* **Robust Localization:** Employs Adaptive Monte Carlo Localization (AMCL) for precise positioning within known maps.
* **Dynamic Path Planning:** Combines global planners (A*/Dijkstra) with local planners (DWA) for optimal routing and reactive obstacle avoidance.
* **Simulation Ready:** Fully compatible with the **Gazebo** simulator for testing before hardware deployment.

##  Tech Stack
* **Framework:** ROS 2 Humble
* **Navigation:** Nav2 (Navigation2 Stack)
* **Algorithms:** SLAM (Gmapping/Cartographer), AMCL, DWA
* **Simulation & Tools:** Gazebo, RViz2
* **Languages:** Python, C++
* **Libraries:** `tf2`, `sensor_msgs`, `nav_msgs`, `geometry_msgs`

##  Repository Structure
```text
Indoor-Navigation-System-Ros2/
├── description/        # URDF and Xacro robot models
├── launch/             # ROS 2 launch files for system bringup
├── config/             # Navigation and SLAM parameter files
├── maps/               # Saved occupancy grid maps (.yaml, .pgm)
├── worlds/             # Gazebo simulation environment files
├── package.xml         # Package dependencies
└── CMakeLists.txt      # Build instructions
```

##  Installation & Setup

### Prerequisites
* Ubuntu 22.04 (Jammy Jellyfish)
* ROS 2 Humble Desktop Install
* Nav2 and Gazebo plugins:
    ```bash
    sudo apt install ros-humble-navigation2 ros-humble-nav2-bringup ros-humble-gazebo-ros-pkgs
    ```

### Build Instructions
1.  Create a workspace and clone the repository:
    ```bash
    mkdir -p ~/nav_ws/src
    cd ~/nav_ws/src
    git clone [https://github.com/sunishka-sarkar/Indoor-Navigation-System-Ros2.git](https://github.com/sunishka-sarkar/Indoor-Navigation-System-Ros2.git)
    ```
2.  Install dependencies and build:
    ```bash
    cd ~/nav_ws
    rosdep install --from-paths src --ignore-src -r -y
    colcon build --symlink-install
    source install/setup.bash
    ```

##  Usage

### 1. Mapping (SLAM)
To start the environment mapping process:
```bash
ros2 launch indoor_navigation_system_ros2 online_async_launch.py
```
Drive the robot using a teleop node to generate the map in RViz2.

### 2. Navigation
Once a map is saved, launch the navigation stack:
```bash
ros2 launch indoor_navigation_system_ros2 navigation_launch.py use_sim_time:=true map:=/path/to/map.yaml
```
Use the **"2D Goal Pose"** button in RViz2 to set a destination.

##  Outcomes
The system successfully achieves:
* Accurate 2D map generation of structured indoor environments.
* Real-time obstacle detection and path re-planning.
* Reliable localization despite sensor noise and odometry drift.

## 👥 Contributors
* **Sunishka Sarkar** -     PES2UG23CS628
* **T Dheeraj Sai Skand** - PES2UG23CS637
* **Tanishq Raj** -         PES2UG23CS642
* **Tanishq Singh Mehta** - PES2UG23CS643
```
