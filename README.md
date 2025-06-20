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
-   │   │   │   ├── gazebo_bridge_2.yaml
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

# For running for just visualising in gazebo and rviz:
- cd Humobotss_ws
- sourec /opt/ros/humble/setup.bash
- ros2 launch Armo_bringup Armo_display.launch.xml

# For Mapping and Localization :
- cd Humobotss_ws
- sourec /opt/ros/humble/setup.bash
- ros2 launch Armo_bringup Armo_display_map.launch.xml                                   --> in terminal 1
- ros2 run teleop_twist_keyboard teleop_twist_keyboard                                   --> in terminal 2
- ------>>>>
- After the map is ready give below command to save the map:
- ------>>>>>
- ros2 run nav2_map_server map_saver_cli -f src/Armo_description/maps/New_map            --> in terminal 3

# To view camera feed in rqt and move the camera joint :
- ros2 run rqt_image_view rqt_image_view                                                 --> in terminal 4
- ros2 topic pub --once  /joint0/cmd_pos std_msgs/msg/Float64 "data: <value>"            --> in terminal 5

- You can give <value> as any number between -1.57 to 1.57 according to angle of camera you want as 1.57 = 90 degree and -1.57 = -90 degree


# For Navigation :
- cd Humobotss_ws
- sourec /opt/ros/humble/setup.bash
- ros2 launch Armo_bringup Armo_display_navigation.launch.xml                             --> in terminal 1

# For transform tree :
- ros2 run tf2_tools view_frames

# Feel free to fork this repo and do your own experiment with this !!!!!!

## 📜 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.







