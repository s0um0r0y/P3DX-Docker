# Usage Instructions

## Get started

**GHCR Authentication** 
  ```bash
  echo "<YOUR_GITHUB_PAT>" | docker login ghcr.io -u <YOUR_GITHUB_USERID> --password-stdin
  ```
##### Prerequisites
- VSCode
- Remote Development Extension by Microsoft (Inside VSCode)
  
##### Setup Process
- Create a folder for P3DX development
    ```bash 
    mkdir P3DX && cd P3DX
    # Clone the repo 
    git clone https://github.com/rtarun1/P3DX-Docker.git
    # Open VSCode 
    code .
    ```
- To enter the container
    - Open Command Pallete with `Ctrl+Shift+P`
    - Select **Dev Containers: Reopen in Container**

    - Use `Build WS` button to build workspace
  
    >Note: To access these buttons you may need to enable [VSCode Action Button Extension](https://marketplace.visualstudio.com/items?itemName=seunlanlege.action-buttons) through the Extensions Tab in VSCode, the extension should download automatically on container startup
  

## Start up the ROS Master Node

```roscore```

## Setup connection with the robot

**Make sure to source the workspace on each terminal.**

```source devel/setup.bash```

```sudo chmod +777 /dev/ttyUSB0```

```rosrun rosaria RosAria```

## Setting up the Camera

```roslaunch realsense2_camera rs_camera.launch align_depth:=true```

To get pointclouds from the RGBD images:

```roslaunch realsense2_camera rs_camera.launch align_depth:=true enable_pointcloud:=true```

## Setup the conversion of RGBD images to Laser Scans

```roslaunch depthimage_to_laserscan launchfile_sample.launch```

## Setup the navigation node

```roslaunch turtlebot3_navigation turtlebot3_navigation.launch```

## Setting up Parser Based Navigation

```rosrun turtlebot3_navigation talker```

```rosrun turtlebot3_navigation Voice_NLP```