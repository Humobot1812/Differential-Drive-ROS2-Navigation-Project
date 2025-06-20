# Differential-Drive-ROS2-Navigation-Project
This repository demonstrates a complete SLAM, localization, and navigation pipeline for a four-wheeled differential drive robot using ROS 2 Humble, Gazebo (Harmonic), SLAM Toolbox, AMCL, and Nav2.



## 🚀 Features
- **SLAM Mapping:** Creates a 2D occupancy map of the environment using SLAM Toolbox.
- **Localization:** Uses AMCL (Adaptive Monte Carlo Localization) to localize the robot within the generated map.
- **Navigation:** Employs Nav2 (Navigation 2) stack for path planning and obstacle avoidance.
- **Simulation:** Runs in Gazebo (Harmonic) with a differential drive robot model.
- **Visualization:** Supports RViz2 for real-time map and path visualization.
- **Image Monitoring:** Uses rqt_image_view to display camera feed from a gimbal-mounted camera.
- **Frame Inspection:** Includes tf2_tools view_frames for inspecting TF transform trees.


## 🔧 Prerequisites
- Ubuntu 22.04 LTS
- ROS 2 Humble Hawksbill
- Gazebo 11 (Harmonic)
- RViz2
- rqt_image_view
- tf2_tools
- A gimbal-mounted camera plugin for Gazebo
- slam_toolbox, nav2_bringup, nav2_amcl, gazebo_ros, packages installed


## 📦 Installation
1. Build the workspace and Clone the repository
- cd
- mkdir Humobotss_ws
- cd Humobotss_ws
- mkdir src
- cd ../
- colcon build
- cd src
- git clone https://github.com/Humobot1812/Differential-Drive-ROS2-Navigation-Project.git.

## Structure of workspace
- └── src/
-   ├── Armo_bringup/
-   │   ├── launch/
-   │   │   │   ├── Armo_display.launch.xml
-   │   │   │   ├── Armo_display_map.launch.xml
-   │   │   │   └── Armo_display_navigation.launch.xml
-   │   ├── CMakeLists.txt
-   │   └── package.xml
-   └── Armo_description/
-   │   |   ├── urdf/
-   │   │   │   ├── base_mobile.xacro
-   │   │   │   ├── base_mobile_2.xacro
-   │   │   │   ├── base_mobile_3.xacro
-   │   │   │   ├── common_properties.xacro
-   │   │   │   ├── robot_base.urdf.xacro
-   │   │   │   └── robot_gazebo.xacro
-   │   ├── config/
-   │   │   │   ├── ekf.yaml
-   │   │   │   ├── gazebo_bridge.yaml
-   │   │   │   ├── param_nav2.yaml
-   │   │   │   └── Slam_param.yaml
-   │   ├── maps/
-   │   │   │   ├── Maze.pgm
-   │   │   │   └── Maze.yaml
-   │   ├── rviz/
-   │   │   │   ├── rviz_config.rviz
-   │   │   │   └── rviz_config_nav2.rviz
-   │   ├── world/
-   │   │   │   ├── Maze.sdf
-   │   │   │   └── Maze.world
-   │   ├── CMakeLists.txt
-   │   └── package.xml



