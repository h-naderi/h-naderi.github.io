---
name: Autonomous Navigation and Exploration
tools: [Nav2, ROS2, C++, Frontier Exploration, Python, SLAM]
image: https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/3-nav-intro.gif?raw=true
description: Enabling Autonomous Navigation and Exploration on Unitree-Go2 Robot
---

# Autonomous Navigation and Obstacle Avoidance on Unitree Go2

## **Project Overview**
This project enabled autonomous navigation and obstacle avoidance on the Unitree Go2 Edu robot using the Nav2 Stack and custom control nodes. The system allows the robot to explore unknown environments, dynamically avoid obstacles, and navigate to user-defined goals.

<br>
<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
    <iframe src="https://www.youtube.com/embed/-A6jT7Qenas" 
            frameborder="0" allowfullscreen
            style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
    </iframe>
</div>
<br>

## **How It Works**
<br>

After successfully implementing SLAM ([see SLAM project page](https://h-naderi.github.io/projects/2-slam)), we integrated the **Nav2 Stack**, which enables autonomous navigation, and obstacle avoidance on the robot. Nav2 subscribes to the `/odom` and `/map` topics, and send the velocity command to a custom control node. This node translates the commands into a format compatible with the Unitree SDK for movement execution. Additionally, a custom exploration node was developed to enable autonomous exploration.
<br>
The diagram below shows the building blocks of our system.
### **Project Architecture**
<center><img src="{{ site.url }}{{ site.baseurl }}/assets/3-diagram.png"/></center>
<br>
Note: steps 1 and 2 are fully explained in the SLAM project page [see here] (https://h-naderi.github.io/projects/2-slam), this page explains the next steps from 3 to 5. 
<br>

## **Hardware Configuration**
<br>

- **Unitree Go2 Edu** with Nvidia Jetson Nano
- **Robosense RS-Helios-32 LiDAR**
- **Intel RealSense D345i RGB-D Camera**

<br>

<br>
The image below shows the robot and its attachments.

<center><img src="{{ site.url }}{{ site.baseurl }}/assets/2-robot-arch.png"/></center>
<br>

## **Software Requirement**

<br>
- **ROS2 Foxy**
- **Ubuntu 20.04**
- **Unitree ROS2 SDK** (Installation guide: [Unitree ROS2 SDK](https://github.com/unitreerobotics/unitree_ros2))
<br>

## **Nav2 Integration**
<br>

In the previous project ([SLAM project page](https://h-naderi.github.io/projects/2-slam)), the **`/odom`** and **`/map`** topics were published by RTAB-Map. Nav2 subscribes to these topics to:
- Generate navigation paths using its global and local planners.
- Avoid obstacles dynamically based on the costmaps.
- Send velocity commands (`/cmd_vel`) for movement.

Find the code for launch file, and configurations in the project Github Repository [click here] (https://github.com/h-naderi/unitree-go2-slam-nav2)
<br>

Once Nav2 is successfully integrated, it publishes velocity commands on the `/cmd_vel` topic. The lifecycle manager in Nav2 initializes key navigation components such as:
- Global and local planners
- Path following behavior tree
- Obstacle avoidance and costmap servers
- Waypoint follower for sequential goal tracking
<br>

Nav2’s configuration file was modified to work with Unitree Go2, specifically adjusting:
- Localization parameters to adapt AMCL for the robot.
- Navigation behavior for smooth path planning.
- Control settings for better speed and stability.
- Global and local costmaps for obstacle avoidance.

These modifications ensured that the robot effectively localized itself, planned efficient routes, and dynamically responded to environmental changes.
<br>


## **Custom Control Node**
The custom control node plays a crucial role in translating Nav2’s velocity commands (`/cmd_vel`) into commands that the **Unitree SDK** can interpret. This ensures smooth and accurate movement execution.

The control node performs the following tasks:
- Subscribes to `/cmd_vel` topic to receive movement commands.
- Converts velocity commands into Unitree SDK-compatible instructions.
- Handles timeout conditions to stop the robot when no new commands are received.
- Supports custom actions such as standing up, laying down, and dancing using Unitree’s API.

Find the code for the node in the project Github Repository [click here] (https://github.com/h-naderi/unitree-go2-slam-nav2)
<br>


With this setup, the robot successfully Navigates through an already mapped environment. See the video below: 


Note: the video in the overview shows the robot after this stage.


## **Dynamic Obstacle Avoidance**

<br>

In dynamic environments, the robot continuously updates its costmaps and navigation goals, adjusting its path to safely maneuver around obstacles. See the video below:

<br>
<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
    <iframe src="https://www.youtube.com/embed/uvrxpd_esPg" 
            frameborder="0" allowfullscreen
            style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
    </iframe>
</div>
<br>


## **Exploration Node**

<br>

To enable autonomous exploration, a frontier-based exploration is utilized for this project. This node identifies unmapped areas (frontiers), selects the best frontier based on distance and exploration efficiency, and publishes a goal pose to Nav2 for autonomous movement.

To improve standard frontier-based exploration, we added following adjustment to frontier based system:
- Farthest-frontier selection to encourage loop closure and full coverage.
- Intermediate goal planning to avoid small, inefficient movements.
- Dynamic frontier filtering to ensure valid exploration targets.

Find the code for the node in the project Github Repository [click here] (https://github.com/h-naderi/unitree-go2-slam-nav2)
<br>

In another project, we went through different exploration nodes and study the behavior of them in a game-based environment in python. Take a look at this. a detailed breakdown of frontier exploration, see the [Exploration Project Page](https://h-naderi.github.io/projects/4-exploration-nodes).

## **GitHub Repository**
The full project code, configurations are available at:  
🔗 [GitHub Repository](https://github.com/h-naderi/unitree-go2-slam-nav2)


## **Acknowledgments**
This project was inspired by the work of Nick Morales ([Website](https://ngmor.github.io)) and Roy Rahul ([Project Page](https://roy2909.github.io/Exploration/#autonomous-exploration-and-mapping)). Thanks to them for droping their code and knowledge online. This project wouldn't exist without their awesome work.
