# TurtleBot3 ROS2 Autonomous Navigation

This repo excludes the YOLOv3 weights file (src/yolov3.weights, >200MB).
See README for instructions to download it from the official source before running object detection.

## How to Run

### 1. Build TurtleBot3 Gazebo workspace

cd ~/Sneh_project_adjustments/src/turtlebot3_ws
rm -rf build install log
colcon build --cmake-clean-cache
source install/setup.bash

text
