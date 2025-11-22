# TurtleBot3 ROS2 Autonomous Navigation

This repo excludes the YOLOv3 weights file (src/yolov3.weights, >200MB).
See README for instructions to download it from the official source before running object detection.

## How to Run

---

### 1. Build TurtleBot3 Gazebo workspace
```
cd ~/Sneh_project_adjustments/src/turtlebot3_ws
rm -rf build install log
colcon build --cmake-clean-cache
source install/setup.bash
```

### 2. Launch Gazebo with custom world

```
ros2 launch turtlebot3_gazebo turtlebot3_my_world.launch.py
```

### 3. Teleop control (New Terminal)

```
source ~/Sneh_project_adjustments/src/turtlebot3_ws/install/setup.bash
ros2 run turtlebot3_teleop teleop_keyboard
```

### 4. Object detection
In a New Terminal:

```
cd ~/Sneh_project_backup_copy/src/ros2_ws
rm -rf build install log
colcon build --packages-select object_detection --symlink-install
source install/setup.bash
ros2 launch object_detection object_detection.launch.py
```

### 5. SLAM with slam_toolbox

Start simulation (robot state publisher)
Then, In a New Terminal:
```
ros2 launch turtlebot3_bringup turtlebot3_state_publisher.launch.py use_sim_time:=True
```

Start SLAM (In a New Terminal)

```
ros2 launch slam_toolbox online_async_launch.py use_sim_time:=True
```


Inspect map topic (In a new Terminal)
```
ros2 topic echo /map
```


Visualize in RViz2 (In a New Terminal)
```
rviz2
```

### 6. A* path planning
Keep SLAM and Robot state publisher on then Run A* planner (In a New Terminal):

```
~/Sneh_project_done/install/astarplanner/bin/astar_planner
```

To visualize the planned path, open RViz2 and add the path planning topics/markers.

### 7. TF frames PDF

In a New Terminal Run:
```
ros2 run tf2_tools view_frames
```
