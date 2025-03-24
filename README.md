# Human Pose Demonstration/Following for Baxter Robot 

This project achieves how to demonstrate a Baxter robot (enable the Baxter robot to follow human actions) using human pose estimation.

## Environment
- **System**: Ubuntu 18.04
- **Sensor**: Kinect v2
- **Robot**: Baxter pkg

## Installation Steps

### 1. Kinect v2 Installation
Follow the instructions provided in the link below to set up Kinect v2:
- [Kinect v2 Installation Guide](https://blog.csdn.net/lwq123free/article/details/90755822)

### 2. kinect2_tracker Installation
Install the `kinect2_tracker` package for human pose tracking:
- [kinect2_tracker Installation Guide](https://blog.csdn.net/nkc555/article/details/123350491)

**Note**: Use `NiTE-Linux-x64-2.2` instead of `NiTE-Linux-x64-2.0`.

### 3. Baxter Robot Setup
Set up the Baxter robot by following the instructions below:
- [Baxter Installation Guide](https://blog.csdn.net/m0_51060098/article/details/133689202)
- Source Code: [Rethink Robotics Baxter GitHub Repository](https://github.com/RethinkRobotics/baxter)

### 4. Kinect-Based Arm Tracking
Clone and set up the `kinect_based_arm_tracking` package:
- Source Code: [kinect_based_arm_tracking GitHub Repository](https://github.com/birlrobotics/birl_baxter_demos/tree/master/kinect_based_arm_tracking)

## Details of the code
check the README.md in each sub folder in src/ for details

## Running the Demo

To run the demo, open multiple terminals and execute the following commands:

### Terminal 1: Start Baxter Robot
```bash
./baxter.sh
rosrun baxter_tools enable_robot.py -e # enable robot at the start
```

### Terminal 2: Launch Kinect2 Tracker
```
roslaunch kinect2_tracker tracker.launch
```
Note: It may take time to model the person. You may need to retry this step multiple times until the "tf" of the person is successfully published.

### Terminal 3: Publish Human Pose Data
```
cd ~/ros_ws/src/kinect_based_arm_tracking/scripts
python tf_listen_v8_puber.py
```

### Terminal 4: Control Baxter Robot
```
cd  ~/ros_ws/src/kinect_based_arm_tracking/scripts
python tf_listen_v8_controller.py
``` 

## References
https://blog.csdn.net/lwq123free/article/details/96335957


