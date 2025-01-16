# ROS2 Integration

This is the readme for the process of switch the locobots from the noetic distribtion to the ros2 galactic distribution. As of (01/16/25) the process of switching distributions has been semi-sucessful. Currently the issue are the create3 nodes not being launched when the control package starts.

## Possible Issues:

- 1. I fogot to do sudo apt update, upgrade and autoremove?
- 2. Maybe I need the **create3_ros_ws**?
- 3. There are nesseary configurations for a multi-robot setup. Therefore I will turn off other bases and try to run the robot from that. 

## Steps to reproduce:

### 1) Backup existing ros1 data set

```bash
mv ~/interbotix_ws ~/interbotix_ws_ros1_backup
mv ~/apriltag_ws ~/apriltag_ws_ros1_backup
mv ~/ros1_bridge_ws ~/ros1_bridge_ws_backup
mv ~/create3_ros1_ws ~/create3_ros1_ws_backup
mv ~/create3_ros2_ws ~/create3_ros2_ws_backup
```

### 2) Installing

```bash
sudo apt update
sudo apt -y upgrade
sudo apt -y autoremove
sudo apt install curl
curl 'https://raw.githubusercontent.com/Interbotix/interbotix_ros_rovers/main/interbotix_ros_xslocobots/install/amd64/xslocobot_amd64_install.sh' > xslocobot_amd64_install.sh
chmod +x xslocobot_amd64_install.sh
./xslocobot_amd64_install.sh -d galactic -b create3
```

### 3) Base 3 configurations

1. Follow Phases 1 and 3 in [iRobot's Create® 3 Setup Guide](https://edu.irobot.com/create3-setup). You should not need to follow Phase 2 since we will provide the latest stable firmware for the base.

2. Make sure the base3 is setup properly in the [Main Configuration](https://docs.trossenrobotics.com/interbotix_xslocobots_docs/getting_started/create3_configuration.html#main-configuration) section in the locobot documentation. Make sure to activate the locobot network and 

3. Also make sure the [Application Parameters](https://docs.trossenrobotics.com/interbotix_xslocobots_docs/getting_started/create3_configuration.html#application-ros-2-parameters-file) are set. 




