---
layout: page
title: About
permalink: /about/
weight: 3
---

# About Me


<br>

Hi, I am **Hossein** :wave:

<br>

<p align="center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/2-robot-arch.png" alt="Robot Architecture" width="60%">
</p>

<br>

I am a PhD Candidate and at the same time a CS master student at **Virginia Tech** and a passionate researcher in **Robotics and AI**. My research focuses on enhancing robot autonomy in unstructured environments, especially construction jobsites, through AI-driven solutions. 

My ultimate goal? Bridging the gap between human-level thinking, dexterity, and adaptability in robotics, enabling robots to take on dangerous tasks in real-world construction environments. To achieve this, I explore foundation models, particularly: Vision-Language Models (VLMs), Large Language Models (LLMs), and Multi-AI Agent Systems.

### **🚀 Skills & Expertise**
Throughout my research and development journey, I have honed my skills in:
- 🖥 Programming: C++, Python, Java  
- 🤖 Robotics Frameworks: ROS2/ROS, Gazebo, MoveIt  
- 🧠 AI & Machine Learning: TensorFlow, OpenCV, PyTorch, Transformers  
- 📡 Foundation Models: Vision-Language Models, Large Language Models, CrewAI, AutoGen  
- 🛠 Development Tools: Linux, Git  

<br>

I am always open to discussions, brainstorming sessions, and collaboration opportunities! If you share my enthusiasm for robotics, AI, or automation, let’s connect. 

<p align="center">
  📧 [Email](mailto:hnaderi@vt.edu) &nbsp; | &nbsp; 🔗 [LinkedIn](https://www.linkedin.com/in/h-naderi) &nbsp; | &nbsp; 💻 [GitHub](https://github.com/h-naderi)
</p>

<br>

### 📜 My CV
🔗 [Download My CV](#) *(Replace with actual link)*

<br>

### ** Beyond Research
When I’m not working with robots, you’ll probably find me:
- 🎨 **Painting**
- 🎬 **Watching movies**
- 🎒 **Going on backpacking trips**  

Let's push the boundaries of robotics together! 🤖✨

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pixel Robot</title>
    <style>
        body {
            background-color: black;
            color: #33ff33;
            font-family: monospace;
            text-align: center;
            font-size: 14px;
        }
        .terminal {
            display: inline-block;
            border: 2px solid #33ff33;
            padding: 10px;
            width: 300px;
            height: 200px;
            overflow: hidden;
            margin-top: 20px;
        }
        .blinking {
            animation: blink 1s infinite;
        }
        @keyframes blink {
            50% { opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="terminal" id="robotTerminal">
        <pre id="robotAscii">
  [ ]     
 (o.o)   < Hi! 
 <( )> 
  | |  
        </pre>
    </div>
    <script>
        const frames = [
            `  [ ]     
 (o.o)   < Hi! 
 <( )>  
  | |  `,
            `  [ ]     
 (O.O)   < Hi! 
 <( )>  
  | |  `,
            `  [ ]     
 (o.o)   < Hi! 
 <( )>  
  | |  `,
        ];
        
        let index = 0;
        function animateRobot() {
            document.getElementById("robotAscii").innerText = frames[index];
            index = (index + 1) % frames.length;
            setTimeout(animateRobot, 500);
        }
        animateRobot();
    </script>
</body>
</html>
