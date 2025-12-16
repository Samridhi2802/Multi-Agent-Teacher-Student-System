# 📘 Multi-Agent Teacher-Student System

This project demonstrates a sophisticated **multi-agent system** built using **Google's Agent Development Kit (ADK)**, simulating a dynamic learning environment. It showcases a collaborative conversational flow between AI agents with distinct roles: a **Teacher**, a **Student**, and a **Root Agent** orchestrating their interaction.

## 🚀 Project Overview

The **Multi-Agent Teacher-Student System** is designed to facilitate a **multi-step reasoning process** where knowledge is explained, summarized, and questioned. It aims to create interactive and intelligent educational or explanatory tools by simulating a more natural, multi-faceted learning interaction.

### 🔑 Key Components
- **Teacher Agent**: Acts as a senior professor, providing clear and comprehensive explanations of a given topic.  
- **Student Agent**: Summarizes the teacher's explanation, identifies key points, and formulates follow-up questions to deepen understanding or clarify concepts.  
- **Root Agent**: The orchestrator that manages the interaction between the Teacher and Student agents, taking the initial user query and returning the processed output.  

### 🧩 Problem Solved
Traditional AI responses are static. This system moves beyond that by enabling:
- Structured information delivery  
- Active learning simulation through summarization and questioning  
- Adaptive engagement where interactions dynamically build upon previous outputs  

### ⚙️ General Approach
The core relies on **Google ADK** to define and connect Large Language Model (LLM)-based agents.  
Each agent has a specific role, name, description, and instructions.  
The `root_agent` uses a `teacher_student_chain` function as a **tool** to sequentially invoke the `teacher` and `student` agents, creating a sophisticated conversational pipeline.

## 🖥️ Usage

### ▶️ Running the Multi-Agent System
To start an interactive session with your agents, execute:

```bash
!adk run teacher_student_agent
# Type "exit" to stop the conversation
```

You will be prompted with `[user]:` to enter your questions.  
The `root_agent` will then orchestrate the `teacher_student_chain` to provide an explanation from the teacher and a follow-up question from the student.

#### 💬 Example Interaction

[user]: Can u tell me what is AI?
[root_agent]: Okay, I can help with that. I will act as a teacher to explain what AI is. Then, I will play the role of a student to ask clarifying questions to ensure you understand.

**Teacher:**
AI, or Artificial Intelligence, refers to the simulation of human intelligence in machines that are programmed to think like humans and mimic their actions. The term may also be applied to any machine that exhibits traits associated with a human mind such as learning and problem-solving.

Do you have any questions so far?

[user]: 
[root_agent]: Okay, I'm ready to continue.

**Student:**
That's a good start. But I have some questions to make sure I understand.

1. What are some examples of AI in everyday life?
2. How is AI different from human intelligence?
3. What are the potential benefits and risks of AI?

To end the session, type `exit` at the `[user]:` prompt.

## 🌐 Running the ADK Web Interface with Ngrok (for Colab)

To access a **web-based UI** for your agents, you can use **ngrok** to expose the ADK web interface publicly.

### 1️⃣ Install `pyngrok`
```bash
!pip install pyngrok
from pyngrok import ngrok
```

### 2️⃣ Set Your Ngrok Auth Token
Obtain your auth token from [ngrok dashboard](https://ngrok.com/get-started/your-authtoken) and set it:
```python
ngrok.set_auth_token("YOUR_NGROK_AUTH_TOKEN")
```

### 3️⃣ Run ADK Web Interface and Create Ngrok Tunnel
```python
# Start ADK web interface in background
get_ipython().system_raw("adk web --port 8000 &")

# Create ngrok tunnel
from pyngrok import ngrok
public_url = ngrok.connect(8000)

public_url
```

This will output a public URL (e.g., `https://XXXX-XXXX-XXXX-XXXX.ngrok-free.app`) that you can open in your browser to interact with the ADK UI.

### 4️⃣ Stop the Ngrok Tunnel
```python
ngrok.kill()
```

---

### Output:
Open this in browser → you will see your **ADK Agent Development Kit UI.

<img width="1920" height="1080" alt="download" src="https://github.com/user-attachments/assets/39e72021-d795-4009-a559-7054a53f41c8" />

---

## 📂 Repository Structure
```
├── teacher_student_agent/
│   ├── agent.py        # Core logic defining Teacher, Student, and Root Agent
│   ├── __init__.py     # Package initializer
│   ├── .env            # Environment variables (Google API Key)
│   └── __pycache__/    # Python cache files
└── README.md           # Project documentation
```

## 🛠️ Requirements
- Python 3.8+  
- [Google ADK](https://google.github.io/adk-docs/get-started/python/)  
- `python-dotenv`  
- `google-generativeai`  
- `pyngrok` (for Colab web interface)  

Install dependencies:
```bash
pip install google-adk python-dotenv google-generativeai pyngrok
```

## 🙌 Acknowledgements
- Built with **Google Agent Development Kit (ADK)**  
- Inspired by interactive learning and multi-agent reasoning systems
  
---

## 📜 License
This project is licensed under the MIT License.  
Feel free to use, modify, and distribute with attribution.

