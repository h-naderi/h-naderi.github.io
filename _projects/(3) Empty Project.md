---
name: Autonomous Navigation and Exploration
tools: [Nav2, ROS2, C++, Frontier Exploration, Python, SLAM]
image: https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/3-nav-intro.gif?raw=true
description: Enabling Autonomous Navigation and Exploration on Unitree-Go2 Robot
---

# Autonomous Navigation and Exploration on Unitree-Go2 

## Introduction

Simultaneous Localization and Mapping (SLAM) is a foundational step in robot development, enabling robots to understand their position in an unknown environment while simultaneously building a map of that environment. This capability is essential for developing more complex robotic behaviors and applications.

This project focused on implementing SLAM on Unitree Go2 robots using ROS2 and the RTAB-Map package. We successfully activated SLAM in two different configurations:
1. Using Lidar data only
2. Using a fusion of Lidar and RGB-Camera data 