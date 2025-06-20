Here’s a polished, GitHub‑ready README for your Differential‑Drive‑ROS2‑Navigation‑Project:

---

# Differential‑Drive‑ROS2‑Navigation‑Project

A complete SLAM, localization, and navigation pipeline for a four‑wheeled differential‑drive robot using ROS 2 Humble, Gazebo (Harmonic), SLAM Toolbox, AMCL, and Nav2.

---

## 🚀 Features

* **SLAM Mapping**
  Build a 2D occupancy map of your environment with SLAM Toolbox.
* **Localization**
  Track the robot’s pose on the map using AMCL (Adaptive Monte Carlo Localization).
* **Autonomous Navigation**
  Plan and follow paths with obstacle avoidance via the Nav2 stack.
* **Simulation**
  Run everything in Gazebo (Harmonic) on a differential‑drive robot model.
* **Visualization**
  View real‑time maps, paths, and TF frames in RViz 2.
* **Camera Monitoring**
  Stream and control a gimbal‑mounted camera with `rqt_image_view`.
* **TF Inspection**
  Inspect transform trees using `tf2_tools view_frames`.

---

## 🎯 Prerequisites

* **OS:** Ubuntu 22.04 LTS
* **ROS 2 Distribution:** Humble Hawksbill
* **Gazebo:** 11 (Harmonic)
* **Tools:**

  * RViz 2
  * rqt\_image\_view
  * tf2\_tools
* **ROS 2 Packages:**

  * `slam_toolbox`
  * `nav2_bringup`
  * `nav2_amcl`
  * `gazebo_ros`
  * `teleop_twist_keyboard`

---

## 🏗️ Repository Structure

```
Differential-Drive-ROS2-Navigation-Project/
├── Armo_bringup/
│   ├── launch/
│   │   ├── Armo_display.launch.xml
│   │   ├── Armo_display_map.launch.xml
│   │   └── Armo_display_navigation.launch.xml
│   ├── CMakeLists.txt
│   └── package.xml
└── Armo_description/
    ├── urdf/
    │   ├── base_mobile.xacro
    │   ├── base_mobile_2.xacro
    │   ├── base_mobile_3.xacro
    │   ├── common_properties.xacro
    │   ├── robot_base.urdf.xacro
    │   └── robot_gazebo.xacro
    ├── config/
    │   ├── ekf.yaml
    │   ├── gazebo_bridge.yaml
    │   ├── gazebo_bridge_2.yaml
    │   ├── param_nav2.yaml
    │   └── Slam_param.yaml
    ├── maps/
    │   ├── Maze.pgm
    │   └── Maze.yaml
    ├── rviz/
    │   ├── rviz_config.rviz
    │   └── rviz_config_nav2.rviz
    ├── world/
    │   ├── Maze.sdf
    │   └── Maze.world
    ├── CMakeLists.txt
    └── package.xml
```

---

## ⚙️ Installation & Build

1. **Clone & Build**

   ```bash
   mkdir -p ~/Humobotss_ws/src
   cd ~/Humobotss_ws/src
   git clone https://github.com/Humobot1812/Differential-Drive-ROS2-Navigation-Project.git
   cd ~/Humobotss_ws
   colcon build
   ```

2. **Source ROS 2**

   ```bash
   source /opt/ros/humble/setup.bash
   source ~/Humobotss_ws/install/setup.bash
   ```

---

## 🛰️ Usage

### 1. Visualize in Gazebo & RViz

```bash
ros2 launch Armo_bringup Armo_display.launch.xml
```

### 2. Mapping & Localization

* **Start mapping**

  ```bash
  ros2 launch Armo_bringup Armo_display_map.launch.xml
  ```
* **Drive the robot**

  ```bash
  ros2 run teleop_twist_keyboard teleop_twist_keyboard
  ```
* **Save your map**

  ```bash
  ros2 run nav2_map_server map_saver_cli -f src/Armo_description/maps/New_map
  ```

### 3. Camera Feed & Gimbal Control

* **View camera stream**

  ```bash
  ros2 run rqt_image_view rqt_image_view
  ```
* **Adjust camera angle**

  ```bash
  ros2 topic pub --once /joint0/cmd_pos std_msgs/msg/Float64 "data: <angle>"
  ```

  Replace `<angle>` between `-1.57` (−90°) and `1.57` (+90°).

### 4. Autonomous Navigation

* **Use a custom map**

  1. Place your `*.yaml` and `*.pgm` files in `Armo_description/maps/`.
  2. Edit line 30 of
     `Armo_bringup/launch/Armo_display_navigation.launch.xml`:

     ```xml
     <arg name="map" value="$(find-pkg-share Armo_description)/maps/YourMap.yaml"/>
     ```
  3. Rebuild:

     ```bash
     colcon build --packages-select Armo_description Armo_bringup --symlink-install
     source install/setup.bash
     ```
* **Launch navigation**

  ```bash
  ros2 launch Armo_bringup Armo_display_navigation.launch.xml
  ```

### 5. TF Transform Tree

```bash
ros2 run tf2_tools view_frames
```

---

## 🤝 Contributing

Feel free to fork, file issues, or submit pull requests. Happy experimenting!

---

## 📜 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
