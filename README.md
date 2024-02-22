# Project Title

HSLAM (Hybrid Simultaneous Localization and Mapping) Project.

A containerized "ready-to-use" SLAM application that leverages both direct and indirect methods.

### Related Publications:
[HSLAM]Younes, G. (2021). A Unified Hybrid Formulation for Visual SLAM (Doctoral dissertation).
**[PDF] (https://scholarworks.aub.edu.lb/bitstream/handle/10938/22253/YounesGeorges_2021.pdf?sequence=5)**

Please cite the paper if used in an academic context.

## Table of Contents

- [Project Description](#project-description)
- [Installation](#installation)
- [Usage](#usage)
- [Features](#features)
- [Contributing](#contributing)
- [License](#license)

## Project Description

The FSLAM project is an implementation of a visual simultaneous localization and mapping algorithm. 
It utilizes the ROS (Robot Operating System) Noetic and is designed for Ubuntu 20.04.



## Installation

To use this Dockerfile and build the FSLAM project, follow these steps:

1. Clone the Repo.
2. Change the workspace name to catkin_ws.
3. Open a terminal and navigate to the Thirdparty directory.
```bash
    cd ~/catkin_ws/src/FSLAM/Thirdparty
```
4. Build Thirparty libraries using script(cmake).
```bash
    sudo chmod +x build.sh && ./build.sh
```
5. Navigate to the FSLAM directory.
```bash
    cd /catkin_ws/src/FSLAM
```
6. Build FSLAM.
```bash
    mkdir -p build && cd build && cmake .. -DCMAKE_BUILD_TYPE=RelwithDebInfo && make -j 10
```
5. Navigate to the workspace directory.
```bash
    cd /catkin_ws
```
6. Build the workspace.
```bash
catkin init \
    && catkin config \
    -DCMAKE_BUILD_TYPE=Release \
    --extend /opt/ros/$ROS_DISTRO \
    && catkin build fslam_ros
```

## Usage

To run the FSLAM run:
1. In the first terminal run the following command to open a camera stream through ROS and publish the camera's images unto a ROS topic:
``` bash
    roslaunch usb_cam usb_cam-test.launch
```

2. In the second terminal, execute this command to run the FSLAM algorithm on the image stream.
``` bash
    rosrun fslam_ros fslam_live image:=/usb_cam/image_raw calib=/catkin_ws/src/res/camera.txt gamma=/catkin_ws/src/res/pcalib.txt vignette=/catkin_ws/src/res/vignette.png mode=0
```
Start moving the camera/computer around and perform SLAM.

## Features

- Utilizes the FSLAM algorithm for simultaneous localization and mapping.
- Integrates with ROS Noetic and utilizes various ROS functionalities.
- Supports camera integration, including Realsense cameras.
- Provides a wrapper for ROS integration and additional functionality.

## Contributing

Contributions to the FSLAM project are welcome. If you would like to contribute, please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make the necessary changes and commit them.
4. Push your changes to your forked repository.
5. Submit a pull request detailing the changes you have made.

## License
This project is licensed under the [MIT License](LICENSE).
