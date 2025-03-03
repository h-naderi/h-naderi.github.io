---
name: Hand Gesture Control of Quadrupped Robot
tools: [ROS2, Python, C++, Quadruped, Computer Vision, MediaPipe]
image: https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/1-hand-gesture-intro.gif?raw=true
description: Controling the Unitree Go2 robot via hand gestures.
---

# Hand Gesture-Controlled Unitree Go2 Robot

## **Description**
This project enables gesture-based control of the Unitree Go2 quadruped robot using a Python interface. The system leverages MediaPipe for real-time hand gesture recognition and OpenCV for image processing. The recognized gestures are used to command the robot to stand up or stand down, providing an intuitive and efficient way to interact with the robot.

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
    <iframe src="https://www.youtube.com/embed/hJjrWiqMabM" 
            frameborder="0" allowfullscreen
            style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
    </iframe>
</div>
<br>

## **Project Flowchart**
Below is the flowchart illustrating the project's workflow.

<center><img src="{{ site.url }}{{ site.baseurl }}/assets/1-hand-gesture-flowchart.png"/></center>

<br>

## **How It Works**
The system follows these steps:

1. The robot's built-in camera streams video.
2. The image stream is processed using OpenCV and MediaPipe.
3. MediaPipe detects hand landmarks and classifies gestures.
4. The detected gestures (thumbs up/down) are mapped to control commands.
5. The commands are sent to the Unitree Go2 robot through its SDK.
6. The robot responds by standing up or standing down.

<br>

## **Hand Gesture Recognition**
The system uses **MediaPipe** to detect and analyze hand gestures. Each frame from the robot’s front camera is processed in real-time to identify hand landmarks and classify gestures.
<br>
<br>
<div style="position: relative; padding-bottom: 56.25%; height:0; overflow: hidden;">
    <center><video src="{{ site.url }}{{ site.baseurl }}/assets/1-hand-gesture-front-camera.mp4" controls style="position: absolute; top:0; left:0; width: 100%; height: 100%;"></video></center>
</div>
<br>
<br>
The gesture recognition model specifically detects the position of the **thumb** to differentiate between two commands:

- **Thumbs Up** → The robot stands up.
- **Thumbs Down** → The robot sits down.

<br>

## **Real-Time Testing**
The following video demonstrates the system in action, where the robot responds to hand gestures in real time.
<br>
<br>

<div style="position: relative; padding-bottom: 56.25%; height:0; overflow: hidden;">
    <center><video src="{{ site.url }}{{ site.baseurl }}/assets/1-hand-gesture-3PersonView.mp4" controls style="position: absolute; top:0; left:0; width: 100%; height: 100%;"></video></center>
</div>
<br>
<br>

## **Code Overview**
The core functionality is implemented in Python, utilizing the `unitree_sdk2py` library to send movement commands to the Unitree Go2 robot. Below is a high-level breakdown of the code:

- **Video Stream Processing**  
  - Captures video frames from the robot’s built-in camera.
  - Converts frames into a format suitable for hand recognition.
  - Uses **MediaPipe** to detect hand landmarks.

- **Gesture Recognition**  
  - Detects the **thumb tip** position.
  - Determines whether the **thumb is up or down**.

- **Robot Control**  
  - Sends control commands via the **Unitree SDK** based on the detected gesture.

For a detailed look at the implementation, visit the GitHub repository:  
[**GitHub Repository**](https://github.com/h-naderi/hand_gesture_unitree/tree/master)

<br>

## **Future Improvements**
Some potential enhancements for this project include:
- Adding more hand gestures for extended functionality.
- Integrating object recognition alongside gesture control.
- Improving robustness in various lighting conditions.

This project demonstrates an intuitive way to control a quadruped robot using natural hand movements, making human-robot interaction more seamless and accessible.

## **Acknowledgment**
This project was inspired by the amazing work of **Ava Zahedi**, who developed a hand gesture-based control system for the Unitree Go1 robot. I want to express my gratitude for making the project publicly available, as it served as a valuable reference in building this system.

I highly encourage everyone to check out Ava's project here:  
[**Gesture-Based Quadruped Control by Ava Zahedi**](https://avazahedi.github.io/projects/04-hgr-go1)

