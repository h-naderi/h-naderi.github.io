---
name: SLAM for Unitree Go2 Robot
tools: [SLAM, ROS2, Sensor Fusion, RGB Depth Camera, 3D Point Data]
image: https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/2-slam-intro.gif?raw=true
description: Enabling SLAM on Unitree Go2 in two ways, with Lidar only, with infusion of Lidar and RGB Camera
---

# SLAM Implementation on Unitree Go2 Robot

## **Overview**

This project focused on implementing SLAM on Unitree Go2 robots using ROS2 and the RTAB-Map package. It was a foundational step as it allows for developing more complex robotic applications. SLAM is successfully activated in two different configurations:
1. Using Lidar data only
2. Using a fusion of Lidar and RGB-Camera.
The video below shows the successful implementation of the project.

<br>
<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
    <iframe src="https://www.youtube.com/embed/Hqmdpe81U_w" 
            frameborder="0" allowfullscreen
            style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
    </iframe>
</div>
<br>

## **Hardware Configuration**

The robot platform used for this project consists of:
- **Unitree Go2 Edu** equipped with an NVIDIA Jetson Nano
- **RoboSense RS-Helios-32** Lidar sensor for 3D point cloud generation
- **Intel RealSense D435i** RGB-D camera for visual data

<br>
The image below shows the robot and its attachments.

<center><img src="{{ site.url }}{{ site.baseurl }}/assets/2-robot-arch.png"/></center>
<br>

## **Software Environment**

SLAM implementation was tested and verified on:
- ROS2 Foxy
- Ubuntu 20.04 LTS

## **Implementation Process**

<br>

### 1. Activating Lidar Data

The first step involved integrating the Lidar sensor with ROS2. We utilized the RoboSense Lidar SDK from the [official GitHub repository](https://github.com/RoboSense-LiDAR/rslidar_sdk) and installed it according to the instructions provided.

After successful implementation, we could visualize the 3D point cloud data in RViz:

The image below shows the 3D data publishing in rslidar topic:

<center><img src="{{ site.url }}{{ site.baseurl }}/assets/2-point-cloud.png"/></center>
<br>

For future integration steps, it's important to note the frame_id and topics used by the SDK to publish 3D data:

```yaml
ros:
  ros_frame_id: base_laser                     # Frame id of packet message and point cloud message
  ros_recv_packet_topic: /rslidar_packets      # Topic used to receive lidar packets from ROS
  ros_send_packet_topic: /rslidar_packets      # Topic used to send lidar packets through ROS
  ros_send_point_cloud_topic: /rslidar_points  # Topic used to send point cloud through ROS
  ```
<br>

### 2. RTAB-Map Installation and Configuration
RTAB-Map is a graph-based SLAM approach that uses visual features for loop closure detection. We installed RTAB-Map on ROS2 following the [official installation guide](https://github.com/introlab/rtabmap/wiki/Installation).

For those who want to learn more about **RTAB-Map**, the [project's website](https://introlab.github.io/rtabmap/) provides comprehensive documentation. To understand the available parameters and optimize RTAB-Map usage, the [Parameters.h](https://github.com/introlab/rtabmap/blob/master/corelib/include/rtabmap/core/Parameters.h) file is an excellent resource.

Using the topics and frames configured in the LiDAR SDK, we created a launch file to implement RTAB-Map in two modes:

- **Localization Mode (`localize_only=true`)**:  
  - In this mode, the robot uses an already created map and does not update it with new sensor data.  
  - The `Mem/IncrementalMemory` parameter is set to false to prevent map updates.

- **Mapping Mode (`localize_only=false`)**:  
  - In this mode, the robot builds a new map each time the node is launched.  
  - The `-d` parameter can be used to reset any existing map, and the `Mem/IncrementalMemory` parameter is set to allow incremental map updates.

<br>

The launch file implements several important nodes:

- **`icp_odometry`**  
  - Uses the Iterative Closest Point (ICP) algorithm** to estimate the robot's movement based on point cloud data.  
  - It subscribes to the LiDAR point cloud and publishes odometry information.

- **`rtabmap`**  
  - The main SLAM node that handles mapping and localization based on sensor data.

- **`rtabmap_viz`**  
  - Provides visualization of the SLAM process, including:
    - The generated map
    - Robot trajectory
    - Feature matches

- `static_transform_publisher` 
  - Establishes the transformation between the base_link (robot base) and base_laser (LiDAR sensor).  
  - The `-0.2` value in the z-axis accounts for the height difference between the robot’s base and the mounted LiDAR sensor.

<br>
The video below shows the succesful implementation of this launch file in the mapping mode: 

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
    <iframe src="https://www.youtube.com/embed/3Y3A4aZpkHY" 
            frameborder="0" allowfullscreen
            style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
    </iframe>
</div>
<br>


---

### 3. SLAM with LiDAR and RGB-Camera Fusion
To improve mapping accuracy and enable automatic loop closure detection, we implemented a sensor fusion approach that combines LiDAR and RGB-D camera data.

- The RTAB-Map node is configured to subscribe to both RGB and depth images:
  ```yaml
  subscribe_depth: True
  subscribe_rgb: True
  ```

- Camera topics are remapped to the actual topics published by the Intel RealSense camera.
- IMU data is incorporated for improved odometry estimation.
- The `-d` argument is used to reset the map database when starting a new mapping session.



<br>
Note: the video in the overview section, is after running this launch file in mapping mode in the lab environment.
<br>




## **Future Work**
This project lays the groundwork for several future developments:
This project publishes odomentry data on `odom` topic, and also updates the `map`. These steps are essential for the next step in implementing autonomous navigation using Nav2, enabling the robot to navigate to specified goals.


<br>

## **Code Repository**
The complete code for this project is available in [**GitHub Repository**](https://github.com/h-naderi/unitree-go2-slam-nav2-demo)

<br>

## **Acknowledgements**
This work was inspired by  projects of [Nick Morales](https://ngmor.github.io) and [Roy Rahul](https://roy2909.github.io/). Their publicly available projects and supports have been invaluable to the development of this project.
