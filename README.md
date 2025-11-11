# 🤖 Multi-Agent LLM System (CrewAI)

This project demonstrates AI agent collaboration using CrewAI with multiple agents working together.

## 👥 Agents
| Agent | Role |
|--------|-----|
| Research Agent | retrieves information |
| Writer Agent | generates final report |

---

## 🚀 Run

```bash
pip install -r requirements.txt
python crew.py



---

### ✅ Code Boilerplate

📁 Structure

crewai-multiagent/
│── crew.py
│── requirements.txt
│── README.md
│── .env


**crew.py**

```python
from crewai import Agent, Task, Crew
from langchain.chat_models import ChatOpenAI
from dotenv import load_dotenv

load_dotenv()

llm = ChatOpenAI(model="gpt-4.1-mini")

researcher = Agent(
    role="Research Agent",
    goal="Collect technical information",
    backstory="Expert at searching structured knowledge"
)

writer = Agent(
    role="Writer Agent",
    goal="Write a concise final summary",
    backstory="Transforms structured info into polished content"
)

task1 = Task(agent=researcher, description="Research what Western Digital does technologically.")
task2 = Task(agent=writer, description="Write a final structured summary.")

crew = Crew(agents=[researcher, writer], tasks=[task1, task2])
result = crew.run()

print(result)

