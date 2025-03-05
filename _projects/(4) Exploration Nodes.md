---
name: Exploration Algorithm Comparison and Simulation
tools: [Python, Pygame, ROS2, Gazebo, Nav2, TurtleBot3 Simulation]
image: https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/4-frontier.gif?raw=true
description: Compare different exploration strategies in a simulation environment. 
---

# **Exploration Algorithm Comparison and Simulation**

## Project Overview
<br>

This project aimed to study autonomous exploration strategies by testing three different algorithms in a 2D grid simulation and later validating the best-performing one in a Gazebo simulation with TurtleBot3. This project had two following stages: 

<br>

1. Initial Testing in a 2D Simulation Environment:
   - Implemented three different exploration algorithms:
     - Complete Coverage Path Planning (CPP)
     - Next Best View (NBV)
     - Frontier-Based Exploration
   - Simulated exploration in a grid-based environment using Pygame.
   - Compared algorithms based on coverage efficiency, and speed.

<br>

2. Final Testing in a Gazebo Simulation:
   - Selected Frontier-Based Exploration due to its superior performance (40% better in computation and time required).
   - Integrated the algorithm into a ROS2 package.
   - Tested it in Gazebo with TurtleBot3, using Nav2 for navigation.


## 2D Exploration Testing**
<br>

In the first phase, the exploration methods were evaluated in a 50x50 grid-based environment with a virtual robot equipped with:
- A simulated sensor with a limited field-of-view (FOV).
- Obstacle detection to avoid unknown areas.
- Goal selection algorithms for different exploration strategies.

Each algorithm was tested independently:

#### 1️⃣ Complete Coverage Path Planning (CPP)
<br>
- Used a lawnmower (snake-like) pattern to cover the entire area.
- Ensured full coverage but was not efficient for unknown environments.

<center><img src="https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/4-cpp.gif?raw=true"/></center>
<br>

#### 2️⃣ Next Best View (NBV)
<br>

- Selected the next goal based on information gain.
- Prioritized moving towards areas that maximized newly discovered space.
- Performed better than CPP but still struggled in bigger spaces due to higher computational need.

<center><img src="https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/4-nbv.gif?raw=true"/></center>
<br>

#### 3️⃣ Frontier-Based Exploration
<br>

- Identified frontier cells (edges between known and unknown space).
- Moved towards the closest frontier to incrementally explore.
- Outperformed other approaches in terms of speed and adaptability.

<center><img src="https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/4-frontier.gif?raw=true"/></center>
<br>

### Gazebo Simulation with TurtleBot3

<br>

After determining Frontier-Based Exploration as the best approach, we:
1. Implemented the algorithm in ROS2 and integrated it with Nav2.
2. Ran the TurtleBot3 simulation in Gazebo, with separate terminals managing:
   - The TurtleBot3 simulation.
   - The Nav2 navigation stack.
   - The custom exploration node.
3. The robot autonomously explored the environment, selecting frontiers dynamically and avoiding obstacles.

<center><img src="https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/4-simulation.gif?raw=true"/></center>
<br>


## **GitHub Repository**
The complete implementation is available at:  
🔗 [GitHub Repository](https://github.com/h-naderi/exploration-algorithms)
