---

name: Adaptable Task Planning for Autonomous Robots
tools: [Python, CrewAI, MiniCPM-7B, Llama3-8B, ROS2, Quadruped Robot, Ollama]
image: https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/5-vlmdescription.png?raw=true
description: A study exploring multi-agent AI for zero-shot robot task planning in construction, enhancing adaptability and generalizability across dynamic tasks.

---

# **Zero-shot Adaptable Task Planning for Autonomous Construction Robots**
<br>

> 🚧 **Note:** This project is currently under review in a peer-reviewed academic journal. Stay tuned for the official publication and full release of all project materials and detailed results.
<br>

## Project Overview
<br>

This project investigates zero-shot adaptable task planning for autonomous construction robots by employing lightweight, open-source foundation models (LLMs and VLMs) in single- and multi-agent AI architectures. It aims to address challenges such as limited adaptability, high costs, and rigid task-specific programming prevalent in current construction robots.

<br>

<br>
![Robot in Painting Task](https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/6-MultiAI.png?raw=true)

## Key Features
<br>

- Zero-shot Task Planning: No task-specific pre-training or detailed human commands required.
- Multi-agent Collaboration: Single-agent and multi-agent (2, 3, and 4 agents) designs to enhance adaptability.
- Cost-Effectiveness: Leveraging lightweight local models instead of expensive cloud-based models.
- Quadruped Robot Integration: Unitree Go2 Edu robot with robotic arm and sensors for real-world experiments.
- Roles Tested: Painter, Safety Inspector, Floor Tiler, each representing varying complexity and dynamism in tasks.



## Experiments Conducted

<br>

Three critical tasks representing diverse construction activities:

| Task            | Category      | Complexity                    |
|-----------------|---------------|-------------------------------|
| **Painting**    | Craft         | High variability              | 
| **Safety Inspection** | Non-routine | High variability, low analyzability | 
| **Floor Tiling** | Craft        | Moderate-high variability     |  

<br>
![Robot in Painting Task](https://github.com/h-naderi/h-naderi.github.io/blob/master/assets/6-painting.png?raw=true)

## **Evaluation Metrics**
<br>

Systems evaluated based on five core metrics:

- ✅ **Correctness**: Object usage accuracy, intention prediction, function relevance.
- ⏳ **Temporal Understanding**: Sequencing of actions.
- 🛠️ **Executability**: Practical execution without hallucinations.
- 💲 **Cost**: Model usage costs per million tokens.
- ⏱️ **Time**: Processing duration for task completion.

---

## **Results & Findings**
<br>

- One of the designs significantly outperformed other architectures and even **GPT-4o** across several metrics.
- Cost Efficiency: Four-Agent model was **10x cheaper** than GPT-4o, making it highly suitable for industry applications.



---

## **Contribution & Impact**
<br>

This research represents a significant advancement toward truly autonomous, adaptable, and cost-effective robotic systems for the construction industry. It sets a benchmark for future research on scalable automation and AI-based task planning across complex, dynamic environments.




