# Stereo camera esetimation

![StereoCamEstimation](https://github.com/user-attachments/assets/d180fc86-ba3b-4c24-a090-a356c2a66bda)

object detection 모델로 탐지한 물체를 삼각측량법으로 측정하는 코드입니다.

[내용 설명](https://drive.google.com/file/d/1NVr0YoYPKzwOAnC_OSKWWteWhLeWmdIq/view?usp=sharing)

# Prerequisites
- OS : Ubuntu-22.04
- Unity : 2021.3.* LTS
- Requirements
  - numpy==1.23.0
  - torch==2.3.0
  - torchaudio==2.3.0
  - torchvision==0.18.0
  - opencv-python==4.9.0.80
  - opencv-contrib-python==4.9.0.80
  - pandas
  - ultralytics

# Installation
## Install ROS2
- 참고: https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html
- sudo apt install software-properties-common
- sudo add-apt-repository universe
- sudo apt update && sudo apt install curl -y
- sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
- echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
- sudo apt update && sudo apt upgrade -y
- sudo apt install ros-humble-desktop -y
- sudo apt install ros-dev-tools -y
- echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc

## Install Gazebo
- sudo apt update && sudo apt upgrade -y
- sudo apt install -y git python3-pip
- sudo apt install ros-humble-xacro
- sudo apt install -y python3-colcon-common-extensions \
ros-humble-joint-state-publisher-gui \
ros-humble-gazebo-plugins \
ros-humble-joint-state-publisher \
ros-humble-gazebo-ros
- sudo apt install ros-humble-ros2-control \
ros-humble-ros2-controllers \
ros-humble-gazebo-ros2-control
- sudo apt install ros-humble-diagnostic-updater

## jetauto_description
- copy meshes to ~/.gazebo/models/jetauto_description/meshes/

# Getting Started
```
cd ros_ws
killall -9 gzserver robot_state_publisher; colcon build; source install/setup.bash; ros2 launch jetauto_control object_detection.launch.py
```

