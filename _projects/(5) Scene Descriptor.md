---
name: Integration of VLM with Robot
tools: [Python, VLM, OpenCV, ROS2, Ollama, MediaPipe, Unitree SDK, Llava-7b, Flask]
image: https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/5-vlmdescription.png?raw=true
description: This project integrates a Vision-Language Model (VLM) with the Unitree Go2 Edu robot to generate real-time scene descriptions based on its camera feed.
---


# **Real-Time Vision-Language Model Integration with Unitree Go2 Edu**
<br>

## Project Overview
<br>

This project enables the Unitree Go2 Edu quadruped robot to understand and describe its environment in real time using a Vision-Language Model (VLM). The system captures images from the robot’s front camera, processes them with Llava-7b, and generates a textual description of the scene. The results are displayed on a Flask-based web interface.

### Key Features:
<br>

- Live video streaming from the Unitree Go2 front camera.
- Integration of the Ollama framework to run Llava-7b for real-time scene understanding.
- Hand gesture-based robot control using MediaPipe (thumbs up/down to control robot standing posture).
- Flask web server to display the live camera feed and generated descriptions.

---

## How It Works
<br>

1. Capturing Real-Time Video:
   - The VideoClient API from Unitree SDK retrieves images from the robot’s front camera.
   - Images are processed in **OpenCV** and resized for efficient handling.

2. Scene Description Generation:
   - The captured image is sent to **Llava-7b** using **Ollama**.
   - The model generates a natural language description of the scene.

3. Hand Gesture Recognition for Robot Control:
   - MediaPipe Hands** detects thumb gestures in the camera feed.
   - If the thumbs up gesture is detected, the robot stands up.
   - If the thumbs down gesture is detected, the robot sits down.

4. Web Interface for Streaming and Description Display:**
   - A Flask server runs a webpage that streams the live video feed.
   - The scene description is dynamically updated on the webpage.

<br>


## System Architecture**
<br>

The project consists of three main components:

### 1️⃣ Video Processing Module
<br>

- Retrieves images using Unitree SDK’s VideoClient.
- Preprocesses frames using OpenCV.
- Runs hand gesture recognition using MediaPipe.

### 2️⃣ Vision-Language Model (VLM) Integration
<br>

- Sends images to Llava-7b via Ollama.
- Processes model-generated text responses and updates the description.

### 3️⃣ Web-Based Interface**
<br>

- Flask server hosts a video feed (`/video_feed`).
- The scene description is updated via a dedicated API endpoint (`/description`).
- Users can view the robot’s observations in real-time.

---

##  Demonstration
<br>

Below is a screenshot of the project in action, showing the robot’s real-time video feed alongside the generated description.

<br>
![VLM Integration with Unitree Go2 Edu](https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/5-vlmdescription.png?raw=true)





## **GitHub Repository**
<br>

The complete implementation is available at:  
🔗 [GitHub Repository](https://github.com/h-naderi/scene_descriptor_unitree/tree/main)
